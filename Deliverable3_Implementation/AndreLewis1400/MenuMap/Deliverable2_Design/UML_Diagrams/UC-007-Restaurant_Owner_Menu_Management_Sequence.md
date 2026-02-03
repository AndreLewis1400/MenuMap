# UC-007: Restaurant Owner Menu Management Sequence Diagram

## Use Case: Restaurant Owner Menu Management
**Actor:** Restaurant Owner 
**Goal:** Create, update, and manage restaurant menus 
**Precondition:** User is authenticated as Restaurant Owner 

**Design Pattern:** Observer Pattern 
**3-Tier Architecture:** MM_Client → MM_Logic → MM_DataStore

---

## **Lifelines (Participants) - Observer Pattern Implementation**

```
RestaurantOwner | MenuForm | MenuManager | UserManager_CMD | MenuRepository | Database
 | |
 FavoriteObserver | NotificationObserver
```

**Tier Mapping:**
- **MM_Client (Presentation):** MenuForm
- **MM_Logic (Business Logic):** MenuManager (Subject), FavoriteObserver, NotificationObserver
- **MM_DataStore (Data):** MenuRepository, Database

**Pattern Roles:**
- **Subject:** MenuManager
- **Observers:** FavoriteObserver, NotificationObserver

---

## Sequence Flow - Observer Pattern

```
RestaurantOwner -> MenuForm: Update menu item (itemId, newPrice)
MenuForm -> MenuManager: updateMenuItem(itemId, newPrice)
MenuManager -> MenuRepository: getMenuItem(itemId)
MenuRepository -> Database: SELECT * FROM menu_items WHERE id=?
Database -> MenuRepository: return menuItem
MenuRepository -> MenuManager: return menuItem
MenuManager -> MenuRepository: updateMenuItem(itemId, newPrice)
MenuRepository -> Database: UPDATE menu_items SET price=? WHERE id=?
Database -> MenuRepository: return success
MenuRepository -> MenuManager: return success

// Observer Pattern: Notify all observers of menu change
MenuManager -> MenuManager: notifyObservers(menuChangeEvent)

MenuManager -> FavoriteObserver: update(menuChangeEvent)
FavoriteObserver -> FavoriteObserver: updateUserFavorites(itemId, newPrice)
FavoriteObserver -> MenuRepository: updateFavoritePrice(itemId, newPrice)
MenuRepository -> Database: UPDATE favorites SET price=? WHERE itemId=?
Database -> MenuRepository: return success
MenuRepository -> FavoriteObserver: return success

MenuManager -> NotificationObserver: update(menuChangeEvent)
NotificationObserver -> NotificationObserver: sendMenuUpdateNotifications(itemId)
NotificationObserver -> UserManager_CMD: getUsersWithFavorite(itemId)
UserManager_CMD -> MenuRepository: SELECT userId FROM favorites WHERE itemId=?
MenuRepository -> Database: SELECT userId FROM favorites WHERE itemId=?
Database -> MenuRepository: return userIds
MenuRepository -> UserManager_CMD: return userIds
UserManager_CMD -> NotificationObserver: return userIds
NotificationObserver -> NotificationObserver: sendNotification(userIds, "Menu item updated")

MenuManager -> MenuForm: return success
MenuForm -> RestaurantOwner: display "Menu updated successfully"
```

---

## Alternative Flows

### A1: Menu Item Creation
```
RestaurantOwner -> MenuForm: Create new menu item
MenuForm -> MenuManager: createMenuItem(menuData)
MenuManager -> MenuRepository: createMenuItem(menuData)
MenuRepository -> Database: INSERT INTO menu_items (...)
Database -> MenuRepository: return newItemId
MenuRepository -> MenuManager: return newItemId
MenuManager -> MenuManager: notifyObservers(newItemEvent)
MenuManager -> FavoriteObserver: update(newItemEvent)
MenuManager -> NotificationObserver: update(newItemEvent)
MenuManager -> MenuForm: return success
```

### A2: Menu Item Deletion
```
RestaurantOwner -> MenuForm: Delete menu item
MenuForm -> MenuManager: deleteMenuItem(itemId)
MenuManager -> MenuManager: notifyObservers(deleteEvent)
MenuManager -> FavoriteObserver: update(deleteEvent)
FavoriteObserver -> MenuRepository: removeFromFavorites(itemId)
MenuRepository -> Database: DELETE FROM favorites WHERE itemId=?
MenuManager -> MenuRepository: deleteMenuItem(itemId)
MenuRepository -> Database: DELETE FROM menu_items WHERE id=?
Database -> MenuRepository: return success
MenuManager -> MenuForm: return success
```

---

## Postconditions
- **Success:** Menu item updated, observers notified, users with favorites notified
- **Failure:** Menu remains unchanged, error message displayed
- **Observer Pattern:** All registered observers receive notifications

---

## Business Rules
- Only Restaurant Owner can modify their own menus
- Menu changes trigger notifications to users with favorites
- Favorite prices automatically update when menu prices change
- Menu deletions remove items from user favorites

