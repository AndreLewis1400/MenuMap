# MenuMap Sequence Diagrams
## CEN4010 Software Engineering - Team 9

**Project:** MenuMap Application 
**Team:** Team 9 
**Software Architecture & Design Lead:** Andre Lewis 
**Date:** [Current Date] 
**Version:** 1.0 

---

## Sequence Diagram Overview

This document contains sequence diagrams for all 7 use cases selected for implementation in Deliverable 2. Each sequence diagram shows the detailed interaction flow between actors and system objects.

---

## UC-001: Browse Restaurant Menus - Sequence Diagram

### **Actors & Objects:**
- **User** (Primary Actor)
- **WebInterface** (Boundary Object)
- **MenuController** (Control Object)
- **Database** (Entity Object)
- **Restaurant** (Entity Object)
- **Menu** (Entity Object)

### **Sequence Flow:**
```
User -> WebInterface: 1. Enter search criteria
WebInterface -> MenuController: 2. searchMenus(query, filters)
MenuController -> Database: 3. findRestaurants(criteria)
Database -> MenuController: 4. return restaurantList
MenuController -> Database: 5. getMenus(restaurantIDs)
Database -> MenuController: 6. return menuList
MenuController -> WebInterface: 7. return searchResults
WebInterface -> User: 8. display restaurant list

User -> WebInterface: 9. select restaurant
WebInterface -> MenuController: 10. getMenuDetails(restaurantID)
MenuController -> Database: 11. getMenu(restaurantID)
Database -> MenuController: 12. return menu
MenuController -> WebInterface: 13. return menuDetails
WebInterface -> User: 14. display menu
```

### **Alternative Flows:**
- **A1: No Results Found**
 - Database returns empty list
 - WebInterface displays "No results found" message

- **A2: Menu Unavailable**
 - Database returns error
 - WebInterface displays error message

---

## UC-002: Manage Favorites - Sequence Diagram

### **Actors & Objects:**
- **User** (Primary Actor)
- **WebInterface** (Boundary Object)
- **UserController** (Control Object)
- **AuthenticationService** (Control Object)
- **Database** (Entity Object)
- **Favorite** (Entity Object)

### **Sequence Flow:**
```
User -> WebInterface: 1. request favorites page
WebInterface -> AuthenticationService: 2. validateSession(sessionToken)
AuthenticationService -> Database: 3. verifySession(sessionToken)
Database -> AuthenticationService: 4. return userID
AuthenticationService -> WebInterface: 5. return userID

WebInterface -> UserController: 6. getUserFavorites(userID)
UserController -> Database: 7. getFavorites(userID)
Database -> UserController: 8. return favoritesList
UserController -> WebInterface: 9. return favorites
WebInterface -> User: 10. display favorites

User -> WebInterface: 11. add to favorites
WebInterface -> UserController: 12. addToFavorites(userID, itemID)
UserController -> Database: 13. saveFavorite(userID, itemID)
Database -> UserController: 14. return success
UserController -> WebInterface: 15. return confirmation
WebInterface -> User: 16. display "Added to favorites"
```

### **Alternative Flows:**
- **A1: Not Logged In**
 - AuthenticationService returns null
 - WebInterface redirects to login

- **A2: Favorites Limit Reached**
 - Database returns limit error
 - WebInterface displays limit message

---

## UC-003: Secure Password Reset - Sequence Diagram

### **Actors & Objects:**
- **User** (Primary Actor)
- **WebInterface** (Boundary Object)
- **AuthenticationService** (Control Object)
- **EmailService** (External Service)
- **Database** (Entity Object)
- **SecurityLogger** (Control Object)

### **Sequence Flow:**
```
User -> WebInterface: 1. click "Forgot Password"
WebInterface -> User: 2. display reset form
User -> WebInterface: 3. enter email address
WebInterface -> AuthenticationService: 4. requestPasswordReset(email)
AuthenticationService -> Database: 5. checkUserExists(email)
Database -> AuthenticationService: 6. return userExists

AuthenticationService -> AuthenticationService: 7. generateResetToken()
AuthenticationService -> Database: 8. saveResetToken(userID, token)
AuthenticationService -> EmailService: 9. sendResetEmail(email, token)
EmailService -> User: 10. deliver reset email
AuthenticationService -> WebInterface: 11. return success message
WebInterface -> User: 12. display "Check your email"

User -> WebInterface: 13. click reset link
WebInterface -> AuthenticationService: 14. validateResetToken(token)
AuthenticationService -> Database: 15. verifyToken(token)
Database -> AuthenticationService: 16. return tokenValid

User -> WebInterface: 17. enter new password
WebInterface -> AuthenticationService: 18. resetPassword(token, newPassword)
AuthenticationService -> Database: 19. updatePassword(userID, newPassword)
AuthenticationService -> Database: 20. invalidateToken(token)
AuthenticationService -> SecurityLogger: 21. logPasswordReset(userID)
AuthenticationService -> WebInterface: 22. return success
WebInterface -> User: 23. display "Password reset successful"
```

### **Alternative Flows:**
- **A1: Email Not Found**
 - Database returns false
 - AuthenticationService returns generic message (security)

- **A2: Token Expired**
 - Database returns token expired
 - WebInterface displays "Token expired" message

- **A3: Invalid Token**
 - Database returns invalid token
 - SecurityLogger logs suspicious activity

---

## UC-004: User Registration & Login - Sequence Diagram

### **Actors & Objects:**
- **User** (Primary Actor)
- **WebInterface** (Boundary Object)
- **AuthenticationService** (Control Object)
- **UserController** (Control Object)
- **Database** (Entity Object)
- **EmailService** (External Service)

### **Registration Flow:**
```
User -> WebInterface: 1. click "Register"
WebInterface -> User: 2. display registration form
User -> WebInterface: 3. submit registration data
WebInterface -> UserController: 4. registerUser(userData)
UserController -> Database: 5. checkUserExists(username, email)
Database -> UserController: 6. return userExists

UserController -> AuthenticationService: 7. hashPassword(password)
AuthenticationService -> UserController: 8. return hashedPassword
UserController -> Database: 9. createUser(userData, hashedPassword)
Database -> UserController: 10. return userID
UserController -> EmailService: 11. sendWelcomeEmail(email)
EmailService -> User: 12. deliver welcome email
UserController -> WebInterface: 13. return success
WebInterface -> User: 14. display "Registration successful"
```

### **Login Flow:**
```
User -> WebInterface: 15. enter credentials
WebInterface -> AuthenticationService: 16. authenticateUser(username, password)
AuthenticationService -> Database: 17. getUserData(username)
Database -> AuthenticationService: 18. return userData
AuthenticationService -> Database: 19. verifyPassword(username, password)
Database -> AuthenticationService: 20. return passwordValid

AuthenticationService -> AuthenticationService: 21. generateSessionToken(userID)
AuthenticationService -> Database: 22. saveSession(userID, sessionToken)
AuthenticationService -> WebInterface: 23. return sessionToken
WebInterface -> User: 24. display dashboard
```

---

## UC-005: Menu Verification System - Sequence Diagram

### **Actors & Objects:**
- **Restaurant Owner** (Primary Actor)
- **Administrator** (Secondary Actor)
- **WebInterface** (Boundary Object)
- **MenuController** (Control Object)
- **VerificationSystem** (Control Object)
- **Database** (Entity Object)
- **Report** (Entity Object)

### **Sequence Flow:**
```
Restaurant Owner -> WebInterface: 1. submit menu for verification
WebInterface -> MenuController: 2. submitMenuForVerification(menuData)
MenuController -> VerificationSystem: 3. verifyMenu(menuData)
VerificationSystem -> VerificationSystem: 4. validateMenuItems()
VerificationSystem -> VerificationSystem: 5. checkPricingConsistency()
VerificationSystem -> VerificationSystem: 6. detectDuplicates()

VerificationSystem -> Database: 7. saveVerificationReport(menuID, report)
Database -> VerificationSystem: 8. return reportID
VerificationSystem -> MenuController: 9. return verificationResult
MenuController -> WebInterface: 10. return verificationStatus
WebInterface -> Restaurant Owner: 11. display verification results

Administrator -> WebInterface: 12. review verification reports
WebInterface -> MenuController: 13. getVerificationReports()
MenuController -> Database: 14. getReports(status)
Database -> MenuController: 15. return reportsList
MenuController -> WebInterface: 16. return reports
WebInterface -> Administrator: 17. display reports

Administrator -> WebInterface: 18. approve/reject menu
WebInterface -> MenuController: 19. updateMenuStatus(menuID, status)
MenuController -> Database: 20. updateMenuStatus(menuID, status)
Database -> MenuController: 21. return success
MenuController -> WebInterface: 22. return confirmation
WebInterface -> Administrator: 23. display "Status updated"
```

---

## UC-006: Spam Protection System - Sequence Diagram

### **Actors & Objects:**
- **User** (Primary Actor)
- **Administrator** (Secondary Actor)
- **WebInterface** (Boundary Object)
- **SpamProtection** (Control Object)
- **Database** (Entity Object)
- **Alert** (Entity Object)

### **Sequence Flow:**
```
User -> WebInterface: 1. submit content (review, menu item)
WebInterface -> SpamProtection: 2. analyzeContent(content)
SpamProtection -> SpamProtection: 3. checkSpamPatterns()
SpamProtection -> SpamProtection: 4. validateContentQuality()
SpamProtection -> SpamProtection: 5. checkRateLimits(userID)

alt Content is Clean
 SpamProtection -> Database: 6a. saveContent(content)
 Database -> SpamProtection: 7a. return success
 SpamProtection -> WebInterface: 8a. return approved
 WebInterface -> User: 9a. display "Content published"
else Content is Spam
 SpamProtection -> Database: 6b. createAlert(content, userID)
 Database -> SpamProtection: 7b. return alertID
 SpamProtection -> WebInterface: 8b. return blocked
 WebInterface -> User: 9b. display "Content blocked"
end

Administrator -> WebInterface: 10. review spam alerts
WebInterface -> SpamProtection: 11. getSpamAlerts()
SpamProtection -> Database: 12. getAlerts(status)
Database -> SpamProtection: 13. return alertsList
SpamProtection -> WebInterface: 14. return alerts
WebInterface -> Administrator: 15. display alerts

Administrator -> WebInterface: 16. take action (block user, approve content)
WebInterface -> SpamProtection: 17. processAlert(alertID, action)
SpamProtection -> Database: 18. updateAlertStatus(alertID, action)
Database -> SpamProtection: 19. return success
SpamProtection -> WebInterface: 20. return confirmation
WebInterface -> Administrator: 21. display "Action completed"
```

---

## UC-007: Restaurant Owner Menu Management - Sequence Diagram

### **Actors & Objects:**
- **Restaurant Owner** (Primary Actor)
- **WebInterface** (Boundary Object)
- **MenuController** (Control Object)
- **AuthenticationService** (Control Object)
- **Database** (Entity Object)
- **Menu** (Entity Object)
- **MenuItem** (Entity Object)

### **Sequence Flow:**
```
Restaurant Owner -> WebInterface: 1. login to restaurant portal
WebInterface -> AuthenticationService: 2. authenticateRestaurantOwner(credentials)
AuthenticationService -> Database: 3. verifyRestaurantOwner(credentials)
Database -> AuthenticationService: 4. return ownerData
AuthenticationService -> WebInterface: 5. return sessionToken
WebInterface -> Restaurant Owner: 6. display restaurant dashboard

Restaurant Owner -> WebInterface: 7. select "Manage Menu"
WebInterface -> MenuController: 8. getRestaurantMenu(restaurantID)
MenuController -> Database: 9. getMenu(restaurantID)
Database -> MenuController: 10. return menu
MenuController -> WebInterface: 11. return menuData
WebInterface -> Restaurant Owner: 12. display current menu

Restaurant Owner -> WebInterface: 13. add new menu item
WebInterface -> MenuController: 14. addMenuItem(restaurantID, itemData)
MenuController -> Database: 15. createMenuItem(restaurantID, itemData)
Database -> MenuController: 16. return itemID
MenuController -> WebInterface: 17. return success
WebInterface -> Restaurant Owner: 18. display "Item added"

Restaurant Owner -> WebInterface: 19. update menu item
WebInterface -> MenuController: 20. updateMenuItem(itemID, updates)
MenuController -> Database: 21. updateMenuItem(itemID, updates)
Database -> MenuController: 22. return success
MenuController -> WebInterface: 23. return confirmation
WebInterface -> Restaurant Owner: 24. display "Item updated"

Restaurant Owner -> WebInterface: 25. delete menu item
WebInterface -> MenuController: 26. deleteMenuItem(itemID)
MenuController -> Database: 27. deleteMenuItem(itemID)
Database -> MenuController: 28. return success
MenuController -> WebInterface: 29. return confirmation
WebInterface -> Restaurant Owner: 30. display "Item deleted"
```

---

## Sequence Diagram Summary

| Use Case | Primary Actor | Key Control Objects | Key Entity Objects | Complexity |
|----------|---------------|-------------------|-------------------|------------|
| UC-001 | User | MenuController | Database, Restaurant, Menu | Medium |
| UC-002 | User | UserController, AuthenticationService | Database, Favorite | Medium |
| UC-003 | User | AuthenticationService, SecurityLogger | Database | High |
| UC-004 | User | AuthenticationService, UserController | Database | Medium |
| UC-005 | Restaurant Owner | MenuController, VerificationSystem | Database, Report | High |
| UC-006 | User | SpamProtection | Database, Alert | High |
| UC-007 | Restaurant Owner | MenuController, AuthenticationService | Database, Menu, MenuItem | Medium |

---

## Implementation Notes

### **Common Patterns:**
1. **Authentication Flow**: Most use cases start with session validation
2. **Error Handling**: Each sequence includes alternative flows for error conditions
3. **Security Logging**: Security-related actions are logged for audit trails
4. **Database Operations**: All persistent data operations go through the Database entity

### **Design Pattern Integration:**
- **Observer Pattern**: Used in real-time notifications and updates
- **Factory Pattern**: Used for creating different types of controllers and services
- **Strategy Pattern**: Used for different verification and spam detection algorithms

---

*These sequence diagrams provide detailed interaction flows for all 7 use cases in the MenuMap application, showing the complete object interactions from user input to system response.*
