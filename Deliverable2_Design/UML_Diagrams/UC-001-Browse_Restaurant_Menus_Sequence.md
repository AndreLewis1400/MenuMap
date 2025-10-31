# UC-001: Browse Restaurant Menus - Sequence Diagram
## MenuMap Application - Team 9

**Use Case:** UC-001: Browse Restaurant Menus  
**Complexity:** Medium  
**Priority:** Core functionality  

---

## 🎯 **Lifelines (Participants) - 3-Tier Architecture**

```
User | WebInterface | MenuManager | MenuDAO | Database
```

**Tier Mapping:**
- **MM_Client (Presentation):** WebInterface
- **MM_Logic (Business Logic):** MenuManager
- **MM_DataStore (Data):** MenuDAO, Database

---

## 📋 **Message Flow (Step by Step) - Corrected for 3-Tier**

### **Phase 1: Menu Search**
```
1. User -> WebInterface: enter search criteria
2. WebInterface -> MenuManager: searchMenus(query, filters)
3. MenuManager -> MenuDAO: findRestaurants(criteria)
4. MenuDAO -> Database: queryRestaurants(criteria)
5. Database -> MenuDAO: return restaurantList
6. MenuDAO -> MenuManager: return restaurantList
7. MenuManager -> MenuDAO: getMenus(restaurantIDs)
8. MenuDAO -> Database: queryMenus(restaurantIDs)
9. Database -> MenuDAO: return menuList
10. MenuDAO -> MenuManager: return menuList
11. MenuManager -> WebInterface: return searchResults
12. WebInterface -> User: display restaurant list
```

### **Phase 2: Menu Selection**
```
13. User -> WebInterface: select restaurant
14. WebInterface -> MenuManager: getMenuDetails(restaurantID)
15. MenuManager -> MenuDAO: getMenu(restaurantID)
16. MenuDAO -> Database: queryMenu(restaurantID)
17. Database -> MenuDAO: return menu
18. MenuDAO -> MenuManager: return menuDetails
19. MenuManager -> WebInterface: return menuDetails
20. WebInterface -> User: display menu
```

---

## 🔄 **Alternative Flows (Alt Frames)**

### **Alt Frame 1: No Results Found**
```
alt No Results Found
    Database -> MenuController: return emptyList
    MenuController -> WebInterface: return noResults
    WebInterface -> User: display "No results found"
```

### **Alt Frame 2: Menu Unavailable**
```
alt Menu Unavailable
    Database -> MenuController: return error
    MenuController -> WebInterface: return menuUnavailable
    WebInterface -> User: display "Menu unavailable"
```

---

## 🎨 **Visual Layout in Papyrus**

### **Lifeline Order (Left to Right):**
```
User | WebInterface | MenuManager | MenuDAO | Database
```

### **Message Types:**
- **Solid Arrow**: Synchronous calls
- **Dashed Arrow**: Return messages
- **Self Arrow**: Internal method calls

### **Activation Boxes:**
- **WebInterface**: Steps 1-2, 9-10, 14
- **MenuController**: Steps 2-7, 10-13
- **Database**: Steps 3-4, 5-6, 11-12

---

## ✅ **Validation Checklist**

- [ ] All 6 lifelines created
- [ ] 14 main flow messages added
- [ ] 2 alternative flows (alt frames) included
- [ ] Activation boxes showing method execution
- [ ] Return messages as dashed arrows
- [ ] Professional formatting applied
- [ ] No syntax errors in validation

---

*This sequence diagram provides detailed interaction flow for UC-001: Browse Restaurant Menus use case.*
