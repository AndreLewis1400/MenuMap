# UC-007: Restaurant Owner Menu Management - Sequence Diagram Quick Reference
## MenuMap Application - Team 9

**Use Case:** UC-007: Restaurant Owner Menu Management  
**Complexity:** Medium  
**Priority:** Good practice for authentication flows  

---

## 🎯 **Lifelines (Participants)**

```
Restaurant Owner | WebInterface | MenuController | AuthenticationService | Database | Menu | MenuItem
```

---

## 📋 **Message Flow (Step by Step)**

### **Phase 1: Restaurant Owner Login**
```
1. Restaurant Owner -> WebInterface: login to restaurant portal
2. WebInterface -> AuthenticationService: authenticateRestaurantOwner(credentials)
3. AuthenticationService -> Database: verifyRestaurantOwner(credentials)
4. Database -> AuthenticationService: return ownerData
5. AuthenticationService -> WebInterface: return sessionToken
6. WebInterface -> Restaurant Owner: display restaurant dashboard
```

### **Phase 2: View Current Menu**
```
7. Restaurant Owner -> WebInterface: select "Manage Menu"
8. WebInterface -> MenuController: getRestaurantMenu(restaurantID)
9. MenuController -> Database: getMenu(restaurantID)
10. Database -> MenuController: return menu
11. MenuController -> WebInterface: return menuData
12. WebInterface -> Restaurant Owner: display current menu
```

### **Phase 3: Add New Menu Item**
```
13. Restaurant Owner -> WebInterface: add new menu item
14. WebInterface -> MenuController: addMenuItem(restaurantID, itemData)
15. MenuController -> Database: createMenuItem(restaurantID, itemData)
16. Database -> MenuController: return itemID
17. MenuController -> WebInterface: return success
18. WebInterface -> Restaurant Owner: display "Item added"
```

### **Phase 4: Update Menu Item**
```
19. Restaurant Owner -> WebInterface: update menu item
20. WebInterface -> MenuController: updateMenuItem(itemID, updates)
21. MenuController -> Database: updateMenuItem(itemID, updates)
22. Database -> MenuController: return success
23. MenuController -> WebInterface: return confirmation
24. WebInterface -> Restaurant Owner: display "Item updated"
```

### **Phase 5: Delete Menu Item**
```
25. Restaurant Owner -> WebInterface: delete menu item
26. WebInterface -> MenuController: deleteMenuItem(itemID)
27. MenuController -> Database: deleteMenuItem(itemID)
28. Database -> MenuController: return success
29. MenuController -> WebInterface: return confirmation
30. WebInterface -> Restaurant Owner: display "Item deleted"
```

---

## 🔄 **Alternative Flows (Alt Frames)**

### **Alt Frame 1: Authentication Failed**
```
alt Authentication Failed
    Database -> AuthenticationService: return null
    AuthenticationService -> WebInterface: return authenticationError
    WebInterface -> Restaurant Owner: display "Login failed"
```

### **Alt Frame 2: Menu Not Found**
```
alt Menu Not Found
    Database -> MenuController: return null
    MenuController -> WebInterface: return menuNotFound
    WebInterface -> Restaurant Owner: display "Menu not found"
```

### **Alt Frame 3: Item Operation Failed**
```
alt Item Operation Failed
    Database -> MenuController: return error
    MenuController -> WebInterface: return operationError
    WebInterface -> Restaurant Owner: display "Operation failed"
```

---

## 🎨 **Visual Layout in Papyrus**

### **Lifeline Order (Left to Right):**
```
Restaurant Owner | WebInterface | MenuController | AuthenticationService | Database | Menu | MenuItem
```

### **Message Types:**
- **Solid Arrow**: Synchronous calls
- **Dashed Arrow**: Return messages
- **Self Arrow**: Internal method calls (if any)

### **Activation Boxes:**
- **WebInterface**: Steps 1-2, 7-8, 13-14, 19-20, 25-26
- **AuthenticationService**: Steps 2-5
- **MenuController**: Steps 8-11, 14-17, 20-23, 26-29
- **Database**: Steps 3-4, 9-10, 15-16, 21-22, 27-28

---

## 🔧 **Papyrus Implementation Tips**

### **Step 1: Verify Lifelines**
1. Check all 7 lifelines are present
2. Name the unlabeled lifeline (likely MenuItem)
3. Space evenly across diagram

### **Step 2: Add Messages**
1. Use "Message" tool
2. Click from source to target lifeline
3. Label with step number and method name

### **Step 3: Add Alt Frames**
1. Use "Interaction Use" tool
2. Draw rectangle around alternative flow
3. Label as "alt [condition]"

### **Step 4: Add Activation Boxes**
1. Right-click on each message
2. Check "Activation" in properties
3. Adjust length to show execution duration

---

## ✅ **Validation Checklist**

- [ ] All 7 lifelines created
- [ ] 30 main flow messages added
- [ ] 3 alternative flows (alt frames) included
- [ ] Activation boxes showing method execution
- [ ] Return messages as dashed arrows
- [ ] Professional formatting applied
- [ ] No syntax errors in validation

---

## 🎯 **Why UC-007 is Good Practice**

1. **Authentication Flow**: Practice with login/authentication
2. **CRUD Operations**: Create, Read, Update, Delete patterns
3. **Multiple Phases**: Clear separation of different operations
4. **Error Handling**: Alternative flows for common failures
5. **Medium Complexity**: Good balance of features without being overwhelming

---

*This quick reference provides everything needed to implement UC-007 sequence diagram in Papyrus. The restaurant owner menu management flow is a common pattern in business applications.*
