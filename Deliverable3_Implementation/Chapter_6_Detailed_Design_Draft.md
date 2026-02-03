# Chapter 6: Detailed Design
## MenuMap Final Systems Document

**Author:** Andre Lewis (Team Lead) 
**Date:** December 2024 
**Status:** Final - Ready for Document Integration 
**Support:** Alfonso Oramas (Class Diagrams for Section 6.4)

---

## Introduction

This chapter provides the detailed design of the MenuMap system, describing the internal structure, class relationships, object interactions, and state management. The detailed design builds upon the software architecture described in Chapter 5 and provides the implementation-level specifications needed for development and testing.

The design follows the three-tier architecture (MM_Client, MM_Logic, MM_DataStore) with clear separation of concerns. This chapter includes class diagrams showing the system's structure, sequence diagrams illustrating object interactions for implemented use cases, and state machine models describing entity state transitions. The detailed design ensures that all components work together cohesively to fulfill the system requirements outlined in Chapter 4.

---

## 6.1 Overview

The MenuMap system is organized into three primary packages corresponding to the three-tier architecture: **MM_Client**, **MM_Logic**, and **MM_DataStore**. Each package contains classes that handle specific responsibilities within their respective tiers.

### Package Structure

**MM_Client Package (Presentation Tier)**:
This package contains classes responsible for user interface components and user interactions. Key classes include:
- **LoginForm**: Handles user authentication interface
- **Dashboard**: Main application dashboard
- **MenuBrowser**: Displays restaurant menus and items
- **UserProfile**: Manages user profile information
- **RestaurantOwnerPanel**: Interface for restaurant owners to manage menus

**Figure 6.1: Presentation Layer Class Diagram**

[Insert diagram: `Package_MM_Client_MM_Client_Class_Dia.PNG`]

**Caption:** The Presentation Layer Class Diagram shows the client-side components including Controllers and Views. This layer handles all user interface interactions and HTTP request/response processing.

**MM_Logic Package (Business Logic Tier)**:
This package contains classes that implement business rules and orchestrate use case execution. Key classes include:
- **MenuBrowsingController**: Orchestrates menu browsing operations
- **AuthenticationController**: Handles authentication logic
- **FavoritesController**: Manages user favorites
- **MenuVerificationController**: Handles menu verification processes
- **BusinessRules**: Enforces business rules and validations

**Figure 6.2: Business Logic Layer Class Diagram**

[Insert diagram: `Package_MM_Logic_MM_Logic_Class_Dia.PNG`]

**Caption:** The Business Logic Layer Class Diagram illustrates service classes that implement core business rules, validation, and processing logic.

**MM_DataStore Package (Data Tier)**:
This package contains classes responsible for data persistence and retrieval. Key classes include:
- **UserRepository**: Manages user data operations
- **MenuRepository**: Handles menu data operations
- **RestaurantRepository**: Manages restaurant data
- **DatabaseConnection**: Manages database connections
- **CacheManager**: Handles caching operations

**Figure 6.3: Data Access Layer Class Diagram**

[Insert diagram: `Package_MM_DataStore_MM_Data_Store_Dia.PNG`]

**Caption:** The Data Access Layer Class Diagram shows Data Access Objects (DAOs) and data models that manage database operations and data persistence.

### Design Patterns Used

The system incorporates several design patterns:

1. **MVC Pattern** (in MM_Client): Separates presentation logic from business logic
2. **Repository Pattern** (in MM_DataStore): Provides abstraction for data access
3. **Controller Pattern** (in MM_Logic): Coordinates between presentation and data layers
4. **Observer Pattern**: Used for real-time updates and notifications
5. **Factory Pattern**: Facilitates object creation
6. **Strategy Pattern**: Enables interchangeable algorithms
7. **DAO Pattern**: Abstracts database operations

### Class Relationships

The classes in each package interact through well-defined interfaces:

- **MM_Client** classes communicate with **MM_Logic** controllers through service interfaces
- **MM_Logic** controllers use **MM_DataStore** repositories for data operations
- **MM_DataStore** repositories interact with the database and cache systems
- Cross-cutting concerns (security, logging) are handled by dedicated services

**Reference Diagram:** `Model_Static_Menu_Map_3_Tier.PNG` (See Appendix D)

---

## 6.2 State Machine Model

The MenuMap system includes state machines for managing entity states and transitions. The primary state machine models user authentication states.

### User Authentication State Machine

The user authentication process follows a state machine that tracks the authentication state of users throughout their interaction with the system.

**States**:
- **Unauthenticated**: User is not logged in
- **Authenticating**: User is in the process of logging in
- **Authenticated**: User has successfully logged in
- **Session Expired**: User's session has expired
- **Locked**: User account has been locked due to security reasons

**Transitions**:
- **Unauthenticated → Authenticating**: User initiates login
- **Authenticating → Authenticated**: Login successful
- **Authenticating → Unauthenticated**: Login failed
- **Authenticated → Session Expired**: Session timeout occurs
- **Authenticated → Unauthenticated**: User logs out
- **Authenticated → Locked**: Account locked due to suspicious activity
- **Session Expired → Unauthenticated**: User must re-authenticate
- **Locked → Unauthenticated**: Account unlocked by administrator

**Figure 6.4: User Authentication State Machine**

[Insert diagram: `State_Machine_UserAuthentication_StateMachine_MM_State_Machine_Dia.PNG` or `State_Machine_StateMachine1_UserAuthentication_StateMachine.PNG`]

**Caption:** The User Authentication State Machine diagram shows the states and transitions for user authentication in the MenuMap system.

### State Management

State transitions are managed by the **AuthenticationController** in the MM_Logic package, which coordinates with the **Security Subsystem** to enforce authentication rules and session management. The state machine ensures that users can only access appropriate resources based on their current authentication state.

**State Transition Details**:

**Unauthenticated State**:
- Initial state for all users
- User can register or attempt to log in
- No access to protected resources

**Authenticating State**:
- User has submitted login credentials
- System validates credentials
- Temporary state during authentication process

**Authenticated State**:
- User has successfully logged in
- Session token is valid
- User can access protected resources
- Session timeout timer is active

**Session Expired State**:
- Session token has expired
- User must re-authenticate
- Temporary state before returning to Unauthenticated

**Locked State**:
- Account locked due to security reasons
- Multiple failed login attempts
- Requires administrator intervention
- No authentication possible

---

## 6.3 Object Interaction (Sequence Diagrams)

This section presents sequence diagrams for the implemented use cases, showing the object interactions between the three tiers (MM_Client, MM_Logic, MM_DataStore) and the flow of messages between components.

### UC-001: Browse Restaurant Menus

This sequence diagram illustrates how a user browses restaurant menus. The interaction flows from the MenuBrowser in the presentation layer, through the MenuBrowsingController in the business logic layer, to the MenuRepository in the data access layer.

**Key Interactions**:
1. User initiates menu browse request through MenuBrowser
2. MenuBrowser sends request to MenuBrowsingController
3. MenuBrowsingController validates request and queries MenuRepository
4. MenuRepository retrieves menu data from database
5. Data flows back through layers to MenuBrowser
6. MenuBrowser displays menu to user

**Figure 6.5: UC-001 Sequence Diagram**

[Insert diagram: `UC-001-Browse_Restaurant_Menus_Sequence.PNG` or `Interaction_Interaction4_UC-001-Browse_Restaurant_Menus_Sequence.PNG`]

**Caption:** Sequence Diagram for UC-001: Browse Restaurant Menus showing interaction between User, MenuController, MenuService, MenuDAO, and Database.

**Lifelines**:
- User (Actor)
- MenuController (Presentation Layer)
- MenuService (Business Logic Layer)
- MenuDAO (Data Access Layer)
- Database (External System)

**Message Flow**:
1. User → MenuController: viewMenu(restaurantId)
2. MenuController → MenuService: getMenuByRestaurantId(restaurantId)
3. MenuService → MenuDAO: findMenuByRestaurantId(restaurantId)
4. MenuDAO → Database: SELECT query
5. Database → MenuDAO: ResultSet
6. MenuDAO → MenuService: Menu entity
7. MenuService → MenuController: MenuDTO
8. MenuController → User: displayMenu(menuData)

### UC-005: User Login

This sequence diagram shows the user login process, including authentication, session creation, and security validation.

**Key Interactions**:
1. User submits login credentials through LoginForm
2. LoginForm sends credentials to AuthenticationController
3. AuthenticationController validates credentials with UserRepository
4. UserRepository queries database for user authentication data
5. AuthenticationController creates session and generates JWT token
6. Session information returned to LoginForm
7. User is redirected to Dashboard upon successful login

**Figure 6.6: UC-005 Sequence Diagram**

[Insert diagram: `UC-005-User_Login.PNG` or `Interaction_Interaction1_UC-005-User_Login.PNG`]

**Caption:** Sequence Diagram for UC-005: User Login showing authentication flow through all three tiers.

**Lifelines**:
- User (Actor)
- UserController (Presentation Layer)
- UserService (Business Logic Layer)
- UserDAO (Data Access Layer)
- Database (External System)

**Message Flow**:
1. User → UserController: login(email, password)
2. UserController → UserService: authenticateUser(email, password)
3. UserService → UserDAO: findUserByEmail(email)
4. UserDAO → Database: SELECT query
5. Database → UserDAO: User entity
6. UserDAO → UserService: User entity
7. UserService → UserService: validatePassword(password, hashedPassword)
8. UserService → UserService: createSession(userId)
9. UserService → UserController: SessionDTO
10. UserController → User: redirectToDashboard()

### Additional Sequence Diagrams

The system includes sequence diagrams for other implemented use cases:

- **UC-002: Manage Favorites** - `UC-002-Manage_Favorites_Sequence.PNG`
- **UC-003: Secure Password Reset** - `UC-003-Secure_Password_Reset_Sequence.PNG`
- **UC-004: User Registration** - `UC-004-Registration_Sequence.PNG`
- **UC-006: User Logout** - `UC-006-User_Logout_Sequence.PNG`
- **UC-007: Restaurant Owner Menu Management** - `UC-007-Menu_Management_Sequence.PNG`

All sequence diagrams follow the same 3-tier architecture pattern, showing interactions between Presentation, Business Logic, and Data Access layers.

---

## 6.4 Detailed Class Design

This section provides detailed class diagrams showing all classes with their attributes and methods. The detailed class design is organized by package (MM_Client, MM_Logic, MM_DataStore) and shows the complete structure of each class.

### MM_Client Package Classes

**MenuController Class**:
- **Attributes**: 
 - `menuService: MenuService`
 - `restaurantService: RestaurantService`
- **Methods**: 
 - `viewMenu(restaurantId: int): MenuDTO`
 - `searchRestaurants(query: String): List<RestaurantDTO>`
 - `filterMenuItems(category: String): List<MenuItemDTO>`
 - `handleError(error: Exception): void`

**UserController Class**:
- **Attributes**: 
 - `userService: UserService`
 - `sessionManager: SessionManager`
- **Methods**: 
 - `login(email: String, password: String): SessionDTO`
 - `register(userData: UserRegistrationDTO): UserDTO`
 - `logout(sessionId: String): void`
 - `getUserProfile(userId: String): UserProfileDTO`

**RestaurantController Class**:
- **Attributes**: 
 - `restaurantService: RestaurantService`
 - `menuService: MenuService`
- **Methods**: 
 - `getRestaurantDetails(restaurantId: int): RestaurantDTO`
 - `updateRestaurantInfo(restaurantId: int, data: RestaurantUpdateDTO): void`
 - `getRestaurantList(): List<RestaurantDTO>`

**Reference Diagram:** `Package_MM_Client_MM_Client_Class_Dia.PNG` (See Appendix D)

### MM_Logic Package Classes

**MenuService Class**:
- **Attributes**: 
 - `menuDAO: MenuDAO`
 - `restaurantDAO: RestaurantDAO`
 - `cacheManager: CacheManager`
- **Methods**: 
 - `getMenuByRestaurantId(restaurantId: int): MenuDTO`
 - `validateMenuData(menuData: MenuItemDTO): boolean`
 - `applyMenuFilters(items: List<MenuItem>, category: String): List<MenuItem>`
 - `searchMenuItems(query: String): List<MenuItemDTO>`

**UserService Class**:
- **Attributes**: 
 - `userDAO: UserDAO`
 - `passwordHasher: PasswordHasher`
 - `sessionManager: SessionManager`
- **Methods**: 
 - `authenticateUser(email: String, password: String): UserDTO`
 - `createUser(userData: UserRegistrationDTO): UserDTO`
 - `hashPassword(password: String): String`
 - `validateUserInput(data: UserRegistrationDTO): ValidationResult`

**RestaurantService Class**:
- **Attributes**: 
 - `restaurantDAO: RestaurantDAO`
 - `menuDAO: MenuDAO`
- **Methods**: 
 - `getRestaurantById(id: int): RestaurantDTO`
 - `validateRestaurantData(data: RestaurantDTO): boolean`
 - `processRestaurantUpdate(data: RestaurantUpdateDTO): void`

**VerificationService Class**:
- **Attributes**: 
 - `menuDAO: MenuDAO`
 - `verificationDAO: VerificationDAO`
- **Methods**: 
 - `verifyMenu(menuId: int): VerificationResult`
 - `checkMenuAccuracy(menuData: MenuDTO): boolean`
 - `flagInconsistencies(menuData: MenuDTO): List<String>`

**Reference Diagram:** `Package_MM_Logic_MM_Logic_Class_Dia.PNG` (See Appendix D)

### MM_DataStore Package Classes

**MenuDAO Class**:
- **Attributes**: 
 - `databaseConnection: DatabaseConnection`
 - `cacheManager: CacheManager`
- **Methods**: 
 - `findMenuByRestaurantId(restaurantId: int): Menu`
 - `saveMenu(menuData: Menu): void`
 - `updateMenu(menuId: int, menuData: Menu): void`
 - `deleteMenu(menuId: int): void`
 - `searchMenuItems(query: String): List<MenuItem>`

**UserDAO Class**:
- **Attributes**: 
 - `databaseConnection: DatabaseConnection`
 - `cacheManager: CacheManager`
- **Methods**: 
 - `findUserByEmail(email: String): User`
 - `findUserById(userId: String): User`
 - `saveUser(userData: User): void`
 - `updateUser(userId: String, userData: User): void`
 - `deleteUser(userId: String): void`

**RestaurantDAO Class**:
- **Attributes**: 
 - `databaseConnection: DatabaseConnection`
 - `cacheManager: CacheManager`
- **Methods**: 
 - `findRestaurantById(id: int): Restaurant`
 - `findRestaurantsByName(name: String): List<Restaurant>`
 - `saveRestaurant(data: Restaurant): void`
 - `updateRestaurant(id: int, data: Restaurant): void`
 - `deleteRestaurant(id: int): void`

**DatabaseConnection Class**:
- **Attributes**: 
 - `connectionPool: ConnectionPool`
 - `transactionManager: TransactionManager`
- **Methods**: 
 - `getConnection(): Connection`
 - `executeQuery(sql: String, params: Object[]): ResultSet`
 - `executeTransaction(operations: List<Operation>): void`
 - `closeConnection(): void`

**CacheManager Class**:
- **Attributes**: 
 - `redisClient: RedisClient`
 - `memoryCache: MemoryCache`
- **Methods**: 
 - `get(key: String): Object`
 - `set(key: String, value: Object, ttl: int): void`
 - `delete(key: String): void`
 - `clear(): void`
 - `invalidate(pattern: String): void`

**Reference Diagram:** `Package_MM_DataStore_MM_Data_Store_Dia.PNG` (See Appendix D)

### Class Relationships

The classes are related through:

**Associations**:
- Controllers use Services for business logic operations
- Services use DAOs for data access operations
- DAOs use DatabaseConnection for database operations

**Dependencies**:
- Presentation classes depend on Business Logic services
- Business Logic classes depend on Data Access repositories
- All layers depend on domain models

**Composition**:
- Repositories contain DatabaseConnection and CacheManager
- Controllers aggregate multiple Services
- Services aggregate multiple DAOs

**Inheritance**:
- Base classes for common functionality
- Interface implementations for abstraction

**Reference Diagram:** Detailed class diagrams in Appendix D

---

## References

- Chapter 5: Software Architecture
- Appendix D: Detailed Class Diagrams
- Deliverable 2: Design Document (UML Diagrams)
- Chapter 4: System Requirements

---

## Notes for Integration

1. **Diagrams**: All sequence diagrams and class diagrams are available as PNG files in `Deliverable2_Design/UML_Diagrams/Diagrams_Only/`. Insert these diagrams into the Final Document at appropriate locations.

2. **Coordination with Alfonso**: Section 6.4 (Detailed Class Design) should be coordinated with Alfonso Oramas, who is responsible for Appendix D (Detailed Class Diagrams). Ensure consistency between this section and Appendix D.

3. **Formatting**: Maintain required formatting (1.5 line spacing, 16pt chapter headings, 13pt section headings, 11pt text) when integrating into the Final Document.

4. **Present Tense**: All descriptions should be in present tense, as the system is implemented.

5. **Diagram References**: All diagrams should be properly referenced and captioned in the Final Document.

---

**Note**: This content should be integrated into the Final Systems Document Word file. Coordinate with Alfonso Oramas for Section 6.4 to ensure detailed class diagrams are consistent with Appendix D.

