# UC-002: Manage Favorites - Sequence Diagram
## MenuMap Application - Team 9

**Use Case:** UC-002: Manage Favorites  
**Complexity:** Medium  
**Priority:** User engagement feature  

---

## 🎯 **Lifelines (Participants)**

```
User | WebInterface | UserController | AuthenticationService | Database | Favorite
```

---

## 📋 **Message Flow (Step by Step)**

### **Phase 1: View Favorites**
```
1. User -> WebInterface: request favorites page
2. WebInterface -> AuthenticationService: validateSession(sessionToken)
3. AuthenticationService -> Database: verifySession(sessionToken)
4. Database -> AuthenticationService: return userID
5. AuthenticationService -> WebInterface: return userID

6. WebInterface -> UserController: getUserFavorites(userID)
7. UserController -> Database: getFavorites(userID)
8. Database -> UserController: return favoritesList
9. UserController -> WebInterface: return favorites
10. WebInterface -> User: display favorites
```

### **Phase 2: Add to Favorites**
```
11. User -> WebInterface: add to favorites
12. WebInterface -> UserController: addToFavorites(userID, itemID)
13. UserController -> Database: saveFavorite(userID, itemID)
14. Database -> UserController: return success
15. UserController -> WebInterface: return confirmation
16. WebInterface -> User: display "Added to favorites"
```

### **Phase 3: Remove from Favorites**
```
17. User -> WebInterface: remove from favorites
18. WebInterface -> UserController: removeFromFavorites(userID, itemID)
19. UserController -> Database: deleteFavorite(userID, itemID)
20. Database -> UserController: return success
21. UserController -> WebInterface: return confirmation
22. WebInterface -> User: display "Removed from favorites"
```

---

## 🔄 **Alternative Flows (Alt Frames)**

### **Alt Frame 1: Not Logged In**
```
alt Not Logged In
    AuthenticationService -> WebInterface: return null
    WebInterface -> User: redirect to login
```

### **Alt Frame 2: Favorites Limit Reached**
```
alt Favorites Limit Reached
    Database -> UserController: return limitError
    UserController -> WebInterface: return limitReached
    WebInterface -> User: display "Favorites limit reached"
```

---

## 🎨 **Visual Layout in Papyrus**

### **Lifeline Order (Left to Right):**
```
User | WebInterface | UserController | AuthenticationService | Database | Favorite
```

### **Message Types:**
- **Solid Arrow**: Synchronous calls
- **Dashed Arrow**: Return messages
- **Self Arrow**: Internal method calls

### **Activation Boxes:**
- **WebInterface**: Steps 1-2, 6, 10-12, 16-18, 22
- **UserController**: Steps 6-9, 12-15, 18-21
- **AuthenticationService**: Steps 2-5
- **Database**: Steps 3-4, 7-8, 13-14, 19-20

---

## ✅ **Validation Checklist**

- [ ] All 6 lifelines created
- [ ] 22 main flow messages added
- [ ] 2 alternative flows (alt frames) included
- [ ] Activation boxes showing method execution
- [ ] Return messages as dashed arrows
- [ ] Professional formatting applied
- [ ] No syntax errors in validation

---

*This sequence diagram provides detailed interaction flow for UC-002: Manage Favorites use case.*
