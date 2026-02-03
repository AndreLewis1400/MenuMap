# MenuMap Detailed Class Diagram
## CEN4010 Software Engineering - Team 9

**Author:** Andre Lewis (Software Architecture & Design Lead) 
**Date:** [Current Date] 
**Version:** 1.0 

---

## Detailed Class Diagram Overview

This document defines the comprehensive class diagram for the MenuMap application, showing the detailed class structure within each layer and subsystem. The diagram follows the layered architecture pattern with clear separation of concerns and well-defined class relationships.

---

## Class Structure by Layer

### **Presentation Layer Classes**

#### **Web Interface Classes**
```
<<Boundary>> WebInterface
├── Attributes:
│ ├── - sessionID: String
│ ├── - currentUser: User
│ └── - isAuthenticated: Boolean
├── Operations:
│ ├── + displayLoginForm(): void
│ ├── + displayDashboard(sessionToken: String): void 
│ ├── + handleUserInput(): void
│ ├── + validateUser(credentials: String): Boolean
│ ├── + handleLoginResponse(sessionToken: String): void
│ └── + renderMenu(menu: Menu): void
└── Relationships:
 ├── uses → AuthenticationController
 ├── uses → MenuController
 └── uses → UserController

<<Boundary>> MobileInterface
├── Attributes:
│ ├── - deviceID: String
│ ├── - platform: String
│ └── - pushToken: String
├── Operations:
│ ├── + displayLoginForm(): void
│ ├── + displayDashboard(): void
│ ├── + handleTouchInput(): void
│ ├── + sendPushNotification(message: String): void
│ └── + syncOfflineData(): void
└── Relationships:
 ├── uses → AuthenticationController
 └── uses → MenuController

<<Boundary>> APIInterface
├── Attributes:
│ ├── - baseURL: String
│ ├── - apiVersion: String
│ └── - rateLimit: Integer
├── Operations:
│ ├── + authenticateUser(credentials: String): String
│ ├── + getMenu(restaurantID: String): Menu
│ ├── + getUserFavorites(userID: String): List<Favorite>
│ ├── + updateUserProfile(userID: String, profile: UserProfile): Boolean
│ └── + searchRestaurants(query: String): List<Restaurant>
└── Relationships:
 ├── uses → AuthenticationController
 ├── uses → MenuController
 └── uses → UserController
```

### **Business Logic Layer Classes**

#### **Use Case Controllers**
```
<<Control>> AuthenticationController
├── Attributes:
│ ├── - authService: AuthenticationService
│ ├── - sessionManager: SessionManager
│ └── - securityLogger: SecurityLogger
├── Operations:
│ ├── + validateUser(credentials: String): Boolean
│ ├── + authenticateUser(username: String, password: String): String
│ ├── + logoutUser(sessionToken: String): void
│ ├── + resetPassword(email: String): Boolean
│ └── + verifyPasswordReset(token: String, newPassword: String): Boolean
└── Relationships:
 ├── uses → AuthenticationService
 ├── uses → UserRepository
 └── uses → NotificationService

<<Control>> MenuController
├── Attributes:
│ ├── - menuService: MenuService
│ ├── - searchService: SearchService
│ └── - verificationService: VerificationService
├── Operations:
│ ├── + browseMenus(restaurantID: String): Menu
│ ├── + searchMenus(query: String, filters: SearchFilters): List<Menu>
│ ├── + getMenuDetails(menuID: String): MenuItem
│ ├── + verifyMenu(menuID: String): Boolean
│ └── + updateMenu(menuID: String, updates: MenuUpdate): Boolean
└── Relationships:
 ├── uses → MenuService
 ├── uses → RestaurantRepository
 └── uses → VerificationService

<<Control>> UserController
├── Attributes:
│ ├── - userService: UserService
│ ├── - favoritesService: FavoritesService
│ └── - preferencesService: PreferencesService
├── Operations:
│ ├── + registerUser(userData: UserRegistration): Boolean
│ ├── + updateUserProfile(userID: String, profile: UserProfile): Boolean
│ ├── + addToFavorites(userID: String, itemID: String): Boolean
│ ├── + removeFromFavorites(userID: String, itemID: String): Boolean
│ ├── + getUserFavorites(userID: String): List<Favorite>
│ └── + updateUserPreferences(userID: String, preferences: UserPreferences): Boolean
└── Relationships:
 ├── uses → UserService
 ├── uses → FavoritesService
 └── uses → UserRepository

<<Control>> RestaurantController
├── Attributes:
│ ├── - restaurantService: RestaurantService
│ ├── - menuService: MenuService
│ └── - verificationService: VerificationService
├── Operations:
│ ├── + createRestaurant(restaurantData: RestaurantData): Boolean
│ ├── + updateRestaurant(restaurantID: String, updates: RestaurantUpdate): Boolean
│ ├── + addMenu(restaurantID: String, menu: Menu): Boolean
│ ├── + updateMenu(restaurantID: String, menuID: String, updates: MenuUpdate): Boolean
│ └── + verifyRestaurant(restaurantID: String): Boolean
└── Relationships:
 ├── uses → RestaurantService
 ├── uses → MenuService
 └── uses → VerificationService
```

#### **Business Rules Classes**
```
<<Control>> MenuValidationRules
├── Attributes:
│ ├── - maxMenuItems: Integer
│ ├── - maxPrice: Decimal
│ └── - requiredFields: List<String>
├── Operations:
│ ├── + validateMenu(menu: Menu): ValidationResult
│ ├── + validateMenuItem(item: MenuItem): ValidationResult
│ ├── + validatePrice(price: Decimal): Boolean
│ └── + validateDescription(description: String): Boolean
└── Relationships:
 └── uses → Menu

<<Control>> UserPermissionRules
├── Attributes:
│ ├── - rolePermissions: Map<Role, List<Permission>>
│ └── - resourcePermissions: Map<Resource, List<Permission>>
├── Operations:
│ ├── + checkPermission(userID: String, resource: String, action: String): Boolean
│ ├── + getUserRole(userID: String): Role
│ ├── + hasPermission(role: Role, permission: Permission): Boolean
│ └── + grantPermission(userID: String, permission: Permission): Boolean
└── Relationships:
 ├── uses → User
 └── uses → Role

<<Control>> SpamDetectionRules
├── Attributes:
│ ├── - spamKeywords: List<String>
│ ├── - maxContentLength: Integer
│ └── - suspiciousPatterns: List<Pattern>
├── Operations:
│ ├── + detectSpam(content: String): SpamResult
│ ├── + analyzeBehavior(userID: String): BehaviorAnalysis
│ ├── + checkRateLimit(userID: String, action: String): Boolean
│ └── + flagSuspiciousActivity(userID: String, activity: Activity): void
└── Relationships:
 ├── uses → User
 └── uses → Content
```

### **Data Access Layer Classes**

#### **Repository Classes**
```
<<Entity>> UserRepository
├── Attributes:
│ ├── - connection: DatabaseConnection
│ └── - cache: Cache
├── Operations:
│ ├── + findById(userID: String): User
│ ├── + findByEmail(email: String): User
│ ├── + save(user: User): Boolean
│ ├── + update(user: User): Boolean
│ ├── + delete(userID: String): Boolean
│ └── + findAll(): List<User>
└── Relationships:
 ├── uses → User
 └── uses → DatabaseConnection

<<Entity>> MenuRepository
├── Attributes:
│ ├── - connection: DatabaseConnection
│ └── - cache: Cache
├── Operations:
│ ├── + findById(menuID: String): Menu
│ ├── + findByRestaurant(restaurantID: String): List<Menu>
│ ├── + save(menu: Menu): Boolean
│ ├── + update(menu: Menu): Boolean
│ ├── + delete(menuID: String): Boolean
│ └── + search(query: String): List<Menu>
└── Relationships:
 ├── uses → Menu
 └── uses → DatabaseConnection

<<Entity>> RestaurantRepository
├── Attributes:
│ ├── - connection: DatabaseConnection
│ └── - cache: Cache
├── Operations:
│ ├── + findById(restaurantID: String): Restaurant
│ ├── + findByLocation(location: Location): List<Restaurant>
│ ├── + save(restaurant: Restaurant): Boolean
│ ├── + update(restaurant: Restaurant): Boolean
│ ├── + delete(restaurantID: String): Boolean
│ └── + search(query: String): List<Restaurant>
└── Relationships:
 ├── uses → Restaurant
 └── uses → DatabaseConnection

<<Entity>> FavoriteRepository
├── Attributes:
│ ├── - connection: DatabaseConnection
│ └── - cache: Cache
├── Operations:
│ ├── + findByUser(userID: String): List<Favorite>
│ ├── + findByItem(itemID: String): List<Favorite>
│ ├── + save(favorite: Favorite): Boolean
│ ├── + delete(favoriteID: String): Boolean
│ └── + exists(userID: String, itemID: String): Boolean
└── Relationships:
 ├── uses → Favorite
 └── uses → DatabaseConnection
```

#### **Data Mapper Classes**
```
<<Entity>> UserMapper
├── Attributes:
│ └── - fieldMappings: Map<String, String>
├── Operations:
│ ├── + toDomain(record: DatabaseRecord): User
│ ├── + toRecord(user: User): DatabaseRecord
│ ├── + mapFields(record: DatabaseRecord): User
│ └── + validateMapping(user: User): Boolean
└── Relationships:
 ├── uses → User
 └── uses → DatabaseRecord

<<Entity>> MenuMapper
├── Attributes:
│ └── - fieldMappings: Map<String, String>
├── Operations:
│ ├── + toDomain(record: DatabaseRecord): Menu
│ ├── + toRecord(menu: Menu): DatabaseRecord
│ ├── + mapFields(record: DatabaseRecord): Menu
│ └── + validateMapping(menu: Menu): Boolean
└── Relationships:
 ├── uses → Menu
 └── uses → DatabaseRecord

<<Entity>> RestaurantMapper
├── Attributes:
│ └── - fieldMappings: Map<String, String>
├── Operations:
│ ├── + toDomain(record: DatabaseRecord): Restaurant
│ ├── + toRecord(restaurant: Restaurant): DatabaseRecord
│ ├── + mapFields(record: DatabaseRecord): Restaurant
│ └── + validateMapping(restaurant: Restaurant): Boolean
└── Relationships:
 ├── uses → Restaurant
 └── uses → DatabaseRecord
```

### **Security Subsystem Classes**

#### **Authentication Service Classes**
```
<<Control>> AuthenticationService
├── Attributes:
│ ├── - userRepository: UserRepository
│ ├── - sessionManager: SessionManager
│ ├── - passwordHasher: PasswordHasher
│ └── - tokenGenerator: TokenGenerator
├── Operations:
│ ├── + validateUser(credentials: String): Boolean
│ ├── + authenticateUser(username: String, password: String): String
│ ├── + verifyPassword(username: String, password: String): Boolean
│ ├── + generateSessionToken(userID: String): String
│ ├── + updateLastLogin(userID: String): void
│ └── + logoutUser(sessionToken: String): void
└── Relationships:
 ├── uses → UserRepository
 ├── uses → SessionManager
 └── uses → PasswordHasher

<<Control>> SessionManager
├── Attributes:
│ ├── - activeSessions: Map<String, Session>
│ ├── - sessionTimeout: Integer
│ └── - maxSessions: Integer
├── Operations:
│ ├── + createSession(userID: String): Session
│ ├── + validateSession(sessionToken: String): Boolean
│ ├── + refreshSession(sessionToken: String): Session
│ ├── + invalidateSession(sessionToken: String): void
│ └── + cleanupExpiredSessions(): void
└── Relationships:
 ├── uses → Session
 └── uses → User

<<Control>> PasswordHasher
├── Attributes:
│ ├── - saltRounds: Integer
│ └── - algorithm: String
├── Operations:
│ ├── + hashPassword(password: String): String
│ ├── + verifyPassword(password: String, hash: String): Boolean
│ ├── + generateSalt(): String
│ └── + validatePasswordStrength(password: String): Boolean
└── Relationships:
 └── uses → Password

<<Control>> TokenGenerator
├── Attributes:
│ ├── - secretKey: String
│ ├── - expirationTime: Integer
│ └── - algorithm: String
├── Operations:
│ ├── + generateAccessToken(userID: String): String
│ ├── + generateRefreshToken(userID: String): String
│ ├── + validateToken(token: String): Boolean
│ ├── + extractUserID(token: String): String
│ └── + refreshToken(refreshToken: String): String
└── Relationships:
 └── uses → Token
```

#### **Authorization Service Classes**
```
<<Control>> AuthorizationService
├── Attributes:
│ ├── - roleManager: RoleManager
│ ├── - permissionChecker: PermissionChecker
│ └── - accessController: AccessController
├── Operations:
│ ├── + checkPermission(userID: String, resource: String, action: String): Boolean
│ ├── + getUserRole(userID: String): Role
│ ├── + grantPermission(userID: String, permission: Permission): Boolean
│ ├── + revokePermission(userID: String, permission: Permission): Boolean
│ └── + hasAccess(userID: String, resource: String): Boolean
└── Relationships:
 ├── uses → RoleManager
 ├── uses → PermissionChecker
 └── uses → User

<<Control>> RoleManager
├── Attributes:
│ ├── - roles: Map<String, Role>
│ └── - roleHierarchy: Map<Role, List<Role>>
├── Operations:
│ ├── + createRole(roleName: String, permissions: List<Permission>): Role
│ ├── + assignRole(userID: String, role: Role): Boolean
│ ├── + removeRole(userID: String, role: Role): Boolean
│ ├── + getRolePermissions(role: Role): List<Permission>
│ └── + validateRole(role: Role): Boolean
└── Relationships:
 ├── uses → Role
 └── uses → Permission

<<Control>> PermissionChecker
├── Attributes:
│ ├── - permissionCache: Cache
│ └── - permissionRules: List<PermissionRule>
├── Operations:
│ ├── + checkPermission(userID: String, permission: Permission): Boolean
│ ├── + hasPermission(role: Role, permission: Permission): Boolean
│ ├── + checkResourceAccess(userID: String, resource: String): Boolean
│ └── + validatePermission(permission: Permission): Boolean
└── Relationships:
 ├── uses → Permission
 └── uses → Role
```

### **Menu Management Subsystem Classes**

#### **Menu Service Classes**
```
<<Control>> MenuService
├── Attributes:
│ ├── - menuRepository: MenuRepository
│ ├── - searchService: SearchService
│ └── - cache: Cache
├── Operations:
│ ├── + getMenu(restaurantID: String): Menu
│ ├── + getMenuItem(menuID: String, itemID: String): MenuItem
│ ├── + searchMenus(query: String, filters: SearchFilters): List<Menu>
│ ├── + updateMenu(menuID: String, updates: MenuUpdate): Boolean
│ └── + deleteMenu(menuID: String): Boolean
└── Relationships:
 ├── uses → MenuRepository
 ├── uses → SearchService
 └── uses → Menu

<<Control>> SearchService
├── Attributes:
│ ├── - searchIndex: SearchIndex
│ ├── - searchStrategies: Map<String, SearchStrategy>
│ └── - cache: Cache
├── Operations:
│ ├── + search(query: String, strategy: String): List<SearchResult>
│ ├── + searchByLocation(location: Location): List<Restaurant>
│ ├── + searchByCuisine(cuisine: String): List<Restaurant>
│ ├── + searchByPrice(priceRange: PriceRange): List<Menu>
│ └── + indexContent(content: Content): Boolean
└── Relationships:
 ├── uses → SearchStrategy
 ├── uses → SearchIndex
 └── uses → SearchResult

<<Control>> RestaurantService
├── Attributes:
│ ├── - restaurantRepository: RestaurantRepository
│ ├── - locationService: LocationService
│ └── - ratingCalculator: RatingCalculator
├── Operations:
│ ├── + getRestaurant(restaurantID: String): Restaurant
│ ├── + getRestaurantsByLocation(location: Location): List<Restaurant>
│ ├── + updateRestaurant(restaurantID: String, updates: RestaurantUpdate): Boolean
│ ├── + calculateRating(restaurantID: String): Rating
│ └── + verifyRestaurant(restaurantID: String): Boolean
└── Relationships:
 ├── uses → RestaurantRepository
 ├── uses → LocationService
 └── uses → Restaurant
```

#### **Verification Service Classes**
```
<<Control>> VerificationService
├── Attributes:
│ ├── - contentValidator: ContentValidator
│ ├── - authenticityChecker: AuthenticityChecker
│ └── - approvalWorkflow: ApprovalWorkflow
├── Operations:
│ ├── + verifyMenu(menuID: String): VerificationResult
│ ├── + verifyContent(content: String): VerificationResult
│ ├── + checkAuthenticity(menuID: String): Boolean
│ ├── + approveContent(contentID: String): Boolean
│ └── + rejectContent(contentID: String, reason: String): Boolean
└── Relationships:
 ├── uses → ContentValidator
 ├── uses → AuthenticityChecker
 └── uses → VerificationResult

<<Control>> ContentValidator
├── Attributes:
│ ├── - validationRules: List<ValidationRule>
│ └── - spamDetector: SpamDetector
├── Operations:
│ ├── + validateContent(content: String): ValidationResult
│ ├── + validateMenu(menu: Menu): ValidationResult
│ ├── + checkSpam(content: String): SpamResult
│ └── + validateFormat(content: String, format: String): Boolean
└── Relationships:
 ├── uses → ValidationRule
 └── uses → SpamDetector
```

### **User Management Subsystem Classes**

#### **User Service Classes**
```
<<Control>> UserService
├── Attributes:
│ ├── - userRepository: UserRepository
│ ├── - profileManager: ProfileManager
│ └── - accountManager: AccountManager
├── Operations:
│ ├── + registerUser(userData: UserRegistration): Boolean
│ ├── + updateProfile(userID: String, profile: UserProfile): Boolean
│ ├── + getUserProfile(userID: String): UserProfile
│ ├── + deactivateAccount(userID: String): Boolean
│ └── + validateUser(userID: String): Boolean
└── Relationships:
 ├── uses → UserRepository
 ├── uses → ProfileManager
 └── uses → User

<<Control>> FavoritesService
├── Attributes:
│ ├── - favoriteRepository: FavoriteRepository
│ ├── - organizer: FavoritesOrganizer
│ └── - cache: Cache
├── Operations:
│ ├── + addFavorite(userID: String, itemID: String): Boolean
│ ├── + removeFavorite(userID: String, itemID: String): Boolean
│ ├── + getUserFavorites(userID: String): List<Favorite>
│ ├── + organizeFavorites(userID: String, categories: List<String>): Boolean
│ └── + shareFavorites(userID: String, shareWith: String): Boolean
└── Relationships:
 ├── uses → FavoriteRepository
 ├── uses → FavoritesOrganizer
 └── uses → Favorite

<<Control>> PreferencesService
├── Attributes:
│ ├── - preferencesRepository: PreferencesRepository
│ ├── - settingsManager: SettingsManager
│ └── - privacyManager: PrivacyManager
├── Operations:
│ ├── + updatePreferences(userID: String, preferences: UserPreferences): Boolean
│ ├── + getPreferences(userID: String): UserPreferences
│ ├── + updateNotificationSettings(userID: String, settings: NotificationSettings): Boolean
│ ├── + updatePrivacySettings(userID: String, settings: PrivacySettings): Boolean
│ └── + resetToDefaults(userID: String): Boolean
└── Relationships:
 ├── uses → PreferencesRepository
 ├── uses → SettingsManager
 └── uses → UserPreferences
```

### **Notification Subsystem Classes**

#### **Email Service Classes**
```
<<Control>> EmailService
├── Attributes:
│ ├── - emailSender: EmailSender
│ ├── - templateEngine: TemplateEngine
│ └── - emailQueue: EmailQueue
├── Operations:
│ ├── + sendEmail(to: String, subject: String, body: String): Boolean
│ ├── + sendTemplateEmail(to: String, template: String, data: Map): Boolean
│ ├── + queueEmail(email: Email): Boolean
│ ├── + processEmailQueue(): void
│ └── + validateEmail(email: String): Boolean
└── Relationships:
 ├── uses → EmailSender
 ├── uses → TemplateEngine
 └── uses → Email

<<Control>> NotificationService
├── Attributes:
│ ├── - pushService: PushService
│ ├── - inAppService: InAppService
│ └── - notificationQueue: NotificationQueue
├── Operations:
│ ├── + sendPushNotification(userID: String, message: String): Boolean
│ ├── + sendInAppNotification(userID: String, notification: Notification): Boolean
│ ├── + scheduleNotification(notification: Notification, scheduleTime: DateTime): Boolean
│ ├── + markAsRead(notificationID: String): Boolean
│ └── + getUserNotifications(userID: String): List<Notification>
└── Relationships:
 ├── uses → PushService
 ├── uses → InAppService
 └── uses → Notification

<<Control>> RealTimeService
├── Attributes:
│ ├── - webSocketManager: WebSocketManager
│ ├── - eventBroadcaster: EventBroadcaster
│ └── - connectionManager: ConnectionManager
├── Operations:
│ ├── + connectUser(userID: String, connection: WebSocketConnection): Boolean
│ ├── + disconnectUser(userID: String): Boolean
│ ├── + broadcastEvent(event: Event): Boolean
│ ├── + sendToUser(userID: String, message: String): Boolean
│ └── + getActiveConnections(): List<WebSocketConnection>
└── Relationships:
 ├── uses → WebSocketManager
 ├── uses → EventBroadcaster
 └── uses → WebSocketConnection
```

---

## Class Relationships

### **Inheritance Relationships**
```
<<Entity>> User
├── <<Entity>> RegularUser
├── <<Entity>> PremiumUser
├── <<Entity>> RestaurantOwner
└── <<Entity>> Administrator

<<Entity>> Menu
├── <<Entity>> FoodMenu
├── <<Entity>> BeverageMenu
└── <<Entity>> DessertMenu

<<Entity>> Notification
├── <<Entity>> EmailNotification
├── <<Entity>> PushNotification
└── <<Entity>> InAppNotification
```

### **Composition Relationships**
```
<<Control>> MenuController
├── contains → MenuService
├── contains → SearchService
└── contains → VerificationService

<<Control>> AuthenticationController
├── contains → AuthenticationService
├── contains → SessionManager
└── contains → PasswordHasher

<<Control>> UserController
├── contains → UserService
├── contains → FavoritesService
└── contains → PreferencesService
```

### **Association Relationships**
```
<<Boundary>> WebInterface
├── uses → AuthenticationController
├── uses → MenuController
├── uses → UserController
└── uses → RestaurantController

<<Control>> AuthenticationService
├── uses → UserRepository
├── uses → SessionManager
└── uses → PasswordHasher

<<Control>> MenuService
├── uses → MenuRepository
├── uses → SearchService
└── uses → RestaurantRepository
```

---

## Design Patterns Implementation

### **Observer Pattern**
```
<<Control>> MenuManager (Subject)
├── + attach(observer: Observer): void
├── + detach(observer: Observer): void
├── + notify(): void
└── Relationships:
 ├── observed by → UserFavorites (Observer)
 ├── observed by → RestaurantOwner (Observer)
 └── observed by → AdminDashboard (Observer)
```

### **Factory Pattern**
```
<<Control>> UserFactory
├── + createRegularUser(userData: UserData): RegularUser
├── + createPremiumUser(userData: UserData): PremiumUser
├── + createRestaurantOwner(userData: UserData): RestaurantOwner
└── + createAdminUser(userData: UserData): Administrator

<<Control>> MenuFactory
├── + createFoodMenu(menuData: MenuData): FoodMenu
├── + createBeverageMenu(menuData: MenuData): BeverageMenu
└── + createDessertMenu(menuData: MenuData): DessertMenu
```

### **Strategy Pattern**
```
<<Control>> SearchContext
├── - searchStrategy: SearchStrategy
├── + setStrategy(strategy: SearchStrategy): void
├── + executeSearch(query: String): List<SearchResult>
└── Relationships:
 ├── uses → LocationSearchStrategy
 ├── uses → CuisineSearchStrategy
 ├── uses → PriceSearchStrategy
 └── uses → RatingSearchStrategy
```

---

## Class Diagram Benefits

### **Maintainability**
- Clear separation of concerns
- Well-defined class responsibilities
- Minimal coupling between classes
- High cohesion within classes

### **Scalability**
- Modular class design
- Independent class scaling
- Easy to add new classes
- Flexible class relationships

### **Testability**
- Independent class testing
- Mock interface implementation
- Clear class dependencies
- Isolated class functionality

---

*This detailed class diagram provides the comprehensive foundation for MenuMap's object-oriented design and implementation.*
