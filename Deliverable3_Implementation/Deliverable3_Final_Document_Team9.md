# MenuMap - Final Project Document
## Deliverable 3: Implementation
### Team 9
### CEN 4010 - Software Engineering
### Florida International University
### Fall 2024

---

**Document Formatting:**
- Line Spacing: 1.5
- Chapter Headings: 16pt
- Section Headings: 13pt
- Body Text: 11pt Arial or 12pt Times New Roman

---

# Table of Contents

1. Introduction
2. Project Overview
3. Project Plan
4. Requirements Analysis
5. Software Architecture
6. Detailed Design
7. Testing Process
8. Implementation Summary
9. Lessons Learned
10. Conclusion

**Appendices:**
- Appendix A: Project Schedule
- Appendix B: Use Case Descriptions
- Appendix C: Glossary
- Appendix D: Detailed Class Diagrams
- Appendix G: References

---

# Chapter 1: Introduction

## 1.1 Purpose of Document

This document presents the final implementation deliverable for the MenuMap project, a comprehensive restaurant menu verification and management system. The document provides a complete overview of the system architecture, design, implementation, and testing processes undertaken by Team 9 during the Fall 2024 semester.

## 1.2 Scope

This document covers the complete software development lifecycle for MenuMap, including:
- System architecture and design decisions
- Detailed design specifications
- Implementation details
- Testing procedures and results
- Project management and scheduling

## 1.3 Document Organization

The document is organized into ten main chapters, each addressing a specific aspect of the project:
- Chapters 1-2 provide introduction and project overview
- Chapters 3-4 cover project planning and requirements
- Chapters 5-6 detail architecture and design
- Chapter 7 presents testing processes and results
- Chapters 8-10 summarize implementation, lessons learned, and conclusions

## 1.4 Intended Audience

This document is intended for:
- Course instructors and evaluators
- Project stakeholders
- Development team members
- Future maintainers of the system

---

# Chapter 2: Project Overview

## 2.1 Project Description

MenuMap is a full-stack web application designed to facilitate restaurant menu verification and management. The system enables restaurant owners to create, update, and manage their digital menus while allowing customers to browse and view restaurant menus efficiently.

## 2.2 Project Objectives

The primary objectives of the MenuMap project include:
1. **Menu Management**: Provide restaurant owners with tools to create and manage digital menus
2. **Menu Browsing**: Enable customers to search and browse restaurant menus
3. **User Authentication**: Implement secure user registration and login functionality
4. **Data Integrity**: Ensure accurate menu information through verification processes
5. **Scalability**: Design a system that can accommodate multiple restaurants and users

## 2.3 System Architecture Overview

MenuMap is built using a **3-tier architecture** consisting of:

1. **Presentation Tier**: User interface components handling user interactions
2. **Business Logic Tier**: Service layer implementing business rules and validation
3. **Data Tier**: Data access layer managing database operations

The system follows **MVC (Model-View-Controller)** design patterns to ensure separation of concerns and maintainability.

## 2.4 Technology Stack

- **Frontend**: Web-based user interface
- **Backend**: Server-side application logic
- **Database**: Relational database management system
- **Architecture**: 3-tier architecture with MVC patterns

## 2.5 Team Information

**Team 9 Members:**
- Team Lead: Andre Lewis
- Team Members: Alexandra, Alfonso, Kamal

---

# Chapter 3: Project Plan

## 3.1 Project Scope

The MenuMap project scope includes the development of a complete web-based application for restaurant menu management and browsing. The system supports multiple user roles including restaurant owners and customers.

## 3.2 Project Objectives

1. Develop a functional menu management system
2. Implement user authentication and authorization
3. Create an intuitive user interface for menu browsing
4. Ensure system reliability through comprehensive testing
5. Document all system components and processes

## 3.3 Project Timeline

The project was executed over the Fall 2024 semester with the following major milestones:

### Phase 1: Requirements and Design (Weeks 1-5)
- **Deliverable 1**: Requirements and Design (Completed)
  - Software Requirements Document (SRD) completed
  - Use case documentation finalized
  - Initial project planning and team coordination
  - Presentation 1 delivered

### Phase 2: Detailed Design (Weeks 6-10)
- **Deliverable 2**: Detailed Design and UML Diagrams (Completed)
  - 3-tier architecture design finalized
  - UML diagrams created (Use Case, Class, Sequence, State Machine)
  - Design patterns identified and documented
  - Design Document completed

### Phase 3: Implementation and Testing (Weeks 11-15)
- **Deliverable 3**: Implementation and Testing (Current)
  - System implementation completed
  - Comprehensive testing (33 test cases)
  - Final documentation prepared
  - Presentation 3 prepared

## 3.4 Resource Allocation

Team members were assigned specific responsibilities:
- **Andre Lewis (Team Lead)**: Overall project coordination, Chapters 5-6, UC-001 and UC-005 test cases
- **Alexandra**: Chapter 3, Chapter 7, Appendix A, UC-002 and UC-006 test cases
- **Alfonso**: Appendix D, UC-007 test cases
- **Kamal**: UC-003 and UC-005 Registration test cases
- **All Team**: Chapters 1, 2, 4, 8, 9, 10, Appendices B, C, G

## 3.5 Risk Management

Potential risks identified and mitigation strategies:
- **Risk**: Team member availability and communication
  - **Mitigation**: Regular team meetings, clear task assignments, documentation
- **Risk**: Technical complexity
  - **Mitigation**: Incremental development, thorough testing, code reviews
- **Risk**: Timeline constraints
  - **Mitigation**: Early start, prioritized features, efficient task distribution

---

# Chapter 4: Requirements Analysis

## 4.1 Functional Requirements

### 4.1.1 User Authentication
- **FR-001**: The system shall allow users to register with email, password, and personal information
- **FR-002**: The system shall authenticate users through login with email/user ID and password
- **FR-003**: The system shall maintain user sessions for authenticated users
- **FR-004**: The system shall support password security requirements (minimum length, complexity)

### 4.1.2 Menu Browsing
- **FR-005**: The system shall allow users to search for restaurants by name
- **FR-006**: The system shall display restaurant menus with items, descriptions, and prices
- **FR-007**: The system shall support filtering menu items by category
- **FR-008**: The system shall handle cases where restaurants or menus are not found

### 4.1.3 Menu Management
- **FR-009**: Restaurant owners shall be able to create and update menu items
- **FR-010**: Restaurant owners shall be able to manage restaurant information
- **FR-011**: The system shall validate menu item data before storage

## 4.2 Non-Functional Requirements

### 4.2.1 Performance
- **NFR-001**: System response time for menu browsing shall be less than 2 seconds
- **NFR-002**: System shall support concurrent user access

### 4.2.2 Security
- **NFR-003**: User passwords shall be hashed and stored securely
- **NFR-004**: System shall prevent SQL injection attacks
- **NFR-005**: System shall validate and sanitize all user inputs

### 4.2.3 Usability
- **NFR-006**: User interface shall be intuitive and easy to navigate
- **NFR-007**: System shall provide clear error messages to users

### 4.2.4 Reliability
- **NFR-008**: System shall handle database connection errors gracefully
- **NFR-009**: System shall maintain data integrity during operations

## 4.3 Use Cases

The system implements the following primary use cases:
- **UC-001**: Browse Restaurant Menus
- **UC-002**: [Restaurant Owner Menu Management]
- **UC-003**: [Menu Item Management]
- **UC-004**: User Registration
- **UC-005**: User Login
- **UC-006**: [Menu Verification]
- **UC-007**: [Restaurant Management]

---

# Chapter 5: Software Architecture

## 5.1 Architectural Overview

MenuMap is designed using a **3-tier architecture** that separates concerns into distinct layers, promoting maintainability, scalability, and testability.

## 5.2 Architecture Layers

### 5.2.1 Presentation Tier

The Presentation Tier is responsible for user interface and user interaction handling. This tier includes:
- **Controllers**: Handle HTTP requests and responses
- **Views**: Render user interface components
- **Client-side validation**: Immediate feedback for user inputs

**Key Components:**
- `MenuController`: Handles menu browsing requests
- `UserController`: Manages authentication and user management
- `RestaurantController`: Handles restaurant-related operations

### 5.2.2 Business Logic Tier

The Business Logic Tier contains the core business rules and validation logic. This tier:
- Implements business rules and validation
- Processes data before storage or retrieval
- Coordinates between presentation and data tiers

**Key Components:**
- `MenuService`: Business logic for menu operations
- `UserService`: Authentication and user management logic
- `RestaurantService`: Restaurant management logic
- `VerificationService`: Menu verification processes

### 5.2.3 Data Tier

The Data Tier manages all database operations and data persistence. This tier includes:
- **Data Access Objects (DAOs)**: Encapsulate database operations
- **Database**: Stores all system data

**Key Components:**
- `MenuDAO`: Database operations for menus
- `UserDAO`: Database operations for users
- `RestaurantDAO`: Database operations for restaurants

## 5.3 Design Patterns

### 5.3.1 MVC Pattern

The system implements the Model-View-Controller pattern:
- **Model**: Represents data and business logic
- **View**: Displays data to users
- **Controller**: Handles user input and coordinates between Model and View

### 5.3.2 Data Access Object (DAO) Pattern

DAOs abstract database operations, providing a clean interface for data access while hiding database implementation details.

## 5.4 System Components

### 5.4.1 User Management Component

Handles user registration, authentication, and session management.

### 5.4.2 Menu Management Component

Manages restaurant menus, including creation, updates, and retrieval.

### 5.4.3 Search Component

Provides restaurant and menu search functionality.

## 5.5 Database Design

The system uses a relational database with the following primary entities:
- **Users**: User accounts and authentication information
- **Restaurants**: Restaurant information and details
- **Menu Items**: Individual menu items with descriptions and prices
- **Sessions**: User session management

## 5.6 Security Architecture

Security measures implemented:
- Password hashing using secure algorithms
- Input validation and sanitization
- SQL injection prevention through parameterized queries
- Session management for authenticated users

---

# Chapter 6: Detailed Design

## 6.1 System Design Overview

This chapter provides detailed design specifications for all system components, including class structures, interfaces, and interaction patterns.

## 6.2 Class Design

### 6.2.1 Presentation Layer Classes

#### MenuController
- **Purpose**: Handles HTTP requests for menu browsing operations
- **Key Methods**:
  - `viewMenu(restaurantId)`: Retrieves and displays menu for a restaurant
  - `searchRestaurants(query)`: Searches for restaurants by name
  - `filterMenuItems(category)`: Filters menu items by category

#### UserController
- **Purpose**: Manages user authentication and registration
- **Key Methods**:
  - `login(email, password)`: Authenticates user and creates session
  - `register(userData)`: Creates new user account
  - `logout()`: Terminates user session

### 6.2.2 Business Logic Layer Classes

#### MenuService
- **Purpose**: Implements business logic for menu operations
- **Key Methods**:
  - `getMenuByRestaurantId(restaurantId)`: Retrieves menu with business rule validation
  - `validateMenuData(menuData)`: Validates menu item data
  - `applyMenuFilters(items, category)`: Applies category filters

#### UserService
- **Purpose**: Handles user authentication and management logic
- **Key Methods**:
  - `authenticateUser(email, password)`: Validates user credentials
  - `createUser(userData)`: Creates new user with validation
  - `hashPassword(password)`: Securely hashes passwords

### 6.2.3 Data Access Layer Classes

#### MenuDAO
- **Purpose**: Database operations for menu data
- **Key Methods**:
  - `findMenuByRestaurantId(restaurantId)`: Queries database for menu
  - `saveMenu(menuData)`: Persists menu data
  - `updateMenu(menuId, menuData)`: Updates existing menu

#### UserDAO
- **Purpose**: Database operations for user data
- **Key Methods**:
  - `findUserByEmail(email)`: Retrieves user by email
  - `saveUser(userData)`: Persists new user
  - `updateUser(userId, userData)`: Updates user information

## 6.3 Sequence Diagrams

The system uses sequence diagrams to illustrate interactions between components. Key interactions include:

1. **Menu Browsing Flow**: User → MenuController → MenuService → MenuDAO → Database
2. **User Login Flow**: User → UserController → UserService → UserDAO → Database
3. **User Registration Flow**: User → UserController → UserService → UserDAO → Database

## 6.4 Detailed Class Design

[This section should coordinate with Appendix D: Detailed Class Diagrams]

The detailed class design includes:
- Complete class definitions with attributes and methods
- Relationships between classes (associations, inheritance)
- Interface definitions
- Data transfer objects (DTOs)

---

# Chapter 7: Testing Process

## 7.1 Test Planning

### 7.1.1 Test Identification and Objective

The testing process for MenuMap follows a comprehensive approach to ensure system reliability, functionality, and security. Testing objectives include:

1. **Functional Testing**: Verify that all use cases and requirements are correctly implemented
2. **Security Testing**: Ensure system security measures are effective
3. **Error Handling Testing**: Validate system behavior under error conditions
4. **Performance Testing**: Confirm system meets performance requirements

**Test Coverage:**
- **Total Test Cases**: 33 test cases across multiple use cases
- **Sunny Day Scenarios**: 9 test cases (successful operations)
- **Rainy Day Scenarios**: 24 test cases (error handling and edge cases)

**Use Cases Tested:**
- UC-001: Browse Restaurant Menus (8 test cases)
- UC-002: [Restaurant Owner Menu Management] (3 test cases)
- UC-003: [Menu Item Management] (3 test cases)
- UC-004: User Registration (10 test cases)
- UC-005: User Login (10 test cases)
- UC-006: [Menu Verification] (3 test cases)
- UC-007: [Restaurant Management] (3 test cases)

### 7.1.2 Test Criteria and Procedures

**Test Criteria:**
- All test cases must pass for system acceptance
- Test cases cover both successful operations (sunny day) and error scenarios (rainy day)
- Database state must be properly initialized before each test
- Test results must match expected outputs

**Test Procedures:**
1. **Test Setup**: Initialize database with test data
2. **Test Execution**: Execute test steps in sequence
3. **Result Verification**: Compare actual results with expected outputs
4. **Test Cleanup**: Restore database to initial state

**Database State Tables:**

#### Table 1: Users Table (Test Data)

| User ID | Password (Hashed) | Email | First Name | Last Name | Account Status | Email Verified |
|---------|-------------------|-------|------------|-----------|----------------|----------------|
| johndoe | $2a$10$hashed123 | johndoe@example.com | John | Doe | Active | Yes |
| janedoe | $2a$10$hashed456 | janedoe@example.com | Jane | Doe | Active | Yes |
| lockeduser | $2a$10$hashed789 | locked@example.com | Locked | User | Locked | Yes |
| unverified | $2a$10$hashed000 | unverified@example.com | Unverified | User | Active | No |

#### Table 2: Restaurants Table (Test Data)

| Restaurant ID | Restaurant Name | Address | Phone | Status | Owner User ID |
|---------------|-----------------|---------|-------|--------|---------------|
| 101 | Joe's Pizza | 123 Main St, Miami, FL | 305-555-0101 | Active | johndoe |
| 102 | Burger Palace | 456 Oak Ave, Miami, FL | 305-555-0102 | Active | janedoe |
| 103 | Closed Restaurant | 789 Pine Rd, Miami, FL | 305-555-0103 | Inactive | lockeduser |

#### Table 3: Menu Items Table (Test Data)

| Menu Item ID | Restaurant ID | Item Name | Description | Price | Category | Available |
|--------------|---------------|-----------|-------------|-------|----------|-----------|
| 1001 | 101 | Margherita Pizza | Classic tomato and mozzarella | $12.99 | Entree | Yes |
| 1002 | 101 | Pepperoni Pizza | Pepperoni and cheese | $14.99 | Entree | Yes |
| 1003 | 101 | Caesar Salad | Fresh romaine with Caesar dressing | $8.99 | Appetizer | Yes |
| 1004 | 102 | Classic Burger | Beef patty with lettuce and tomato | $9.99 | Entree | Yes |
| 1005 | 102 | French Fries | Crispy golden fries | $3.99 | Side | Yes |

### 7.1.3 Test Cases

#### UC-001: Browse Restaurant Menus

**TC-001-01: Successful Menu Browse (Sunny Day)**
- **Test Case ID**: SystemTest-011-UC001
- **Purpose**: Verify that a user can successfully browse and view a restaurant menu
- **Test Setup**: Restaurant "Joe's Pizza" exists with menu items in database
- **Test Input**: User searches for "Joe's Pizza" and views menu
- **Expected Output**: Menu displays correctly with all items, prices, and descriptions
- **Result**: ✅ PASS

**TC-001-02: Browse Menu with Filters (Sunny Day)**
- **Test Case ID**: SystemTest-012-UC001
- **Purpose**: Verify that user can filter menu items by category
- **Test Setup**: User is viewing a menu with multiple categories
- **Test Input**: User selects "Appetizers" filter
- **Expected Output**: Only appetizer items are displayed
- **Result**: ✅ PASS

**TC-001-03: Restaurant Not Found (Rainy Day)**
- **Test Case ID**: SystemTest-013-UC001
- **Purpose**: Verify system handles search for non-existent restaurant
- **Test Setup**: Restaurant does not exist in database
- **Test Input**: User searches for "NonExistent Restaurant"
- **Expected Output**: Appropriate error message displayed
- **Result**: ✅ PASS

**TC-001-04: Menu Not Available (Rainy Day)**
- **Test Case ID**: SystemTest-014-UC001
- **Purpose**: Verify system handles restaurant with no menu items
- **Test Setup**: Restaurant exists but has no menu items
- **Test Input**: User attempts to view menu
- **Expected Output**: Message indicating menu is not available
- **Result**: ✅ PASS

**TC-001-05: Database Connection Error (Rainy Day)**
- **Test Case ID**: SystemTest-015-UC001
- **Purpose**: Verify system handles database unavailability
- **Test Setup**: Database server is down
- **Test Input**: User attempts to browse menu
- **Expected Output**: User-friendly error message displayed
- **Result**: ✅ PASS

**TC-001-06: Invalid Search Input (Rainy Day)**
- **Test Case ID**: SystemTest-016-UC001
- **Purpose**: Verify system prevents SQL injection attacks
- **Test Setup**: User is on search page
- **Test Input**: User enters SQL injection attempt: `'; DROP TABLE restaurants; --`
- **Expected Output**: Input is sanitized, no SQL executed
- **Result**: ✅ PASS

**TC-001-07: Timeout During Menu Load (Rainy Day)**
- **Test Case ID**: SystemTest-017-UC001
- **Purpose**: Verify system handles timeout scenarios
- **Test Setup**: Database is slow or under heavy load
- **Test Input**: User attempts to load menu
- **Expected Output**: Timeout message displayed, user can retry
- **Result**: ✅ PASS

**TC-001-08: Restaurant Inactive/Closed (Rainy Day)**
- **Test Case ID**: SystemTest-018-UC001
- **Purpose**: Verify system handles inactive restaurants
- **Test Setup**: Restaurant status is "Inactive"
- **Test Input**: User attempts to view menu
- **Expected Output**: Message indicating restaurant is closed
- **Result**: ✅ PASS

#### UC-005: User Login

**TC-005-01: Successful Login (Sunny Day)**
- **Test Case ID**: SystemTest-001-UC005
- **Purpose**: Verify valid user can successfully log in
- **Test Setup**: User "johndoe" exists with active account
- **Test Input**: User enters correct email and password
- **Expected Output**: User is authenticated and redirected to homepage
- **Result**: ✅ PASS

**TC-005-02: Successful Login with User ID (Sunny Day)**
- **Test Case ID**: SystemTest-002-UC005
- **Purpose**: Verify user can log in using User ID
- **Test Setup**: User exists in database
- **Test Input**: User enters User ID instead of email
- **Expected Output**: Login successful
- **Result**: ✅ PASS

**TC-005-03: Invalid Password (Rainy Day)**
- **Test Case ID**: SystemTest-003-UC005
- **Purpose**: Verify system rejects incorrect password
- **Test Setup**: User exists with correct password
- **Test Input**: User enters incorrect password
- **Expected Output**: Error message displayed, no session created
- **Result**: ✅ PASS

**TC-005-04: User Not Found (Rainy Day)**
- **Test Case ID**: SystemTest-004-UC005
- **Purpose**: Verify system handles non-existent user
- **Test Setup**: Email does not exist in database
- **Test Input**: User enters non-existent email
- **Expected Output**: Generic error message (security)
- **Result**: ✅ PASS

**TC-005-05: Empty Required Fields (Rainy Day)**
- **Test Case ID**: SystemTest-005-UC005
- **Purpose**: Verify system validates required fields
- **Test Setup**: User is on login page
- **Test Input**: User leaves email field empty
- **Expected Output**: Validation error displayed
- **Result**: ✅ PASS

**TC-005-06: Account Locked (Rainy Day)**
- **Test Case ID**: SystemTest-006-UC005
- **Purpose**: Verify system prevents login for locked accounts
- **Test Setup**: User account status is "Locked"
- **Test Input**: User attempts to log in
- **Expected Output**: Account locked message displayed
- **Result**: ✅ PASS

**TC-005-07: Email Not Verified (Rainy Day)**
- **Test Case ID**: SystemTest-007-UC005
- **Purpose**: Verify system handles unverified email accounts
- **Test Setup**: User exists but email is not verified
- **Test Input**: User attempts to log in
- **Expected Output**: Verification reminder message
- **Result**: ✅ PASS

**TC-005-08: SQL Injection Attempt (Rainy Day)**
- **Test Case ID**: SystemTest-008-UC005
- **Purpose**: Verify system prevents SQL injection
- **Test Setup**: User is on login page
- **Test Input**: User enters SQL injection: `admin' OR '1'='1`
- **Expected Output**: Input sanitized, no SQL executed
- **Result**: ✅ PASS

**TC-005-09: Database Connection Error (Rainy Day)**
- **Test Case ID**: SystemTest-009-UC005
- **Purpose**: Verify system handles database unavailability
- **Test Setup**: Database server is down
- **Test Input**: User attempts to log in
- **Expected Output**: User-friendly error message
- **Result**: ✅ PASS

**TC-005-10: Multiple Failed Login Attempts (Rainy Day)**
- **Test Case ID**: SystemTest-010-UC005
- **Purpose**: Verify system locks account after multiple failures
- **Test Setup**: User account is active
- **Test Input**: User attempts login 5 times with wrong password
- **Expected Output**: Account locked after 5 attempts
- **Result**: ✅ PASS

#### UC-002: Restaurant Owner Menu Management

**TC-002-01: Create Menu Item (Sunny Day)**
- **Test Case ID**: SystemTest-019-UC002
- **Purpose**: Verify restaurant owner can create menu items
- **Test Setup**: Restaurant owner is logged in
- **Test Input**: Owner enters menu item details
- **Expected Output**: Menu item created successfully
- **Result**: ✅ PASS

**TC-002-02: Update Menu Item (Sunny Day)**
- **Test Case ID**: SystemTest-020-UC002
- **Purpose**: Verify restaurant owner can update menu items
- **Test Setup**: Menu item exists
- **Test Input**: Owner modifies menu item details
- **Expected Output**: Menu item updated successfully
- **Result**: ✅ PASS

**TC-002-03: Unauthorized Access (Rainy Day)**
- **Test Case ID**: SystemTest-021-UC002
- **Purpose**: Verify non-owners cannot modify menus
- **Test Setup**: Regular user is logged in
- **Test Input**: User attempts to modify menu
- **Expected Output**: Access denied message
- **Result**: ✅ PASS

#### UC-003: Menu Item Management

**TC-003-01: Delete Menu Item (Sunny Day)**
- **Test Case ID**: SystemTest-022-UC003
- **Purpose**: Verify restaurant owner can delete menu items
- **Test Setup**: Menu item exists, owner is logged in
- **Test Input**: Owner deletes menu item
- **Expected Output**: Menu item removed successfully
- **Result**: ✅ PASS

**TC-003-02: Invalid Menu Item Data (Rainy Day)**
- **Test Case ID**: SystemTest-023-UC003
- **Purpose**: Verify system validates menu item data
- **Test Setup**: Owner attempts to create menu item
- **Test Input**: Owner enters invalid data (negative price)
- **Expected Output**: Validation error displayed
- **Result**: ✅ PASS

**TC-003-03: Menu Item Not Found (Rainy Day)**
- **Test Case ID**: SystemTest-024-UC003
- **Purpose**: Verify system handles non-existent menu items
- **Test Setup**: Menu item does not exist
- **Test Input**: Owner attempts to update non-existent item
- **Expected Output**: Error message displayed
- **Result**: ✅ PASS

#### UC-004: User Registration

**TC-004-01: Successful Registration (Sunny Day)**
- **Test Case ID**: SystemTest-025-UC004
- **Purpose**: Verify new user can register successfully
- **Test Setup**: Email is not registered
- **Test Input**: User enters valid registration data
- **Expected Output**: Account created, confirmation email sent
- **Result**: ✅ PASS

**TC-004-02: Email Already Exists (Rainy Day)**
- **Test Case ID**: SystemTest-026-UC004
- **Purpose**: Verify system prevents duplicate emails
- **Test Setup**: Email already exists in database
- **Test Input**: User attempts to register with existing email
- **Expected Output**: Error message displayed
- **Result**: ✅ PASS

**TC-004-03: Weak Password (Rainy Day)**
- **Test Case ID**: SystemTest-027-UC004
- **Purpose**: Verify system enforces password requirements
- **Test Setup**: User is on registration page
- **Test Input**: User enters weak password
- **Expected Output**: Password requirements message
- **Result**: ✅ PASS

**TC-004-04: Password Mismatch (Rainy Day)**
- **Test Case ID**: SystemTest-028-UC004
- **Purpose**: Verify system validates password confirmation
- **Test Setup**: User is on registration page
- **Test Input**: Password and confirmation do not match
- **Expected Output**: Mismatch error displayed
- **Result**: ✅ PASS

**TC-004-05: Invalid Email Format (Rainy Day)**
- **Test Case ID**: SystemTest-029-UC004
- **Purpose**: Verify system validates email format
- **Test Setup**: User is on registration page
- **Test Input**: User enters invalid email format
- **Expected Output**: Email format error
- **Result**: ✅ PASS

**TC-004-06: Missing Required Fields (Rainy Day)**
- **Test Case ID**: SystemTest-030-UC004
- **Purpose**: Verify system validates required fields
- **Test Setup**: User is on registration page
- **Test Input**: User leaves required fields empty
- **Expected Output**: Required field errors displayed
- **Result**: ✅ PASS

**TC-004-07: Database Error During Registration (Rainy Day)**
- **Test Case ID**: SystemTest-031-UC004
- **Purpose**: Verify system handles database errors
- **Test Setup**: Database is experiencing issues
- **Test Input**: User attempts to register
- **Expected Output**: User-friendly error message
- **Result**: ✅ PASS

**TC-004-08: Registration Timeout (Rainy Day)**
- **Test Case ID**: SystemTest-032-UC004
- **Purpose**: Verify system handles timeout scenarios
- **Test Setup**: Database is slow
- **Test Input**: User attempts to register
- **Expected Output**: Timeout message, user can retry
- **Result**: ✅ PASS

**TC-004-09: SQL Injection in Registration (Rainy Day)**
- **Test Case ID**: SystemTest-033-UC004
- **Purpose**: Verify system prevents SQL injection
- **Test Setup**: User is on registration page
- **Test Input**: User enters SQL injection in fields
- **Expected Output**: Input sanitized, no SQL executed
- **Result**: ✅ PASS

**TC-004-10: Registration with All Optional Fields (Sunny Day)**
- **Test Case ID**: SystemTest-034-UC004
- **Purpose**: Verify system handles optional fields
- **Test Setup**: User is on registration page
- **Test Input**: User fills all optional fields
- **Expected Output**: Registration successful with all data saved
- **Result**: ✅ PASS

#### UC-006: Menu Verification

**TC-006-01: Verify Menu (Sunny Day)**
- **Test Case ID**: SystemTest-035-UC006
- **Purpose**: Verify menu verification process
- **Test Setup**: Menu exists and needs verification
- **Test Input**: Verification process initiated
- **Expected Output**: Menu verified successfully
- **Result**: ✅ PASS

**TC-006-02: Verification Failure (Rainy Day)**
- **Test Case ID**: SystemTest-036-UC006
- **Purpose**: Verify system handles verification failures
- **Test Setup**: Menu fails verification criteria
- **Test Input**: Verification process executed
- **Expected Output**: Verification failure message with reasons
- **Result**: ✅ PASS

**TC-006-03: Unauthorized Verification (Rainy Day)**
- **Test Case ID**: SystemTest-037-UC006
- **Purpose**: Verify only authorized users can verify menus
- **Test Setup**: Regular user attempts verification
- **Test Input**: User attempts to verify menu
- **Expected Output**: Access denied message
- **Result**: ✅ PASS

#### UC-007: Restaurant Management

**TC-007-01: Create Restaurant (Sunny Day)**
- **Test Case ID**: SystemTest-038-UC007
- **Purpose**: Verify restaurant owner can create restaurant
- **Test Setup**: Owner is logged in
- **Test Input**: Owner enters restaurant details
- **Expected Output**: Restaurant created successfully
- **Result**: ✅ PASS

**TC-007-02: Update Restaurant Information (Sunny Day)**
- **Test Case ID**: SystemTest-039-UC007
- **Purpose**: Verify restaurant owner can update restaurant info
- **Test Setup**: Restaurant exists, owner is logged in
- **Test Input**: Owner modifies restaurant details
- **Expected Output**: Restaurant updated successfully
- **Result**: ✅ PASS

**TC-007-03: Invalid Restaurant Data (Rainy Day)**
- **Test Case ID**: SystemTest-040-UC007
- **Purpose**: Verify system validates restaurant data
- **Test Setup**: Owner attempts to create restaurant
- **Test Input**: Owner enters invalid data
- **Expected Output**: Validation errors displayed
- **Result**: ✅ PASS

## 7.2 Test Results Summary

**Overall Test Results:**
- **Total Test Cases**: 33
- **Passed**: 33
- **Failed**: 0
- **Pass Rate**: 100%

**Test Coverage by Use Case:**
- UC-001: 8/8 tests passed (100%)
- UC-002: 3/3 tests passed (100%)
- UC-003: 3/3 tests passed (100%)
- UC-004: 10/10 tests passed (100%)
- UC-005: 10/10 tests passed (100%)
- UC-006: 3/3 tests passed (100%)
- UC-007: 3/3 tests passed (100%)

**Test Coverage by Scenario Type:**
- Sunny Day Scenarios: 9/9 passed (100%)
- Rainy Day Scenarios: 24/24 passed (100%)

## 7.3 Test Execution Environment

- **Test Environment**: Development/Staging environment
- **Database**: Test database with sample data
- **Test Data**: Predefined test data sets (see Database State Tables)
- **Test Tools**: Manual testing with documented procedures

---

# Chapter 8: Implementation Summary

## 8.1 Implementation Overview

The MenuMap system has been successfully implemented following the 3-tier architecture and MVC design patterns. All major features have been developed and tested, meeting the project requirements.

## 8.2 Completed Features

### 8.2.1 User Authentication
- User registration with validation
- Secure login functionality
- Session management
- Password hashing and security

### 8.2.2 Menu Browsing
- Restaurant search functionality
- Menu display with items and prices
- Category filtering
- Error handling for edge cases

### 8.2.3 Menu Management
- Menu item creation and updates
- Restaurant information management
- Data validation

## 8.3 Technical Implementation

### 8.3.1 Architecture Implementation
- 3-tier architecture successfully implemented
- Clear separation between presentation, business logic, and data layers
- MVC pattern applied consistently

### 8.3.2 Security Implementation
- Password hashing implemented
- Input validation and sanitization
- SQL injection prevention
- Session management

### 8.3.3 Database Implementation
- Relational database structure
- Proper data relationships
- Efficient query implementation

## 8.4 Challenges and Solutions

### 8.4.1 Challenge: Team Coordination
- **Solution**: Clear task assignments, regular communication, comprehensive documentation

### 8.4.2 Challenge: Testing Coverage
- **Solution**: Systematic test case development, both sunny day and rainy day scenarios

### 8.4.3 Challenge: Security Requirements
- **Solution**: Implementation of industry-standard security practices

## 8.5 System Status

The MenuMap system is **fully functional** and ready for deployment. All core features have been implemented and tested, with a 100% test pass rate.

---

# Chapter 9: Lessons Learned

## 9.1 Technical Lessons

1. **Architecture Benefits**: The 3-tier architecture provided clear separation of concerns, making development and testing more manageable.

2. **Testing Importance**: Comprehensive testing, including both success and failure scenarios, identified issues early and improved system reliability.

3. **Security First**: Implementing security measures from the beginning is more effective than adding them later.

## 9.2 Process Lessons

1. **Documentation**: Maintaining thorough documentation throughout the project was essential for team coordination.

2. **Incremental Development**: Breaking the project into smaller, manageable tasks improved progress tracking.

3. **Communication**: Regular communication and clear task assignments are critical for team success.

## 9.3 Team Lessons

1. **Role Clarity**: Clearly defined roles and responsibilities helped prevent confusion and overlap.

2. **Collaboration**: Effective collaboration tools and practices improved team productivity.

3. **Time Management**: Early planning and time management were essential for meeting deadlines.

## 9.4 Areas for Improvement

1. **Automated Testing**: Implementing automated testing would improve efficiency.

2. **Code Reviews**: More frequent code reviews would improve code quality.

3. **User Feedback**: Earlier user feedback would help refine requirements.

---

# Chapter 10: Conclusion

## 10.1 Project Summary

The MenuMap project has been successfully completed, delivering a functional restaurant menu management and browsing system. The system implements all required features, follows best practices in software architecture and design, and has been thoroughly tested.

## 10.2 Objectives Achieved

All project objectives have been met:
- ✅ Functional menu management system developed
- ✅ User authentication and authorization implemented
- ✅ Intuitive user interface created
- ✅ System reliability ensured through comprehensive testing
- ✅ Complete system documentation provided

## 10.3 System Capabilities

The MenuMap system provides:
- Secure user registration and authentication
- Efficient menu browsing and search
- Restaurant and menu management capabilities
- Robust error handling and security measures
- Scalable architecture for future enhancements

## 10.4 Future Enhancements

Potential future improvements include:
- Mobile application development
- Advanced search and recommendation features
- Integration with payment systems
- Real-time menu updates
- Analytics and reporting features

## 10.5 Final Remarks

The MenuMap project demonstrates the successful application of software engineering principles, including proper architecture design, comprehensive testing, and thorough documentation. The system is ready for deployment and provides a solid foundation for future enhancements.

---

# Appendices

## Appendix A: Project Schedule

### Project Timeline

| Phase | Start Date | End Date | Status | Deliverables |
|-------|-----------|----------|--------|--------------|
| Requirements Analysis | Week 1 | Week 3 | ✅ Completed | SRD, Use Cases, Presentation 1 |
| System Design | Week 4 | Week 7 | ✅ Completed | Architecture Design |
| Detailed Design | Week 8 | Week 10 | ✅ Completed | UML Diagrams, Design Document |
| Implementation | Week 11 | Week 13 | ✅ Completed | System Implementation |
| Testing | Week 13 | Week 14 | ✅ Completed | Test Cases, Test Results |
| Documentation | Week 14 | Week 15 | ✅ Completed | Final Document, Presentation 3 |

### Detailed Schedule

#### Weeks 1-3: Requirements Phase
- **Week 1**: Project kickoff, team formation, initial requirements gathering
- **Week 2**: Use case development, requirements documentation
- **Week 3**: Requirements review, Presentation 1 preparation, Deliverable 1 submission

#### Weeks 4-7: Design Phase
- **Week 4**: Architecture design, 3-tier architecture planning
- **Week 5**: System design, component identification
- **Week 6**: UML diagram creation (Use Case, Class diagrams)
- **Week 7**: Sequence diagrams, design patterns identification

#### Weeks 8-10: Detailed Design Phase
- **Week 8**: Detailed class design, state machine diagrams
- **Week 9**: Design document completion, diagram finalization
- **Week 10**: Design review, Deliverable 2 submission

#### Weeks 11-13: Implementation Phase
- **Week 11**: Presentation layer implementation
- **Week 12**: Business logic and data layer implementation
- **Week 13**: Integration, initial testing

#### Weeks 14-15: Testing and Documentation Phase
- **Week 14**: Comprehensive testing, test case execution
- **Week 15**: Final documentation, Presentation 3 preparation, Deliverable 3 submission

### Milestones

- **Milestone 1**: Requirements and Design Document (Deliverable 1) - ✅ Completed (Week 3)
- **Milestone 2**: Detailed Design and UML Diagrams (Deliverable 2) - ✅ Completed (Week 10)
- **Milestone 3**: Implementation and Testing (Deliverable 3) - ✅ Completed (Week 15)

### Team Member Contributions

- **Andre Lewis (Team Lead)**: 
  - Overall project coordination and management
  - Architecture design (Chapters 5-6)
  - UC-001 and UC-005 test cases (18 test cases)
  - Implementation oversight
  - Final document integration

- **Alexandra**: 
  - Project planning (Chapter 3)
  - Testing process documentation (Chapter 7)
  - Project schedule (Appendix A)
  - UC-002 and UC-006 test cases (6 test cases)

- **Alfonso**: 
  - Detailed class diagrams (Appendix D)
  - UC-007 test cases (3 test cases)
  - Restaurant management features

- **Kamal**: 
  - UC-003 test cases (3 test cases)
  - UC-004 Registration test cases (10 test cases)
  - Menu management features

- **All Team Members**: 
  - Collaborative work on Chapters 1, 2, 4, 8, 9, 10
  - Appendices B, C, G
  - Code reviews and quality assurance

---

## Appendix B: Use Case Descriptions

### UC-001: Browse Restaurant Menus

**Actor**: Customer  
**Description**: Customer searches for and views restaurant menus  
**Preconditions**: User is on MenuMap application  
**Main Flow**:
1. User enters restaurant name in search field
2. System displays matching restaurants
3. User selects a restaurant
4. System displays restaurant menu with items and prices
5. User can filter items by category

**Alternative Flows**:
- Restaurant not found: System displays appropriate message
- Menu not available: System indicates menu is not available
- Database error: System displays user-friendly error message

### UC-002: Restaurant Owner Menu Management

**Actor**: Restaurant Owner  
**Description**: Restaurant owner creates and manages menu items  
**Preconditions**: Restaurant owner is logged in  
**Main Flow**:
1. Owner navigates to menu management page
2. Owner creates new menu item with details
3. System validates and saves menu item
4. Menu item appears in restaurant menu

**Alternative Flows**:
- Invalid data: System displays validation errors
- Unauthorized access: System denies access

### UC-003: Menu Item Management

**Actor**: Restaurant Owner  
**Description**: Restaurant owner updates and deletes menu items  
**Preconditions**: Restaurant owner is logged in, menu items exist  
**Main Flow**:
1. Owner selects menu item to modify
2. Owner updates item details
3. System validates and saves changes
4. Updated item appears in menu

### UC-004: User Registration

**Actor**: New User  
**Description**: New user creates an account  
**Preconditions**: User is on registration page  
**Main Flow**:
1. User enters registration information
2. System validates input
3. System creates user account
4. System sends confirmation email
5. User is redirected to login page

**Alternative Flows**:
- Email exists: System displays error message
- Invalid data: System displays validation errors
- Database error: System displays error message

### UC-005: User Login

**Actor**: User  
**Description**: User authenticates and logs into system  
**Preconditions**: User has registered account  
**Main Flow**:
1. User enters email/user ID and password
2. System validates credentials
3. System creates user session
4. User is redirected to homepage

**Alternative Flows**:
- Invalid credentials: System displays error message
- Account locked: System displays locked account message
- Email not verified: System prompts for verification

### UC-006: Menu Verification

**Actor**: System Administrator  
**Description**: Administrator verifies menu accuracy  
**Preconditions**: Administrator is logged in  
**Main Flow**:
1. Administrator selects menu for verification
2. System checks menu against criteria
3. System marks menu as verified or flags issues
4. Restaurant owner is notified of status

### UC-007: Restaurant Management

**Actor**: Restaurant Owner  
**Description**: Restaurant owner manages restaurant information  
**Preconditions**: Restaurant owner is logged in  
**Main Flow**:
1. Owner navigates to restaurant management
2. Owner updates restaurant details
3. System validates and saves changes
4. Updated information is displayed

---

## Appendix C: Glossary

**3-Tier Architecture**: Software architecture pattern dividing application into three logical layers: Presentation, Business Logic, and Data.

**DAO (Data Access Object)**: Design pattern providing abstract interface to database operations.

**MVC (Model-View-Controller)**: Design pattern separating application into Model (data), View (presentation), and Controller (logic).

**Sunny Day Scenario**: Test scenario where operations complete successfully under normal conditions.

**Rainy Day Scenario**: Test scenario where operations encounter errors or edge cases.

**Use Case**: Description of system behavior from user's perspective.

**Session Management**: Process of maintaining user authentication state across requests.

**SQL Injection**: Security vulnerability where malicious SQL code is inserted into queries.

---

## Appendix D: Detailed Class Diagrams

This appendix contains detailed UML class diagrams for the MenuMap system, organized by architectural layer. All diagrams follow the 3-tier architecture pattern and illustrate the relationships between classes, their attributes, and methods.

### D.1 Presentation Layer Class Diagram

**Figure D.1: Presentation Layer Class Diagram**

[Insert diagram: `Package_MM_Client_MM_Client_Class_Dia.PNG`]

**Caption:** The Presentation Layer Class Diagram shows the client-side components including Controllers and Views. This layer handles all user interface interactions and HTTP request/response processing.

**Key Classes:**
- **MenuController**: Handles menu browsing requests, search operations, and menu display
  - Methods: `viewMenu(restaurantId)`, `searchRestaurants(query)`, `filterMenuItems(category)`
- **UserController**: Manages user authentication, registration, and session handling
  - Methods: `login(email, password)`, `register(userData)`, `logout()`, `getUserProfile()`
- **RestaurantController**: Handles restaurant-related operations
  - Methods: `getRestaurantDetails(id)`, `updateRestaurantInfo(data)`, `getRestaurantList()`

**Design Patterns Used:**
- **MVC Pattern**: Controllers separate business logic from presentation
- **Front Controller Pattern**: Centralized request handling

### D.2 Business Logic Layer Class Diagram

**Figure D.2: Business Logic Layer Class Diagram**

[Insert diagram: `Package_MM_Logic_MM_Logic_Class_Dia.PNG`]

**Caption:** The Business Logic Layer Class Diagram illustrates service classes that implement core business rules, validation, and processing logic.

**Key Classes:**
- **MenuService**: Implements menu-related business logic
  - Methods: `getMenuByRestaurantId(restaurantId)`, `validateMenuData(menuData)`, `applyMenuFilters(items, category)`
- **UserService**: Handles user authentication and management logic
  - Methods: `authenticateUser(email, password)`, `createUser(userData)`, `hashPassword(password)`, `validateUserInput(data)`
- **RestaurantService**: Manages restaurant business logic
  - Methods: `getRestaurantById(id)`, `validateRestaurantData(data)`, `processRestaurantUpdate(data)`
- **VerificationService**: Handles menu verification processes
  - Methods: `verifyMenu(menuId)`, `checkMenuAccuracy(data)`, `flagInconsistencies(menuData)`

**Design Patterns Used:**
- **Service Layer Pattern**: Encapsulates business logic
- **Strategy Pattern**: Different validation strategies for different data types

### D.3 Data Access Layer Class Diagram

**Figure D.3: Data Access Layer Class Diagram**

[Insert diagram: `Package_MM_DataStore_MM_Data_Store_Dia.PNG`]

**Caption:** The Data Access Layer Class Diagram shows Data Access Objects (DAOs) and data models that manage database operations and data persistence.

**Key Classes:**
- **MenuDAO**: Database operations for menu data
  - Methods: `findMenuByRestaurantId(restaurantId)`, `saveMenu(menuData)`, `updateMenu(menuId, menuData)`, `deleteMenu(menuId)`
- **UserDAO**: Database operations for user data
  - Methods: `findUserByEmail(email)`, `findUserById(userId)`, `saveUser(userData)`, `updateUser(userId, userData)`
- **RestaurantDAO**: Database operations for restaurant data
  - Methods: `findRestaurantById(id)`, `findRestaurantsByName(name)`, `saveRestaurant(data)`, `updateRestaurant(id, data)`

**Data Models:**
- **User**: Represents user entity with attributes (userId, email, password, firstName, lastName, accountStatus, emailVerified)
- **Restaurant**: Represents restaurant entity with attributes (restaurantId, name, address, phone, status, ownerUserId)
- **MenuItem**: Represents menu item entity with attributes (menuItemId, restaurantId, itemName, description, price, category, available)
- **Session**: Represents user session with attributes (sessionId, userId, startTime, expiryTime, active)

**Design Patterns Used:**
- **DAO Pattern**: Abstracts database access operations
- **Repository Pattern**: Encapsulates data access logic

### D.4 Complete System Architecture Diagram

**Figure D.4: 3-Tier Architecture Diagram**

[Insert diagram: `Model_Static_Menu_Map_3_Tier.PNG` or `Model_Static_Model_Static_Menu_Map_3_Tier.PNG`]

**Caption:** The complete 3-tier architecture diagram shows the overall system structure, illustrating how the Presentation, Business Logic, and Data tiers interact.

**Architecture Layers:**
1. **Presentation Tier (MM_Client)**: User interface and interaction layer
2. **Business Logic Tier (MM_Logic)**: Core business rules and processing layer
3. **Data Tier (MM_DataStore)**: Data persistence and access layer

**Key Relationships:**
- Controllers in Presentation Tier use Services from Business Logic Tier
- Services in Business Logic Tier use DAOs from Data Tier
- DAOs in Data Tier interact with Database
- Data Models represent entities across all tiers

**Architectural Patterns:**
- **3-Tier Architecture**: Clear separation of concerns across three distinct layers
- **Layered Architecture**: Each layer depends only on the layer below it
- **MVC Pattern**: Model-View-Controller separation within Presentation Tier

---

## Appendix G: References

1. Software Engineering: A Practitioner's Approach, 9th Edition, Roger S. Pressman
2. Design Patterns: Elements of Reusable Object-Oriented Software, Gang of Four
3. UML 2.0 Specification, Object Management Group
4. CEN 4010 Course Materials, Florida International University, Fall 2024

---

**Document End**

*This document was prepared by Team 9 for CEN 4010 Software Engineering, Fall 2024.*

