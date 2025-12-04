# MenuMap - Deliverable 3 Presentation
## Team 9
## CEN 4010 - Software Engineering
## Fall 2024

---

# Slide 1: Cover Slide

**MenuMap: Restaurant Menu Management System**

**Team 9 Members:**
- Andre Lewis - Team Lead
- Alexandra
- Alfonso
- Kamal

**Roles for Three Phases:**
- **Deliverable 1 (Requirements)**: 
  - Andre: Project coordination, SRD oversight
  - Alexandra: Requirements gathering, use case development
  - Kamal: Use cases UC-003, UC-004
  - Alfonso: Use case UC-007
- **Deliverable 2 (Design)**: 
  - Andre: Architecture design, design coordination
  - Alexandra: Design documentation, design patterns
  - Kamal: Sequence diagrams UC-003, UC-004
  - Alfonso: All UML diagrams (Use Case, Class, Sequence, State Machine)
- **Deliverable 3 (Implementation)**: 
  - Andre: Chapters 5-6, UC-001 & UC-005 test cases
  - Alexandra: Chapter 3, Chapter 7, Appendix A, UC-002 & UC-006 test cases
  - Kamal: UC-003 & UC-004 test cases
  - Alfonso: Appendix D, UC-007 test cases

**CEN 4010 - Software Engineering**
**Florida International University**
**Fall 2024**

---

# Slide 2: Purpose and Scope of System

## MenuMap System Purpose

**Primary Purpose:**
- Restaurant menu verification and management platform
- Enables restaurant owners to create and manage digital menus
- Allows customers to browse, search, and view restaurant menus

**System Scope:**
- Web-based application supporting multiple user roles
- Restaurant menu browsing and search functionality
- Menu management for restaurant owners
- User authentication and account management
- Menu verification and content accuracy

**Target Users:**
- Restaurant customers (browse menus)
- Restaurant owners (manage menus)
- System administrators (verify content)

---

# Slide 3: Updated Project Schedule

## Complete Project Timeline

**Phase 1: Requirements (Weeks 1-3)**
- Requirements gathering and documentation
- Use case development
- Deliverable 1 submission

**Phase 2: Design (Weeks 4-10)**
- Architecture design
- UML diagram creation
- Design document completion
- Deliverable 2 submission

**Phase 3: Implementation (Weeks 11-15)**
- System implementation
- Comprehensive testing (33 test cases)
- Final documentation
- Deliverable 3 submission

**Current Status:** ✅ All phases completed

---

# Slide 4: UML Use Case Diagram (Implemented Use Cases)

[Insert diagram: `MenuMap_UseCase_Diagram.PNG` or `Model_UseCase_MenuMap_UseCase_Diagram.PNG`]

**Caption:** UML Use Case Diagram showing all implemented use cases in the MenuMap system.

**Implemented Use Cases:**
- UC-001: Browse Restaurant Menus
- UC-002: Manage Favorites
- UC-003: Secure Password Reset (Security)
- UC-004: User Registration
- UC-005: User Login
- UC-006: User Logout
- UC-007: Restaurant Owner Menu Management

**Actors:**
- Customer
- Restaurant Owner
- System Administrator

---

# Slide 5: Functional Requirements - Use Case 1 (UC-001)

## UC-001: Browse Restaurant Menus

**Description:**
Customer searches for and views restaurant menus with items, descriptions, and prices.

**Main Flow:**
1. User enters restaurant name in search field
2. System displays matching restaurants
3. User selects a restaurant
4. System displays restaurant menu with items and prices
5. User can filter items by category

**Functional Requirements:**
- FR-005: System allows users to search for restaurants by name
- FR-006: System displays restaurant menus with items, descriptions, and prices
- FR-007: System supports filtering menu items by category
- FR-008: System handles cases where restaurants or menus are not found

**Non-Functional Requirements:**
- NFR-001: System response time for menu browsing shall be less than 2 seconds
- NFR-006: User interface shall be intuitive and easy to navigate
- NFR-007: System shall provide clear error messages to users

---

# Slide 6: Functional Requirements - Use Case 1 (UC-001) - Continued

## UC-001: Browse Restaurant Menus (Continued)

**Alternative Flows:**
- Restaurant not found: System displays appropriate message
- Menu not available: System indicates menu is not available
- Database error: System displays user-friendly error message

**Preconditions:**
- User is on MenuMap application
- System is accessible

**Postconditions:**
- Menu is displayed (if found)
- User can browse menu items
- User can apply filters

**Business Rules:**
- Only active restaurants are displayed
- Menu items must have valid prices
- Categories must be predefined

---

# Slide 7: Functional Requirements - Use Case 2 (UC-003) - Security Use Case

## UC-003: Secure Password Reset

**Description:**
User securely resets forgotten password through email verification process.

**Main Flow:**
1. User requests password reset
2. System validates user email
3. System generates secure reset token
4. System sends reset link to user email
5. User clicks reset link
6. System validates token
7. User enters new password
8. System validates and updates password
9. System invalidates reset token

**Functional Requirements:**
- FR-012: System allows users to request password reset
- FR-013: System validates user email before sending reset link
- FR-014: System generates secure, time-limited reset tokens
- FR-015: System validates reset tokens before allowing password change

**Non-Functional Requirements:**
- NFR-003: User passwords shall be hashed and stored securely
- NFR-004: System shall prevent SQL injection attacks
- NFR-005: System shall validate and sanitize all user inputs
- NFR-010: Reset tokens shall expire after 24 hours

---

# Slide 8: Functional Requirements - Use Case 2 (UC-003) - Continued

## UC-003: Secure Password Reset (Continued)

**Alternative Flows:**
- Invalid email: System displays generic message (security)
- Token expired: System prompts user to request new reset
- Invalid token: System denies password reset
- Weak password: System enforces password complexity requirements

**Preconditions:**
- User has registered account
- User has access to registered email

**Postconditions:**
- Password is updated (if successful)
- Reset token is invalidated
- User can log in with new password

**Security Features:**
- Secure token generation (cryptographically random)
- Time-limited tokens (24-hour expiration)
- Token single-use only
- Password complexity enforcement
- Email verification required

---

# Slide 9: Software Architecture Diagram

[Insert diagram: `Model_Static_Menu_Map_3_Tier.PNG` or `Model_Static_Model_Static_Menu_Map_3_Tier.PNG`]

**Caption:** Software Architecture Diagram showing the 3-Tier Architecture of MenuMap system.

**Architectural Style: 3-Tier Architecture**

**Tier 1: Presentation Layer (MM_Client)**
- Controllers: MenuController, UserController, RestaurantController
- Views: User interface components
- Handles HTTP requests and responses

**Tier 2: Business Logic Layer (MM_Logic)**
- Services: MenuService, UserService, RestaurantService, VerificationService
- Implements business rules and validation
- Processes data before storage or retrieval

**Tier 3: Data Layer (MM_DataStore)**
- DAOs: MenuDAO, UserDAO, RestaurantDAO
- Data Models: User, Restaurant, MenuItem, Session
- Manages database operations

**Architectural Patterns:**
- 3-Tier Architecture (Primary)
- MVC Pattern (within Presentation Tier)
- Layered Architecture

---

# Slide 10: Data Management - Part 1

## Database Design and Structure

**Database Type:** Relational Database (MySQL/PostgreSQL)

**Primary Entities:**
- **Users**: User accounts and authentication information
  - Attributes: userId, email, password (hashed), firstName, lastName, accountStatus, emailVerified
- **Restaurants**: Restaurant information and details
  - Attributes: restaurantId, name, address, phone, status, ownerUserId
- **MenuItems**: Individual menu items with descriptions and prices
  - Attributes: menuItemId, restaurantId, itemName, description, price, category, available

**Relationships:**
- Users → Restaurants (One-to-Many: Owner relationship)
- Restaurants → MenuItems (One-to-Many)
- Users → Sessions (One-to-Many)

---

# Slide 11: Data Management - Part 2

## Data Access and Persistence

**Data Access Objects (DAOs):**
- **MenuDAO**: Handles menu data operations
  - Methods: findMenuByRestaurantId(), saveMenu(), updateMenu()
- **UserDAO**: Manages user data operations
  - Methods: findUserByEmail(), saveUser(), updateUser()
- **RestaurantDAO**: Handles restaurant data operations
  - Methods: findRestaurantById(), saveRestaurant(), updateRestaurant()

**Data Integrity:**
- Foreign key constraints ensure referential integrity
- Transaction management for data consistency
- Validation at service layer before persistence

**Data Security:**
- Passwords stored as hashed values (BCrypt)
- Sensitive data encrypted in transit (HTTPS)
- Parameterized queries prevent SQL injection

---

# Slide 12: Security/Privacy - Part 1

## Access Control and Authentication

**Authentication Mechanisms:**
- Email/User ID and password authentication
- Secure password hashing using BCrypt algorithm
- Session management with secure tokens
- Password reset with time-limited tokens

**Access Control:**
- Role-based access control (RBAC)
  - Customer: Browse menus, manage favorites
  - Restaurant Owner: Manage own restaurant menus
  - Administrator: Verify menus, manage system
- Authorization checks at service layer
- Unauthorized access attempts logged

**Session Management:**
- Secure session tokens
- Session timeout after inactivity
- Session invalidation on logout
- Protection against session hijacking

---

# Slide 13: Security/Privacy - Part 2

## Data Encryption and Privacy Protection

**Data Encryption:**
- Passwords: BCrypt hashing (one-way encryption)
- Data in transit: HTTPS/TLS encryption
- Sensitive data: Encrypted at rest in database
- Reset tokens: Cryptographically secure random generation

**Privacy Protection:**
- User data access restricted to authorized users
- No information leakage in error messages
- Secure password reset process
- Email verification required for account activation

**Security Measures:**
- SQL injection prevention (parameterized queries)
- Input validation and sanitization
- XSS (Cross-Site Scripting) prevention
- CSRF (Cross-Site Request Forgery) protection
- Account lockout after multiple failed login attempts

---

# Slide 14: Minimal Class Diagram - Part 1

[Insert diagram: `Package_MM_Client_MM_Client_Class_Dia.PNG`]

**Caption:** Presentation Layer Class Diagram showing Controllers and Views.

**Presentation Layer Classes:**
- **MenuController**: Handles menu browsing requests
- **UserController**: Manages authentication and user management
- **RestaurantController**: Handles restaurant operations

**Design Patterns Identified:**
- **MVC Pattern**: Model-View-Controller separation
- **Front Controller Pattern**: Centralized request handling

---

# Slide 15: Minimal Class Diagram - Part 2

[Insert diagram: `Package_MM_Logic_MM_Logic_Class_Dia.PNG`]

**Caption:** Business Logic Layer Class Diagram showing Service classes.

**Business Logic Layer Classes:**
- **MenuService**: Menu business logic and validation
- **UserService**: User authentication and management logic
- **RestaurantService**: Restaurant management logic
- **VerificationService**: Menu verification processes

**Design Patterns Identified:**
- **Service Layer Pattern**: Encapsulates business logic
- **Strategy Pattern**: Different validation strategies

---

# Slide 16: Minimal Class Diagram - Part 3

[Insert diagram: `Package_MM_DataStore_MM_Data_Store_Dia.PNG`]

**Caption:** Data Access Layer Class Diagram showing DAOs and Data Models.

**Data Access Layer Classes:**
- **MenuDAO**: Database operations for menus
- **UserDAO**: Database operations for users
- **RestaurantDAO**: Database operations for restaurants

**Data Models:**
- **User**: User entity with authentication data
- **Restaurant**: Restaurant entity with business information
- **MenuItem**: Menu item entity with product details

**Design Patterns Identified:**
- **DAO Pattern**: Abstracts database access operations
- **Repository Pattern**: Encapsulates data access logic

---

# Slide 17: Sequence Diagram

[Insert diagram: `Interaction_Interaction4_UC-001-Browse_Restaurant_Menus_Sequence.PNG` or `UC-001-Browse_Restaurant_Menus_Sequence.PNG`]

**Caption:** Sequence Diagram for UC-001: Browse Restaurant Menus showing interaction between User, MenuController, MenuService, MenuDAO, and Database.

**Interaction Flow:**
1. User requests menu view
2. MenuController receives request
3. MenuController calls MenuService
4. MenuService applies business rules
5. MenuService calls MenuDAO
6. MenuDAO queries Database
7. Data flows back through layers
8. User receives menu display

**Lifelines:**
- User (Actor)
- MenuController (Presentation Layer)
- MenuService (Business Logic Layer)
- MenuDAO (Data Access Layer)
- Database (External System)

---

# Slide 18: Test Cases - UC-001 Sunny Day

## UC-001: Browse Restaurant Menus - Sunny Day Test Case

**Test Case ID:** SystemTest-011-UC001

**Purpose:** Verify that a user can successfully browse and view a restaurant menu.

**Test Setup:**
- Restaurant "Joe's Pizza" exists with menu items in database
- Database state initialized (see Data Model)

**Data Model (Before Test):**
| Restaurant ID | Restaurant Name | Status |
|---------------|-----------------|--------|
| 101 | Joe's Pizza | Active |

| Menu Item ID | Restaurant ID | Item Name | Price | Category |
|--------------|---------------|-----------|-------|----------|
| 1001 | 101 | Margherita Pizza | $12.99 | Entree |
| 1002 | 101 | Pepperoni Pizza | $14.99 | Entree |
| 1003 | 101 | Caesar Salad | $8.99 | Appetizer |

**Test Steps:**
1. User navigates to MenuMap application
2. User searches for "Joe's Pizza"
3. User selects "Joe's Pizza" from results
4. System displays menu with all items

**Expected Output:**
- Menu displays correctly with all items, prices, and descriptions
- All menu items visible
- Categories properly organized

**Result:** ✅ PASS

---

# Slide 19: Test Cases - UC-001 Rainy Day

## UC-001: Browse Restaurant Menus - Rainy Day Test Case

**Test Case ID:** SystemTest-013-UC001

**Purpose:** Verify system handles search for non-existent restaurant.

**Test Setup:**
- Restaurant does not exist in database
- Database state initialized (see Data Model)

**Data Model (Before Test):**
| Restaurant ID | Restaurant Name | Status |
|---------------|-----------------|--------|
| 101 | Joe's Pizza | Active |
| 102 | Burger Palace | Active |

**Test Steps:**
1. User navigates to MenuMap application
2. User searches for "NonExistent Restaurant"
3. System processes search request

**Expected Output:**
- Appropriate error message displayed: "No restaurants found matching your search"
- User-friendly message (no technical details)
- User can retry search

**Data Model (After Test):**
- No changes to database
- No data corruption

**Result:** ✅ PASS

---

# Slide 20: Test Cases - UC-003 Sunny Day

## UC-003: Secure Password Reset - Sunny Day Test Case

**Test Case ID:** SystemTest-041-UC003

**Purpose:** Verify user can successfully reset password through secure process.

**Test Setup:**
- User "johndoe" exists with verified email
- Database state initialized (see Data Model)

**Data Model (Before Test):**
| User ID | Email | Password (Hashed) | Email Verified | Account Status |
|---------|-------|-------------------|----------------|----------------|
| johndoe | johndoe@example.com | $2a$10$hashed123 | Yes | Active |

**Test Steps:**
1. User navigates to password reset page
2. User enters email: johndoe@example.com
3. System validates email and generates reset token
4. System sends reset link to email
5. User clicks reset link
6. System validates token
7. User enters new password: NewSecurePass123!
8. System validates and updates password

**Expected Output:**
- Reset link sent successfully
- Token validated correctly
- Password updated securely
- User can log in with new password

**Data Model (After Test):**
| User ID | Password (Hashed) | Reset Token |
|---------|-------------------|-------------|
| johndoe | $2a$10$newHash456 | NULL (invalidated) |

**Result:** ✅ PASS

---

# Slide 21: Test Cases - UC-003 Rainy Day

## UC-003: Secure Password Reset - Rainy Day Test Case

**Test Case ID:** SystemTest-042-UC003

**Purpose:** Verify system handles expired reset token correctly.

**Test Setup:**
- User exists with expired reset token (older than 24 hours)
- Database state initialized (see Data Model)

**Data Model (Before Test):**
| User ID | Email | Reset Token | Token Created | Token Expires |
|---------|-------|-------------|---------------|---------------|
| johndoe | johndoe@example.com | abc123token | 2024-12-01 10:00 | 2024-12-02 10:00 |
| Current Time | | | 2024-12-03 15:00 | (Token expired) |

**Test Steps:**
1. User navigates to password reset page
2. User clicks expired reset link
3. System checks token expiration
4. System detects token is expired

**Expected Output:**
- Error message: "Reset link has expired. Please request a new password reset."
- Option to request new reset link
- User cannot proceed with expired token
- Security maintained (expired tokens cannot be used)

**Data Model (After Test):**
- No password changes
- Token remains expired
- User must request new reset

**Result:** ✅ PASS

---

# Slide 22: Test Cases - UC-001 Additional Test Case

## UC-001: Browse Restaurant Menus - Additional Test Case

**Test Case ID:** SystemTest-012-UC001

**Purpose:** Verify that user can filter menu items by category.

**Test Setup:**
- Restaurant exists with menu items in multiple categories
- Database state initialized (see Data Model)

**Data Model (Before Test):**
| Menu Item ID | Restaurant ID | Item Name | Category |
|--------------|---------------|-----------|----------|
| 1001 | 101 | Margherita Pizza | Entree |
| 1002 | 101 | Pepperoni Pizza | Entree |
| 1003 | 101 | Caesar Salad | Appetizer |
| 1004 | 101 | Garlic Bread | Appetizer |

**Test Steps:**
1. User views restaurant menu
2. User selects "Appetizers" filter
3. System applies category filter

**Expected Output:**
- Only appetizer items displayed (Caesar Salad, Garlic Bread)
- Entree items hidden
- Filter works correctly

**Result:** ✅ PASS

---

# Slide 23: Test Cases - UC-003 Additional Test Case

## UC-003: Secure Password Reset - Additional Test Case

**Test Case ID:** SystemTest-043-UC003

**Purpose:** Verify system prevents password reset with invalid email.

**Test Setup:**
- Email does not exist in database
- Database state initialized (see Data Model)

**Data Model (Before Test):**
| User ID | Email |
|---------|-------|
| johndoe | johndoe@example.com |
| janedoe | janedoe@example.com |

**Test Steps:**
1. User navigates to password reset page
2. User enters non-existent email: nonexistent@example.com
3. System processes reset request

**Expected Output:**
- Generic message displayed: "If an account exists with this email, a reset link will be sent."
- No information leakage (does not reveal if email exists)
- Security maintained (prevents email enumeration)

**Data Model (After Test):**
- No reset tokens generated
- No changes to database
- Security maintained

**Result:** ✅ PASS

---

# Slide 24: Summary

## Key Achievements

✅ **Complete Implementation**
- All use cases implemented and tested
- 3-tier architecture successfully deployed
- 33 test cases with 100% pass rate

✅ **Security Features**
- Secure password reset (UC-003)
- Password hashing and encryption
- SQL injection prevention
- Access control implemented

✅ **Quality Assurance**
- Comprehensive testing (sunny day and rainy day scenarios)
- Data models validated
- Error handling verified

**System Status:** Ready for deployment

---

# Slide 25: Q&A

## Questions & Answers

**We welcome your questions about:**
- System architecture and design
- Implementation details
- Testing process and results
- Security measures
- Use case functionality
- Any other aspects of the project

**Contact Information:**
- Team Lead: Andre Lewis
- Team 9, CEN 4010
- Florida International University

**Thank you for your attention!**

---

**Presentation End**

*Prepared by Team 9 for CEN 4010 Software Engineering, Fall 2024*

**Presentation Guidelines:**
- Each slide should contain at most 10 lines
- Font size should be ≥ 22pt
- All team members must present
- Team leader starts presentation
- Rehearse before presenting!
- Total time: 30 minutes (20 min presenting + 10 min Q&A)
