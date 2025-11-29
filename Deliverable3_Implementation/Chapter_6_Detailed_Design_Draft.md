# Chapter 6: Detailed Design - Draft Content
## MenuMap Final Systems Document

**Author:** Andre Lewis (Group Lead)  
**Date:** [Current Date]  
**Status:** Draft - Ready for Final Document Integration  
**Support:** Alfonso Oramas (Class Diagrams for Section 6.4)

---

## 6.0 Introduction

This chapter provides the detailed design of the MenuMap system, describing the internal structure, class relationships, object interactions, and state management. The detailed design builds upon the software architecture described in Chapter 5 and provides the implementation-level specifications needed for development and testing.

The design follows the three-tier architecture (MM_Client, MM_Logic, MM_DataStore) with clear separation of concerns. This chapter includes class diagrams showing the system's structure, sequence diagrams illustrating object interactions for implemented use cases, and state machine models describing entity state transitions. The detailed design ensures that all components work together cohesively to fulfill the system requirements outlined in Chapter 4.

---

## 6.1 Overview (Minimum Class Diagram)

The MenuMap system is organized into three primary packages corresponding to the three-tier architecture: **MM_Client**, **MM_Logic**, and **MM_DataStore**. Each package contains classes that handle specific responsibilities within their respective tiers.

### Package Structure

**MM_Client Package (Presentation Tier)**:
This package contains classes responsible for user interface components and user interactions. Key classes include:
- **LoginForm**: Handles user authentication interface
- **Dashboard**: Main application dashboard
- **MenuBrowser**: Displays restaurant menus and items
- **UserProfile**: Manages user profile information
- **RestaurantOwnerPanel**: Interface for restaurant owners to manage menus

**Reference Diagram:** `Package_MM_Client_MM_Client_Class_Dia.PNG` (See Appendix D)

**MM_Logic Package (Business Logic Tier)**:
This package contains classes that implement business rules and orchestrate use case execution. Key classes include:
- **MenuBrowsingController**: Orchestrates menu browsing operations
- **AuthenticationController**: Handles authentication logic
- **FavoritesController**: Manages user favorites
- **MenuVerificationController**: Handles menu verification processes
- **BusinessRules**: Enforces business rules and validations

**Reference Diagram:** `Package_MM_Logic_MM_Logic_Class_Dia.PNG` (See Appendix D)

**MM_DataStore Package (Data Tier)**:
This package contains classes responsible for data persistence and retrieval. Key classes include:
- **UserRepository**: Manages user data operations
- **MenuRepository**: Handles menu data operations
- **RestaurantRepository**: Manages restaurant data
- **DatabaseConnection**: Manages database connections
- **CacheManager**: Handles caching operations

**Reference Diagram:** `Package_MM_DataStore_MM_Data_Store_Dia.PNG` (See Appendix D)

### Design Patterns Used

The system incorporates several design patterns:

1. **MVC Pattern** (in MM_Client): Separates presentation logic from business logic
2. **Repository Pattern** (in MM_DataStore): Provides abstraction for data access
3. **Controller Pattern** (in MM_Logic): Coordinates between presentation and data layers
4. **Observer Pattern**: Used for real-time updates and notifications
5. **Factory Pattern**: Facilitates object creation
6. **Strategy Pattern**: Enables interchangeable algorithms

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

**Reference Diagram:** `State_Machine_UserAuthentication_StateMachine_MM_State_Machine_Dia.PNG` (See Appendix D)

### State Management

State transitions are managed by the **AuthenticationController** in the MM_Logic package, which coordinates with the **Security Subsystem** to enforce authentication rules and session management. The state machine ensures that users can only access appropriate resources based on their current authentication state.

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

**Reference Diagram:** `UC-001-Browse_Restaurant_Menus_Sequence.PNG` (See Appendix D)

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

**Reference Diagram:** `UC-005-User_Login.PNG` (See Appendix D)

### UC-004: User Registration

This sequence diagram illustrates the user registration process, including data validation, account creation, and email verification.

**Key Interactions**:
1. User submits registration form through RegistrationForm
2. RegistrationForm sends data to UserRegistrationController
3. UserRegistrationController validates data and checks for existing users
4. UserRepository creates new user account in database
5. NotificationService sends verification email
6. Confirmation returned to RegistrationForm
7. User receives email verification link

**Reference Diagram:** `UC-004-Registration_Sequence.PNG` (See Appendix D)

### UC-002: Manage Favorites

This sequence diagram shows how users add, remove, and view their favorite restaurants.

**Key Interactions**:
1. User selects favorite action through MenuBrowser
2. MenuBrowser sends request to FavoritesController
3. FavoritesController validates user authentication
4. FavoritesController updates favorites through FavoriteRepository
5. FavoriteRepository persists changes to database
6. Updated favorites list returned to MenuBrowser
7. MenuBrowser displays updated favorites to user

**Reference Diagram:** `UC-002-Manage_Favorites_Sequence.PNG` (See Appendix D)

### UC-003: Secure Password Reset

This sequence diagram illustrates the secure password reset process, including token generation, email delivery, and password update.

**Key Interactions**:
1. User requests password reset through PasswordResetForm
2. PasswordResetForm sends request to AuthenticationController
3. AuthenticationController generates secure reset token
4. Token stored in database through UserRepository
5. NotificationService sends reset email with token
6. User clicks reset link and submits new password
7. AuthenticationController validates token and updates password
8. Password updated in database through UserRepository
9. Confirmation returned to user

**Reference Diagram:** `UC-003-Secure_Password_Reset_Sequence.PNG` (See Appendix D)

### UC-007: Restaurant Owner Menu Management

This sequence diagram shows how restaurant owners manage their menu items, including adding, updating, and deleting items.

**Key Interactions**:
1. Restaurant owner accesses RestaurantOwnerPanel
2. RestaurantOwnerPanel sends menu management request to RestaurantOwnerController
3. RestaurantOwnerController validates owner permissions
4. MenuRepository performs CRUD operations on menu items
5. Changes persisted to database
6. Updated menu returned to RestaurantOwnerPanel
7. RestaurantOwnerPanel displays updated menu

**Reference Diagram:** `UC-007-Menu_Management_Sequence.PNG` (See Appendix D)

### UC-006: User Logout

This sequence diagram illustrates the user logout process, including session termination and cleanup.

**Key Interactions**:
1. User initiates logout through Dashboard
2. Dashboard sends logout request to AuthenticationController
3. AuthenticationController invalidates session
4. Session removed from database through UserRepository
5. JWT token invalidated
6. Confirmation returned to Dashboard
7. User redirected to login page

**Reference Diagram:** `UC-006-User_Logout_Sequence.PNG` (See Appendix D)

---

## 6.4 Detailed Class Design (Detailed Class Diagram)

This section provides detailed class diagrams showing all classes with their attributes and methods. The detailed class design is organized by package (MM_Client, MM_Logic, MM_DataStore) and shows the complete structure of each class.

### MM_Client Package Classes

**LoginForm Class**:
- **Attributes**: username, password, errorMessage, isLoading
- **Methods**: handleSubmit(), validateInput(), displayError(), redirectToDashboard()

**Dashboard Class**:
- **Attributes**: userInfo, menuItems, favorites, notifications
- **Methods**: loadDashboard(), displayMenu(), addToFavorites(), handleLogout()

**MenuBrowser Class**:
- **Attributes**: restaurants, menuItems, selectedRestaurant, filters
- **Methods**: searchRestaurants(), displayMenu(), applyFilters(), addToFavorites()

**UserProfile Class**:
- **Attributes**: userData, preferences, favorites
- **Methods**: loadProfile(), updateProfile(), updatePreferences(), viewFavorites()

**RestaurantOwnerPanel Class**:
- **Attributes**: restaurantInfo, menuItems, editMode
- **Methods**: loadMenu(), addMenuItem(), updateMenuItem(), deleteMenuItem(), saveChanges()

**Reference Diagram:** `Package_MM_Client_MM_Client_Class_Dia.PNG` (See Appendix D)

### MM_Logic Package Classes

**MenuBrowsingController Class**:
- **Attributes**: menuRepository, cacheManager
- **Methods**: browseMenu(), searchRestaurants(), filterMenuItems(), getMenuByRestaurant()

**AuthenticationController Class**:
- **Attributes**: userRepository, sessionManager, tokenGenerator
- **Methods**: authenticateUser(), createSession(), validateToken(), logout(), resetPassword()

**FavoritesController Class**:
- **Attributes**: favoriteRepository, userRepository
- **Methods**: addFavorite(), removeFavorite(), getFavorites(), isFavorite()

**UserRegistrationController Class**:
- **Attributes**: userRepository, notificationService, validator
- **Methods**: registerUser(), validateRegistrationData(), sendVerificationEmail(), activateAccount()

**MenuVerificationController Class**:
- **Attributes**: menuRepository, verificationRepository
- **Methods**: verifyMenu(), submitVerification(), approveVerification(), rejectVerification()

**RestaurantOwnerController Class**:
- **Attributes**: menuRepository, restaurantRepository, permissionChecker
- **Methods**: createMenuItem(), updateMenuItem(), deleteMenuItem(), manageRestaurant()

**BusinessRules Class**:
- **Attributes**: validationRules, permissionRules
- **Methods**: validateMenuData(), checkUserPermissions(), enforceBusinessRules()

**Reference Diagram:** `Package_MM_Logic_MM_Logic_Class_Dia.PNG` (See Appendix D)

### MM_DataStore Package Classes

**UserRepository Class**:
- **Attributes**: databaseConnection, cacheManager
- **Methods**: findUserById(), findUserByEmail(), createUser(), updateUser(), deleteUser(), authenticateUser()

**MenuRepository Class**:
- **Attributes**: databaseConnection, cacheManager
- **Methods**: findMenuByRestaurant(), searchMenuItems(), createMenuItem(), updateMenuItem(), deleteMenuItem()

**RestaurantRepository Class**:
- **Attributes**: databaseConnection, cacheManager
- **Methods**: findRestaurantById(), searchRestaurants(), createRestaurant(), updateRestaurant(), deleteRestaurant()

**FavoriteRepository Class**:
- **Attributes**: databaseConnection, cacheManager
- **Methods**: addFavorite(), removeFavorite(), getFavorites(), isFavorite()

**DatabaseConnection Class**:
- **Attributes**: connectionPool, transactionManager
- **Methods**: getConnection(), executeQuery(), executeTransaction(), closeConnection()

**CacheManager Class**:
- **Attributes**: redisClient, memoryCache
- **Methods**: get(), set(), delete(), clear(), invalidate()

**Reference Diagram:** `Package_MM_DataStore_MM_Data_Store_Dia.PNG` (See Appendix D)

### Class Relationships

The classes are related through:
- **Association**: Controllers use Repositories for data access
- **Dependency**: Presentation classes depend on Logic controllers
- **Composition**: Repositories contain DatabaseConnection and CacheManager
- **Aggregation**: Controllers aggregate multiple Repositories

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

