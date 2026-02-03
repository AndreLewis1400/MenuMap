# UC-002: Manage Favorites - Sequence Diagram
## MenuMap Application - Team 9

**Use Case:** UC-002: Manage Favorites 
**Complexity:** Medium 
**Priority:** User engagement feature 

---

## **Lifelines (Participants) - 3-Tier Architecture**

```
User | FavoritesForm | UserManager_CMD | UserRepository | Database
```

**Tier Mapping:**
- **MM_Client (Presentation):** FavoritesForm
- **MM_Logic (Business Logic):** UserManager_CMD
- **MM_DataStore (Data):** UserRepository, Database

---

## **Message Flow (Step by Step) - Corrected for 3-Tier**

### **Phase 1: View Favorites**
```
1. User -> FavoritesForm: request favorites page
2. FavoritesForm -> UserManager_CMD: getUserFavorites(sessionToken)
3. UserManager_CMD -> UserRepository: validateSession(sessionToken)
4. UserRepository -> Database: SELECT userId FROM sessions WHERE token=?
5. Database -> UserRepository: return userId
6. UserRepository -> UserManager_CMD: return userId

7. UserManager_CMD -> UserRepository: getFavorites(userId)
8. UserRepository -> Database: SELECT * FROM favorites WHERE userId=?
9. Database -> UserRepository: return favoritesList
10. UserRepository -> UserManager_CMD: return favoritesList
11. UserManager_CMD -> FavoritesForm: return favorites
12. FavoritesForm -> User: display favorites
```

### **Phase 2: Add to Favorites**
```
13. User -> FavoritesForm: add to favorites (itemId)
14. FavoritesForm -> UserManager_CMD: addToFavorites(sessionToken, itemId)
15. UserManager_CMD -> UserRepository: validateSession(sessionToken)
16. UserRepository -> Database: SELECT userId FROM sessions WHERE token=?
17. Database -> UserRepository: return userId
18. UserRepository -> UserManager_CMD: return userId

19. UserManager_CMD -> UserRepository: saveFavorite(userId, itemId)
20. UserRepository -> Database: INSERT INTO favorites (userId, itemId)
21. Database -> UserRepository: return success
22. UserRepository -> UserManager_CMD: return success
23. UserManager_CMD -> FavoritesForm: return confirmation
24. FavoritesForm -> User: display "Added to favorites"
```

### **Phase 3: Remove from Favorites**
```
25. User -> FavoritesForm: remove from favorites (itemId)
26. FavoritesForm -> UserManager_CMD: removeFromFavorites(sessionToken, itemId)
27. UserManager_CMD -> UserRepository: validateSession(sessionToken)
28. UserRepository -> Database: SELECT userId FROM sessions WHERE token=?
29. Database -> UserRepository: return userId
30. UserRepository -> UserManager_CMD: return userId

31. UserManager_CMD -> UserRepository: deleteFavorite(userId, itemId)
32. UserRepository -> Database: DELETE FROM favorites WHERE userId=? AND itemId=?
33. Database -> UserRepository: return success
34. UserRepository -> UserManager_CMD: return success
35. UserManager_CMD -> FavoritesForm: return confirmation
36. FavoritesForm -> User: display "Removed from favorites"
```

---

## **Alternative Flows (Alt Frames)**

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

## **Visual Layout in Papyrus**

### **Lifeline Order (Left to Right):**
```
User | FavoritesForm | UserManager_CMD | UserRepository | Database
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

## **Validation Checklist**

- [ ] All 6 lifelines created
- [ ] 22 main flow messages added
- [ ] 2 alternative flows (alt frames) included
- [ ] Activation boxes showing method execution
- [ ] Return messages as dashed arrows
- [ ] Professional formatting applied
- [ ] No syntax errors in validation

---

*This sequence diagram provides detailed interaction flow for UC-002: Manage Favorites use case.*
