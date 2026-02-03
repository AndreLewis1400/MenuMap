# MenuMap OCL Statements
## CEN4010 Software Engineering - Team 9

**Author:** Andre Lewis (Software Architecture & Design Lead)  
**Date:** [Current Date]  
**Version:** 1.0  

---

## OCL Statements Overview

This document contains Object Constraint Language (OCL) statements for the MenuMap application's control objects. These statements define business rules, constraints, and invariants that ensure system integrity and proper behavior.

---

## OCL Statements by Control Object

### **AuthenticationController**

#### **Invariants**
```ocl
context AuthenticationController
inv: self.authService <> null
inv: self.sessionManager <> null
inv: self.securityLogger <> null

-- Session management constraints
inv: self.sessionManager.activeSessions->size() <= self.sessionManager.maxSessions
inv: self.sessionManager.activeSessions->forAll(s | s.isValid())
```

#### **Preconditions**
```ocl
context AuthenticationController::authenticateUser(username: String, password: String): String
pre: username <> null and username.size() > 0
pre: password <> null and password.size() >= 8
pre: not username.contains(" ")
pre: password.matches(".*[A-Z].*") and password.matches(".*[a-z].*") and password.matches(".*[0-9].*")

context AuthenticationController::resetPassword(email: String): Boolean
pre: email <> null and email.matches("^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$")
pre: self.userRepository.findByEmail(email) <> null
```

#### **Postconditions**
```ocl
context AuthenticationController::authenticateUser(username: String, password: String): String
post: result <> null implies result.size() > 0
post: result <> null implies self.sessionManager.activeSessions->exists(s | s.token = result)
post: result = null implies self.securityLogger.logFailedLogin(username)

context AuthenticationController::logoutUser(sessionToken: String): void
post: not self.sessionManager.activeSessions->exists(s | s.token = sessionToken)
post: self.securityLogger.logUserLogout(sessionToken)
```

### **MenuController**

#### **Invariants**
```ocl
context MenuController
inv: self.menuService <> null
inv: self.searchService <> null
inv: self.verificationService <> null

-- Menu validation constraints
inv: self.menuService.cache->forAll(m | m.isValid())
inv: self.searchService.searchIndex->size() >= 0
```

#### **Preconditions**
```ocl
context MenuController::browseMenus(restaurantID: String): Menu
pre: restaurantID <> null and restaurantID.size() > 0
pre: self.restaurantRepository.findById(restaurantID) <> null

context MenuController::searchMenus(query: String, filters: SearchFilters): List<Menu>
pre: query <> null and query.size() >= 2
pre: filters <> null
pre: query.size() <= 100

context MenuController::verifyMenu(menuID: String): Boolean
pre: menuID <> null and menuID.size() > 0
pre: self.menuRepository.findById(menuID) <> null
```

#### **Postconditions**
```ocl
context MenuController::browseMenus(restaurantID: String): Menu
post: result <> null implies result.restaurantID = restaurantID
post: result <> null implies result.menuItems->size() > 0

context MenuController::searchMenus(query: String, filters: SearchFilters): List<Menu>
post: result <> null
post: result->forAll(m | m.matches(query) or m.matches(filters))
post: result->size() <= 50

context MenuController::updateMenu(menuID: String, updates: MenuUpdate): Boolean
post: result = true implies self.menuRepository.findById(menuID).lastModified = DateTime.now()
post: result = false implies self.verificationService.logUpdateFailure(menuID)
```

### **UserController**

#### **Invariants**
```ocl
context UserController
inv: self.userService <> null
inv: self.favoritesService <> null
inv: self.preferencesService <> null

-- User management constraints
inv: self.userService.activeUsers->forAll(u | u.isValid())
inv: self.favoritesService.userFavorites->size() >= 0
```

#### **Preconditions**
```ocl
context UserController::registerUser(userData: UserRegistration): Boolean
pre: userData <> null
pre: userData.email <> null and userData.email.matches("^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$")
pre: userData.username <> null and userData.username.size() >= 3
pre: userData.password <> null and userData.password.size() >= 8
pre: not self.userRepository.findByEmail(userData.email).exists()
pre: not self.userRepository.findByUsername(userData.username).exists()

context UserController::addToFavorites(userID: String, itemID: String): Boolean
pre: userID <> null and userID.size() > 0
pre: itemID <> null and itemID.size() > 0
pre: self.userRepository.findById(userID) <> null
pre: self.menuRepository.findById(itemID) <> null
pre: not self.favoritesService.exists(userID, itemID)
```

#### **Postconditions**
```ocl
context UserController::registerUser(userData: UserRegistration): Boolean
post: result = true implies self.userRepository.findByEmail(userData.email) <> null
post: result = true implies self.userService.activeUsers->includes(self.userRepository.findByEmail(userData.email))
post: result = false implies self.userService.logRegistrationFailure(userData.email)

context UserController::addToFavorites(userID: String, itemID: String): Boolean
post: result = true implies self.favoritesService.exists(userID, itemID)
post: result = true implies self.favoritesService.getUserFavorites(userID)->includes(itemID)
post: result = false implies self.favoritesService.logAddFailure(userID, itemID)
```

### **RestaurantController**

#### **Invariants**
```ocl
context RestaurantController
inv: self.restaurantService <> null
inv: self.menuService <> null
inv: self.verificationService <> null

-- Restaurant management constraints
inv: self.restaurantService.activeRestaurants->forAll(r | r.isValid())
inv: self.menuService.restaurantMenus->size() >= 0
```

#### **Preconditions**
```ocl
context RestaurantController::createRestaurant(restaurantData: RestaurantData): Boolean
pre: restaurantData <> null
pre: restaurantData.name <> null and restaurantData.name.size() >= 2
pre: restaurantData.address <> null and restaurantData.address.size() > 0
pre: restaurantData.phoneNumber <> null and restaurantData.phoneNumber.matches("^\\+?[1-9]\\d{1,14}$")
pre: not self.restaurantRepository.findByName(restaurantData.name).exists()

context RestaurantController::addMenu(restaurantID: String, menu: Menu): Boolean
pre: restaurantID <> null and restaurantID.size() > 0
pre: menu <> null
pre: menu.name <> null and menu.name.size() > 0
pre: self.restaurantRepository.findById(restaurantID) <> null
pre: menu.menuItems->size() > 0
```

#### **Postconditions**
```ocl
context RestaurantController::createRestaurant(restaurantData: RestaurantData): Boolean
post: result = true implies self.restaurantRepository.findByName(restaurantData.name) <> null
post: result = true implies self.restaurantService.activeRestaurants->includes(self.restaurantRepository.findByName(restaurantData.name))
post: result = false implies self.restaurantService.logCreationFailure(restaurantData.name)

context RestaurantController::addMenu(restaurantID: String, menu: Menu): Boolean
post: result = true implies self.menuRepository.findByRestaurant(restaurantID)->includes(menu)
post: result = true implies menu.restaurantID = restaurantID
post: result = false implies self.menuService.logAddFailure(restaurantID, menu.id)
```

### **MenuValidationRules**

#### **Invariants**
```ocl
context MenuValidationRules
inv: self.maxMenuItems > 0 and self.maxMenuItems <= 1000
inv: self.maxPrice > 0 and self.maxPrice <= 10000
inv: self.requiredFields <> null and self.requiredFields->size() > 0

-- Validation rule constraints
inv: self.requiredFields->includes("name")
inv: self.requiredFields->includes("price")
inv: self.requiredFields->includes("description")
```

#### **Preconditions**
```ocl
context MenuValidationRules::validateMenu(menu: Menu): ValidationResult
pre: menu <> null
pre: menu.menuItems <> null

context MenuValidationRules::validateMenuItem(item: MenuItem): ValidationResult
pre: item <> null
pre: item.name <> null
pre: item.price <> null
```

#### **Postconditions**
```ocl
context MenuValidationRules::validateMenu(menu: Menu): ValidationResult
post: result <> null
post: result.isValid = (menu.menuItems->size() <= self.maxMenuItems and 
                       menu.menuItems->forAll(i | i.price <= self.maxPrice) and
                       menu.menuItems->forAll(i | self.requiredFields->forAll(f | i.hasField(f))))

context MenuValidationRules::validateMenuItem(item: MenuItem): ValidationResult
post: result <> null
post: result.isValid = (item.price > 0 and item.price <= self.maxPrice and
                       self.requiredFields->forAll(f | item.hasField(f)) and
                       item.name.size() > 0 and item.description.size() > 0)
```

### **UserPermissionRules**

#### **Invariants**
```ocl
context UserPermissionRules
inv: self.rolePermissions <> null and self.rolePermissions->size() > 0
inv: self.resourcePermissions <> null and self.resourcePermissions->size() > 0

-- Permission system constraints
inv: self.rolePermissions->forAll(rp | rp.key <> null and rp.value <> null)
inv: self.resourcePermissions->forAll(rp | rp.key <> null and rp.value <> null)
```

#### **Preconditions**
```ocl
context UserPermissionRules::checkPermission(userID: String, resource: String, action: String): Boolean
pre: userID <> null and userID.size() > 0
pre: resource <> null and resource.size() > 0
pre: action <> null and action.size() > 0
pre: self.userRepository.findById(userID) <> null

context UserPermissionRules::grantPermission(userID: String, permission: Permission): Boolean
pre: userID <> null and userID.size() > 0
pre: permission <> null
pre: self.userRepository.findById(userID) <> null
pre: not self.hasPermission(self.getUserRole(userID), permission)
```

#### **Postconditions**
```ocl
context UserPermissionRules::checkPermission(userID: String, resource: String, action: String): Boolean
post: result = self.hasPermission(self.getUserRole(userID), self.getPermissionForAction(action))
post: result = false implies self.logPermissionDenied(userID, resource, action)

context UserPermissionRules::grantPermission(userID: String, permission: Permission): Boolean
post: result = true implies self.hasPermission(self.getUserRole(userID), permission)
post: result = false implies self.logPermissionGrantFailure(userID, permission)
```

### **SpamDetectionRules**

#### **Invariants**
```ocl
context SpamDetectionRules
inv: self.spamKeywords <> null and self.spamKeywords->size() > 0
inv: self.maxContentLength > 0 and self.maxContentLength <= 10000
inv: self.suspiciousPatterns <> null and self.suspiciousPatterns->size() > 0

-- Spam detection constraints
inv: self.spamKeywords->forAll(k | k <> null and k.size() > 0)
inv: self.suspiciousPatterns->forAll(p | p <> null and p.isValid())
```

#### **Preconditions**
```ocl
context SpamDetectionRules::detectSpam(content: String): SpamResult
pre: content <> null
pre: content.size() <= self.maxContentLength

context SpamDetectionRules::checkRateLimit(userID: String, action: String): Boolean
pre: userID <> null and userID.size() > 0
pre: action <> null and action.size() > 0
```

#### **Postconditions**
```ocl
context SpamDetectionRules::detectSpam(content: String): SpamResult
post: result <> null
post: result.isSpam = (self.spamKeywords->exists(k | content.toLowerCase().contains(k.toLowerCase())) or
                      self.suspiciousPatterns->exists(p | p.matches(content)) or
                      content.size() > self.maxContentLength)
post: result.confidence >= 0.0 and result.confidence <= 1.0

context SpamDetectionRules::checkRateLimit(userID: String, action: String): Boolean
post: result = (self.getUserActionCount(userID, action) < self.getRateLimit(action))
post: result = false implies self.flagSuspiciousActivity(userID, action)
```

### **AuthenticationService**

#### **Invariants**
```ocl
context AuthenticationService
inv: self.userRepository <> null
inv: self.sessionManager <> null
inv: self.passwordHasher <> null
inv: self.tokenGenerator <> null

-- Authentication system constraints
inv: self.sessionManager.activeSessions->forAll(s | s.isValid())
inv: self.userRepository.activeUsers->forAll(u | u.isAuthenticated())
```

#### **Preconditions**
```ocl
context AuthenticationService::authenticateUser(username: String, password: String): String
pre: username <> null and username.size() > 0
pre: password <> null and password.size() >= 8
pre: self.userRepository.findByUsername(username) <> null

context AuthenticationService::generateSessionToken(userID: String): String
pre: userID <> null and userID.size() > 0
pre: self.userRepository.findById(userID) <> null
pre: not self.sessionManager.hasActiveSession(userID)
```

#### **Postconditions**
```ocl
context AuthenticationService::authenticateUser(username: String, password: String): String
post: result <> null implies result.size() > 0
post: result <> null implies self.sessionManager.activeSessions->exists(s | s.token = result and s.userID = self.userRepository.findByUsername(username).id)
post: result = null implies self.logAuthenticationFailure(username)

context AuthenticationService::generateSessionToken(userID: String): String
post: result <> null and result.size() > 0
post: self.sessionManager.activeSessions->exists(s | s.token = result and s.userID = userID)
post: self.userRepository.findById(userID).lastLogin = DateTime.now()
```

### **MenuService**

#### **Invariants**
```ocl
context MenuService
inv: self.menuRepository <> null
inv: self.searchService <> null
inv: self.cache <> null

-- Menu service constraints
inv: self.cache->forAll(m | m.isValid())
inv: self.searchService.searchIndex->size() >= 0
```

#### **Preconditions**
```ocl
context MenuService::getMenu(restaurantID: String): Menu
pre: restaurantID <> null and restaurantID.size() > 0
pre: self.restaurantRepository.findById(restaurantID) <> null

context MenuService::searchMenus(query: String, filters: SearchFilters): List<Menu>
pre: query <> null and query.size() >= 2
pre: filters <> null
pre: query.size() <= 100
```

#### **Postconditions**
```ocl
context MenuService::getMenu(restaurantID: String): Menu
post: result <> null implies result.restaurantID = restaurantID
post: result <> null implies result.menuItems->size() > 0
post: result <> null implies self.cache->includes(result)

context MenuService::searchMenus(query: String, filters: SearchFilters): List<Menu>
post: result <> null
post: result->forAll(m | m.matches(query) or m.matches(filters))
post: result->size() <= 50
post: result->forAll(m | self.cache->includes(m))
```

---

## Security-Related OCL Statements

### **Password Security Constraints**
```ocl
context PasswordHasher
inv: self.saltRounds >= 10 and self.saltRounds <= 15
inv: self.algorithm = "bcrypt"

context PasswordHasher::hashPassword(password: String): String
pre: password <> null and password.size() >= 8
pre: password.matches(".*[A-Z].*") and password.matches(".*[a-z].*") and password.matches(".*[0-9].*")
post: result <> null and result.size() > 0
post: result <> password
```

### **Session Security Constraints**
```ocl
context SessionManager
inv: self.sessionTimeout > 0 and self.sessionTimeout <= 1440 -- max 24 hours
inv: self.maxSessions > 0 and self.maxSessions <= 1000

context SessionManager::createSession(userID: String): Session
pre: userID <> null and userID.size() > 0
pre: self.activeSessions->size() < self.maxSessions
post: result <> null and result.isValid()
post: result.userID = userID
post: result.expirationTime = DateTime.now() + self.sessionTimeout.minutes()
```

### **Token Security Constraints**
```ocl
context TokenGenerator
inv: self.secretKey <> null and self.secretKey.size() >= 32
inv: self.expirationTime > 0 and self.expirationTime <= 3600 -- max 1 hour
inv: self.algorithm = "HS256"

context TokenGenerator::generateAccessToken(userID: String): String
pre: userID <> null and userID.size() > 0
post: result <> null and result.size() > 0
post: result.contains(userID)
post: self.validateToken(result)
```

---

## Business Rule OCL Statements

### **Menu Business Rules**
```ocl
context Menu
inv: self.menuItems->size() > 0
inv: self.menuItems->forAll(i | i.price > 0)
inv: self.menuItems->forAll(i | i.name.size() > 0)
inv: self.restaurantID <> null

context MenuItem
inv: self.price > 0 and self.price <= 10000
inv: self.name <> null and self.name.size() > 0
inv: self.description <> null and self.description.size() > 0
inv: self.category <> null
```

### **User Business Rules**
```ocl
context User
inv: self.email <> null and self.email.matches("^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$")
inv: self.username <> null and self.username.size() >= 3
inv: self.passwordHash <> null and self.passwordHash.size() > 0
inv: self.createdDate <= DateTime.now()

context Favorite
inv: self.userID <> null
inv: self.itemID <> null
inv: self.createdDate <= DateTime.now()
inv: not self.userID.isEmpty() and not self.itemID.isEmpty()
```

### **Restaurant Business Rules**
```ocl
context Restaurant
inv: self.name <> null and self.name.size() >= 2
inv: self.address <> null and self.address.size() > 0
inv: self.phoneNumber <> null and self.phoneNumber.matches("^\\+?[1-9]\\d{1,14}$")
inv: self.isActive implies self.menus->size() > 0
```

---

## OCL Statement Benefits

### **System Integrity**
- Ensures data consistency across all operations
- Prevents invalid state transitions
- Validates business rule compliance

### **Security Enforcement**
- Enforces authentication and authorization rules
- Validates input parameters
- Ensures secure session management

### **Quality Assurance**
- Provides clear specifications for testing
- Documents expected behavior
- Enables automated validation

---

*These OCL statements provide comprehensive constraints and business rules for the MenuMap application's control objects, ensuring system integrity, security, and proper behavior.*
