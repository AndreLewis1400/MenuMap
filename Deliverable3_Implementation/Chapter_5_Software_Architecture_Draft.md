# Chapter 5: Software Architecture
## MenuMap Final Systems Document

**Author:** Andre Lewis (Team Lead) 
**Date:** December 2024 
**Status:** Final - Ready for Document Integration

---

## Introduction

This chapter describes the software architecture of the MenuMap system. The architecture is designed to support a scalable, maintainable, and secure platform for restaurant menu browsing and management. The system follows a layered architecture pattern with clear separation of concerns, enabling independent development, testing, and deployment of components. The architectural decisions presented here reflect the implementation of the system and address the requirements outlined in Chapter 4.

The MenuMap architecture is built on a three-tier foundation (Presentation, Business Logic, and Data Access layers) with additional specialized subsystems for security, menu management, user management, and notifications. This design ensures that the system can handle the expected load, maintain data integrity, and provide a secure environment for users and restaurant owners.

---

## 5.1 Overview

The MenuMap system follows a **Layered Architecture** pattern as the primary architectural style, with **Model-View-Controller (MVC)** as a secondary pattern implemented within the presentation layer. The system is decomposed into seven major subsystems that handle specific functional areas while maintaining clear separation of concerns.

### Primary Architectural Pattern: 3-Tier Architecture

The system is organized into three primary tiers:

1. **MM_Client (Presentation Tier)**: Handles all user interface components and user interactions across web and mobile platforms. This tier is responsible for rendering web pages, forms, and interactive elements, as well as client-side input validation.

2. **MM_Logic (Business Logic Tier)**: Contains core business rules, application logic, and orchestrates use case execution. This tier enforces business rules, validates data, and coordinates workflows between the presentation and data layers.

3. **MM_DataStore (Data Tier)**: Manages data persistence, retrieval, and database operations. This tier handles all database interactions, data mapping, transaction management, and cache operations.

**Figure 5.1: 3-Tier Architecture Diagram**

[Insert diagram: `Model_Static_Menu_Map_3_Tier.PNG` or `Model_Static_Model_Static_Menu_Map_3_Tier.PNG`]

**Caption:** The 3-tier architecture diagram shows the overall system structure with Presentation (MM_Client), Business Logic (MM_Logic), and Data (MM_DataStore) tiers.

### Secondary Architectural Pattern: MVC

The MVC pattern is implemented within the MM_Client tier:

- **Model**: Handles data representation and business logic at the presentation level
- **View**: UI components including Forms, Dashboard, Menu Browser, User Profile, and Restaurant Owner Panel
- **Controller**: User interaction handlers that process user input and coordinate with the business logic layer

**Reference Diagram:** `Package_MM_Client_MM_Client_Class_Dia.PNG` (See Appendix D)

### Design Patterns

The system incorporates several design patterns to enhance maintainability and flexibility:

- **Observer Pattern**: Used for real-time updates and notifications
- **Factory Pattern**: Facilitates object creation and management
- **Strategy Pattern**: Enables interchangeable algorithms for different business scenarios
- **Repository Pattern**: Provides a consistent interface for data access operations
- **DAO Pattern**: Abstracts database operations

**Reference Diagrams:** `Package_MM_Logic_MM_Logic_Class_Dia.PNG`, `Package_MM_DataStore_MM_Data_Store_Dia.PNG` (See Appendix D)

### Architectural Benefits

The layered architecture provides several key benefits:

1. **Separation of Concerns**: Each layer has distinct responsibilities, making the system easier to understand and maintain
2. **Maintainability**: Changes in one layer do not directly affect other layers, reducing the risk of unintended side effects
3. **Testability**: Each layer can be tested independently, enabling comprehensive unit and integration testing
4. **Scalability**: Layers can be scaled independently based on demand, optimizing resource utilization
5. **Flexibility**: The architecture supports multiple client types (web, mobile) using the same business logic

---

## 5.2 Subsystem Decomposition

The MenuMap system is decomposed into seven major subsystems, each handling specific functional areas:

### Subsystem 1: Presentation Layer (MM_Client)

**Purpose**: Handles all user interface components and user interactions across web and mobile platforms.

**Responsibilities**:
- User interface rendering (web pages, forms, interactive elements)
- Client-side user input validation
- Response formatting for display to users
- Mobile responsiveness and touch optimization
- Session management and authentication state

**Key Components**:
- **WebInterface**: LoginForm, Dashboard, MenuBrowser, UserProfile, RestaurantOwnerPanel
- **MobileInterface**: MobileApp, ResponsiveDesign, TouchOptimization
- **APIInterface**: RESTEndpoints, GraphQLQueries, WebSocketConnections

**Use Cases Supported**: UC-001, UC-002, UC-003, UC-004, UC-005, UC-006, UC-007

**Interfaces**:
- Communicates with Business Logic Layer through service interfaces
- Receives user input and displays system responses
- Manages client-side state and session information

### Subsystem 2: Business Logic Layer (MM_Logic)

**Purpose**: Contains core business rules, application logic, and orchestrates use case execution.

**Responsibilities**:
- Use case orchestration and coordination
- Business rule enforcement
- Server-side data validation
- Workflow management for complex business processes
- Transaction coordination for multi-step operations

**Key Components**:
- **UseCaseControllers**: MenuBrowsingController, FavoritesController, AuthenticationController, UserRegistrationController, MenuVerificationController, SpamProtectionController, RestaurantOwnerController
- **BusinessRules**: MenuValidationRules, UserPermissionRules, SpamDetectionRules, SecurityRules
- **WorkflowEngine**: AuthenticationWorkflow, MenuVerificationWorkflow, NotificationWorkflow

**Use Cases Supported**: All 7 use cases (orchestrates execution)

**Interfaces**:
- Receives requests from Presentation Layer
- Coordinates with Data Access Layer for data operations
- Enforces business rules and validations

### Subsystem 3: Data Access Layer (MM_DataStore)

**Purpose**: Manages data persistence, retrieval, and database operations.

**Responsibilities**:
- Database operations (CRUD for all entities)
- Data mapping between database and domain objects
- Transaction management to ensure data consistency
- Cache management for performance optimization
- Query optimization for efficient data access

**Key Components**:
- **Repositories**: UserRepository, MenuRepository, RestaurantRepository, FavoriteRepository, VerificationRepository
- **DataMappers**: UserMapper, MenuMapper, RestaurantMapper, FavoriteMapper
- **DatabaseConnections**: ConnectionPool, TransactionManager, QueryOptimizer
- **CacheManager**: RedisCache, MemoryCache, CacheInvalidation

**Use Cases Supported**: All 7 use cases (data persistence)

**Interfaces**:
- Provides data access interfaces to Business Logic Layer
- Manages database connections and transactions
- Handles cache operations

### Subsystem 4: Security Subsystem

**Purpose**: Handles authentication, authorization, and all security-related functionality.

**Responsibilities**:
- User authentication (login, logout, session management)
- Password security (hashing, reset, validation)
- Spam protection (detect and prevent spam content)
- Access control (role-based permissions)
- Security monitoring (audit logs, threat detection)

**Key Components**:
- **AuthenticationService**: LoginManager, SessionManager, TokenGenerator, PasswordValidator
- **AuthorizationService**: RoleManager, PermissionChecker, AccessController
- **SpamProtectionService**: ContentAnalyzer, BehaviorMonitor, MLDetector, RateLimiter
- **SecurityMonitoring**: AuditLogger, ThreatDetector, SecurityAlerts

**Use Cases Supported**: UC-003, UC-004, UC-005, UC-006

**Interfaces**:
- Provides authentication services to all subsystems
- Enforces authorization policies
- Monitors security events

### Subsystem 5: Menu Management Subsystem

**Purpose**: Manages restaurant and menu data, including browsing, search, and verification.

**Responsibilities**:
- Menu browsing and display
- Search functionality (location, cuisine, price-based)
- Menu verification (verify menu accuracy and authenticity)
- Restaurant data management
- Content moderation (review and approve menu content)

**Key Components**:
- **MenuService**: MenuBrowser, MenuSearch, MenuFilter, MenuRanking
- **RestaurantService**: RestaurantManager, LocationService, CuisineClassifier, RatingCalculator
- **VerificationService**: MenuVerifier, ContentValidator, AuthenticityChecker, ApprovalWorkflow
- **ContentModeration**: ContentReviewer, ModerationQueue, ApprovalSystem

**Use Cases Supported**: UC-001, UC-005, UC-007

**Interfaces**:
- Provides menu browsing and search services
- Handles menu verification processes
- Manages restaurant information

### Subsystem 6: User Management Subsystem

**Purpose**: Handles user accounts, profiles, preferences, and favorites management.

**Responsibilities**:
- User registration and account creation
- Profile management (update user information and preferences)
- Favorites management (add, remove, organize favorites)
- User preferences (store and manage user settings)
- Account management (activation, deactivation, deletion)

**Key Components**:
- **UserService**: UserRegistration, ProfileManager, AccountManager, UserValidator
- **FavoritesService**: FavoritesManager, FavoritesOrganizer, FavoritesSharing, FavoritesAnalytics
- **PreferencesService**: SettingsManager, NotificationPreferences, PrivacySettings, DisplayPreferences
- **UserAnalytics**: UsageTracker, BehaviorAnalyzer, RecommendationEngine

**Use Cases Supported**: UC-002, UC-004, UC-007

**Interfaces**:
- Provides user management services
- Handles favorites and preferences
- Manages user accounts

### Subsystem 7: Notification Subsystem

**Purpose**: Handles all types of notifications including email, SMS, and in-app notifications.

**Responsibilities**:
- Email delivery (password reset, confirmation emails)
- System notifications (in-app notifications and alerts)
- Real-time updates (WebSocket-based real-time notifications)
- Notification management (queue, schedule, track notifications)
- Template management (manage notification templates)

**Key Components**:
- **EmailService**: EmailSender, TemplateEngine, EmailQueue, DeliveryTracker
- **NotificationService**: InAppNotifications, PushNotifications, NotificationQueue, NotificationHistory
- **RealTimeService**: WebSocketManager, EventBroadcaster, ConnectionManager, MessageRouter
- **TemplateManager**: EmailTemplates, NotificationTemplates, TemplateEngine, TemplateVersioning

**Use Cases Supported**: UC-003, UC-004, UC-005, UC-006

**Interfaces**:
- Provides notification services to other subsystems
- Handles email and in-app notifications
- Manages real-time communication

### Subsystem Interactions

The subsystems interact through well-defined interfaces:

**Primary Data Flow**:
```
User Request → Presentation Layer → Business Logic Layer → Data Access Layer → Database
 ↓
 Security Subsystem (Authentication/Authorization)
 ↓
 Specific Subsystem (Menu/User/Notification)
 ↓
 Response ← Presentation Layer ← Business Logic Layer ← Data Access Layer
```

**Cross-Subsystem Dependencies**:
- Security ↔ All Subsystems: Provides authentication and authorization services
- Business Logic ↔ All Subsystems: Orchestrates and coordinates operations
- Data Access ↔ All Subsystems: Handles data persistence and retrieval
- Notification ↔ User Management: Uses user preferences and contact information
- Notification ↔ Security: Sends security alerts and password reset notifications
- Menu Management ↔ User Management: Manages user favorites and preferences

---

## 5.3 Hardware and Software Mapping

The MenuMap system is deployed as a web-based application using Java and associated web technologies. The system follows a traditional web application deployment model.

### Hardware Infrastructure

**Web Server**:
- Application server hosting the web application
- Handles HTTP requests and responses
- Manages application lifecycle

**Database Server**:
- Relational database management system (MySQL/PostgreSQL)
- Stores all persistent data
- Handles data queries and transactions

**Client Devices**:
- Web browsers (Chrome, Firefox, Safari, Edge)
- Desktop and mobile devices
- Responsive design for various screen sizes

### Software Technology Stack

**Frontend Technologies**:
- **HTML5**: Structure and content
- **CSS3**: Styling and layout
- **JavaScript**: Client-side interactivity
- **Web Framework**: React, Angular, or Vue.js (if applicable)

**Backend Technologies**:
- **Java**: Primary programming language
- **Web Framework**: Spring Boot, Java EE, or similar
- **Application Server**: Tomcat, Jetty, or similar
- **Build Tool**: Maven or Gradle

**Database Technologies**:
- **Primary Database**: MySQL 8.0+ or PostgreSQL 12+
- **Connection Pooling**: HikariCP or similar
- **ORM**: Hibernate, JPA, or similar

**Development Tools**:
- **IDE**: Eclipse, IntelliJ IDEA, or similar
- **Version Control**: Git
- **UML Modeling**: Eclipse Papyrus

### Software Component Mapping

**Presentation Layer (MM_Client)**:
- Deployed as web application on application server
- Serves HTML, CSS, JavaScript to client browsers
- Handles user interface rendering and interactions

**Business Logic Layer (MM_Logic)**:
- Java services and controllers
- Deployed on application server
- Processes business logic and coordinates operations

**Data Access Layer (MM_DataStore)**:
- Java DAOs and repositories
- Deployed on application server
- Connects to database server for data operations

**Database**:
- Relational database (MySQL/PostgreSQL)
- Runs on database server
- Stores all persistent data

### Deployment Architecture

**Single-Tier Deployment** (Development):
- Application server and database server on same machine
- Suitable for development and testing

**Two-Tier Deployment** (Production):
- Application server on one machine
- Database server on separate machine
- Provides better performance and security

**Network Configuration**:
- HTTP/HTTPS for web traffic
- Database connections over secure network
- Firewall rules for security

---

## 5.4 Persistent Data Management

The MenuMap system uses a **relational database** (MySQL or PostgreSQL) as the primary database for persistent data storage.

### Database Design

**Primary Database: MySQL 8.0+ or PostgreSQL 12+**
- Relational database management system
- ACID compliance for data integrity
- Support for complex queries and transactions
- Multi-user concurrent access support

**Database Schema**:

**Users Table**:
- Stores user accounts and authentication information
- Attributes: userId (PK), email, password (hashed), firstName, lastName, accountStatus, emailVerified, createdAt, updatedAt

**Restaurants Table**:
- Stores restaurant information and details
- Attributes: restaurantId (PK), name, address, phone, status, ownerUserId (FK), createdAt, updatedAt

**MenuItems Table**:
- Stores menu items with descriptions and prices
- Attributes: menuItemId (PK), restaurantId (FK), itemName, description, price, category, available, createdAt, updatedAt

**Favorites Table**:
- Stores user favorites relationships
- Attributes: favoriteId (PK), userId (FK), restaurantId (FK), createdAt

**Sessions Table**:
- Stores user session management data
- Attributes: sessionId (PK), userId (FK), token, expiryTime, createdAt

**Verification Table**:
- Stores menu verification records
- Attributes: verificationId (PK), menuId (FK), verifiedBy, status, verifiedAt, createdAt

**Notifications Table**:
- Stores notification history and tracking
- Attributes: notificationId (PK), userId (FK), type, message, sentAt, readAt

### Data Access Patterns

**Repository Pattern**:
- Consistent interface for data access operations
- Abstracts database implementation details
- Provides clean API for business logic layer

**Data Mappers**:
- Convert between database records and domain objects
- Handle data transformation
- Manage object-relational mapping

**Connection Pooling**:
- Efficient connection management
- Reuses database connections
- Improves performance and resource utilization

**Transaction Management**:
- Ensures data consistency across operations
- ACID properties for critical operations
- Rollback capability for error handling

### Data Storage Strategy

**Storage Architecture**:
- **Primary Storage**: Relational database with automated backups
- **Indexing**: Database indexes for efficient queries
- **Normalization**: Normalized database design to reduce redundancy

**Data Backup and Recovery**:
- Automated daily backups
- Backup retention policy
- Point-in-time recovery capability
- Backup encryption

**Data Integrity**:
- Foreign key constraints
- Check constraints for data validation
- Unique constraints for data uniqueness
- Referential integrity enforcement

### Data Access Operations

**Read Operations**:
- Primary database for all queries
- Indexed queries for performance
- Connection pooling for efficiency
- Caching for frequently accessed data (if implemented)

**Write Operations**:
- Primary database with transaction support
- Optimistic locking for concurrent updates
- Data validation at multiple layers
- Audit logging for data changes

**Data Consistency**:
- ACID transactions for critical operations
- Foreign key constraints for referential integrity
- Data validation at application and database levels
- Transaction rollback for error scenarios

---

## 5.5 Security Management

The MenuMap system implements comprehensive security measures to protect user data, ensure system integrity, and prevent unauthorized access.

### Security Architecture

**Authentication & Authorization**:
- **User Authentication**: Email/password authentication with secure password hashing
- **Session Management**: Secure session tokens with expiration
- **Role-Based Access Control (RBAC)**: Different roles (Customer, Restaurant Owner, Administrator) with appropriate permissions
- **Password Security**: BCrypt hashing with appropriate rounds, password complexity requirements

**Data Protection**:
- **Encryption at Rest**: Database encryption for sensitive data
- **Encryption in Transit**: HTTPS/TLS for all web traffic
- **Password Hashing**: One-way hashing (BCrypt) for passwords
- **Sensitive Data**: Encrypted storage for sensitive information

### Security Controls

**Threat Detection & Prevention**:
- **Input Validation**: All user inputs validated and sanitized
- **SQL Injection Prevention**: Parameterized queries, no string concatenation
- **XSS Protection**: Input sanitization and output encoding
- **CSRF Protection**: Token-based protection for state-changing operations
- **Rate Limiting**: Prevents brute force attacks

**Security Monitoring**:
- **Audit Logging**: Comprehensive logging of security events
- **Failed Login Tracking**: Monitors and logs failed login attempts
- **Account Lockout**: Automatic account lockout after multiple failed attempts
- **Security Alerts**: Notifications for suspicious activities

### Access Control

**User Roles**:
- **Customer**: Browse menus, manage favorites, view restaurant information
- **Restaurant Owner**: Manage own restaurant menus, update restaurant information
- **Administrator**: Verify menus, manage system settings, access all features

**Permission Model**:
- Role-based permissions
- Resource-level access control
- Operation-level restrictions
- Session-based authorization

### Security Policies

**Password Policy**:
- Minimum length requirements
- Complexity requirements (uppercase, lowercase, numbers, special characters)
- Password history enforcement
- Password expiration (if applicable)

**Session Policy**:
- Session timeout after inactivity
- Secure session token generation
- Session invalidation on logout
- Protection against session hijacking

**Data Privacy**:
- User data access restrictions
- Privacy policy compliance
- Data minimization principles
- User consent management

### Security Testing

**Security Measures Tested**:
- Password hashing verification
- SQL injection prevention
- XSS attack prevention
- Session management security
- Access control enforcement
- Input validation effectiveness

**Security Test Results**:
- All security test cases passed (see Chapter 7: Testing Process)
- No security vulnerabilities identified
- Security measures validated and verified

---

## References

- Appendix D: Detailed Class Diagrams
- Deliverable 2: Design Document (Architecture sections)
- Chapter 4: System Requirements

---

**Note**: This content should be integrated into the Final Systems Document Word file, maintaining the required formatting (1.5 line spacing, 16pt chapter headings, 13pt section headings, 11pt text). All diagrams referenced should be inserted as PNG images from `Deliverable2_Design/UML_Diagrams/Diagrams_Only/`.

