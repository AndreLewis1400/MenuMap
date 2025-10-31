# UC-007: Restaurant Owner Menu Management Sequence Diagram

## Use Case: Restaurant Owner Menu Management
**Actor:** Restaurant Owner  
**Goal:** Create, update, and manage restaurant menus  
**Precondition:** User is authenticated as Restaurant Owner  

**Design Pattern:** Observer Pattern  
**3-Tier Architecture:** MM_Client → MM_Logic → MM_DataStore

---

## 🎯 **Lifelines (Participants) - Observer Pattern Implementation**

```
RestaurantOwner | MenuForm | MenuManager | UserManager_CMD | MenuDAO | Database
                       |          |
                  FavoriteObserver | NotificationObserver
```

**Tier Mapping:**
- **MM_Client (Presentation):** MenuForm
- **MM_Logic (Business Logic):** MenuManager (Subject), FavoriteObserver, NotificationObserver
- **MM_DataStore (Data):** MenuDAO, Database

**Pattern Roles:**
- **Subject:** MenuManager
- **Observers:** FavoriteObserver, NotificationObserver

---

## Sequence Flow - Observer Pattern

```
RestaurantOwner -> MenuForm: Update menu item (itemId, newPrice)
MenuForm -> MenuManager: updateMenuItem(itemId, newPrice)
MenuManager -> MenuDAO: getMenuItem(itemId)
MenuDAO -> Database: SELECT * FROM menu_items WHERE id=?
Database -> MenuDAO: return menuItem
MenuDAO -> MenuManager: return menuItem
MenuManager -> MenuDAO: updateMenuItem(itemId, newPrice)
MenuDAO -> Database: UPDATE menu_items SET price=? WHERE id=?
Database -> MenuDAO: return success
MenuDAO -> MenuManager: return success

// Observer Pattern: Notify all observers of menu change
MenuManager -> MenuManager: notifyObservers(menuChangeEvent)

MenuManager -> FavoriteObserver: update(menuChangeEvent)
FavoriteObserver -> FavoriteObserver: updateUserFavorites(itemId, newPrice)
FavoriteObserver -> MenuDAO: updateFavoritePrice(itemId, newPrice)
MenuDAO -> Database: UPDATE favorites SET price=? WHERE itemId=?
Database -> MenuDAO: return success
MenuDAO -> FavoriteObserver: return success

MenuManager -> NotificationObserver: update(menuChangeEvent)
NotificationObserver -> NotificationObserver: sendMenuUpdateNotifications(itemId)
NotificationObserver -> UserManager_CMD: getUsersWithFavorite(itemId)
UserManager_CMD -> MenuDAO: SELECT userId FROM favorites WHERE itemId=?
MenuDAO -> Database: SELECT userId FROM favorites WHERE itemId=?
Database -> MenuDAO: return userIds
MenuDAO -> UserManager_CMD: return userIds
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
MenuManager -> MenuDAO: createMenuItem(menuData)
MenuDAO -> Database: INSERT INTO menu_items (...)
Database -> MenuDAO: return newItemId
MenuDAO -> MenuManager: return newItemId
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
FavoriteObserver -> MenuDAO: removeFromFavorites(itemId)
MenuDAO -> Database: DELETE FROM favorites WHERE itemId=?
MenuManager -> MenuDAO: deleteMenuItem(itemId)
MenuDAO -> Database: DELETE FROM menu_items WHERE id=?
Database -> MenuDAO: return success
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

