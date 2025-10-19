# UC-001: Browse Restaurant Menus - Sequence Diagram
## MenuMap Application - Team 9

**Use Case:** UC-001: Browse Restaurant Menus  
**Complexity:** Medium  
**Priority:** Core functionality  

---

## 🎯 **Lifelines (Participants)**

```
User | WebInterface | MenuController | Database | Restaurant | Menu
```

---

## 📋 **Message Flow (Step by Step)**

### **Phase 1: Menu Search**
```
1. User -> WebInterface: enter search criteria
2. WebInterface -> MenuController: searchMenus(query, filters)
3. MenuController -> Database: findRestaurants(criteria)
4. Database -> MenuController: return restaurantList
5. MenuController -> Database: getMenus(restaurantIDs)
6. Database -> MenuController: return menuList
7. MenuController -> WebInterface: return searchResults
8. WebInterface -> User: display restaurant list
```

### **Phase 2: Menu Selection**
```
9. User -> WebInterface: select restaurant
10. WebInterface -> MenuController: getMenuDetails(restaurantID)
11. MenuController -> Database: getMenu(restaurantID)
12. Database -> MenuController: return menu
13. MenuController -> WebInterface: return menuDetails
14. WebInterface -> User: display menu
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
User | WebInterface | MenuController | Database | Restaurant | Menu
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
