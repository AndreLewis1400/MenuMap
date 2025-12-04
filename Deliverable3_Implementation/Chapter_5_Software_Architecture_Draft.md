# Chapter 5: Software Architecture - Draft Content
## MenuMap Final Systems Document

**Author:** Andre Lewis (Group Lead)  
**Date:** [Current Date]  
**Status:** Draft - Ready for Final Document Integration

---

## 5.0 Introduction

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

**Reference Diagram:** `Model_Static_Menu_Map_3_Tier.PNG` (See Appendix D)

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

### Subsystem 1: Presentation Layer

**Purpose**: Handles all user interface components and user interactions across web and mobile platforms.

**Responsibilities**:
- User interface rendering (web pages, forms, interactive elements)
- Client-side user input validation
- Response formatting for display to users
- Mobile responsiveness and touch optimization
- Session management and authentication state

**Key Components**:
- WebInterface (LoginForm, Dashboard, MenuBrowser, UserProfile, RestaurantOwnerPanel)
- MobileInterface (MobileApp, ResponsiveDesign, TouchOptimization)
- APIInterface (RESTEndpoints, GraphQLQueries, WebSocketConnections)

**Use Cases Supported**: UC-001, UC-002, UC-003, UC-004, UC-005, UC-006, UC-007

### Subsystem 2: Business Logic Layer

**Purpose**: Contains core business rules, application logic, and orchestrates use case execution.

**Responsibilities**:
- Use case orchestration and coordination
- Business rule enforcement
- Server-side data validation
- Workflow management for complex business processes
- Transaction coordination for multi-step operations

**Key Components**:
- UseCaseControllers (MenuBrowsingController, FavoritesController, AuthenticationController, UserRegistrationController, MenuVerificationController, SpamProtectionController, RestaurantOwnerController)
- BusinessRules (MenuValidationRules, UserPermissionRules, SpamDetectionRules, SecurityRules)
- WorkflowEngine (AuthenticationWorkflow, MenuVerificationWorkflow, NotificationWorkflow)

**Use Cases Supported**: All 7 use cases (orchestrates execution)

### Subsystem 3: Data Access Layer

**Purpose**: Manages data persistence, retrieval, and database operations.

**Responsibilities**:
- Database operations (CRUD for all entities)
- Data mapping between database and domain objects
- Transaction management to ensure data consistency
- Cache management for performance optimization
- Query optimization for efficient data access

**Key Components**:
- Repositories (UserRepository, MenuRepository, RestaurantRepository, FavoriteRepository, VerificationRepository)
- DataMappers (UserMapper, MenuMapper, RestaurantMapper, FavoriteMapper)
- DatabaseConnections (ConnectionPool, TransactionManager, QueryOptimizer)
- CacheManager (RedisCache, MemoryCache, CacheInvalidation)

**Use Cases Supported**: All 7 use cases (data persistence)

### Subsystem 4: Security Subsystem

**Purpose**: Handles authentication, authorization, and all security-related functionality.

**Responsibilities**:
- User authentication (login, logout, session management)
- Password security (hashing, reset, validation)
- Spam protection (detect and prevent spam content)
- Access control (role-based permissions)
- Security monitoring (audit logs, threat detection)

**Key Components**:
- AuthenticationService (LoginManager, SessionManager, TokenGenerator, PasswordValidator)
- AuthorizationService (RoleManager, PermissionChecker, AccessController)
- SpamProtectionService (ContentAnalyzer, BehaviorMonitor, MLDetector, RateLimiter)
- SecurityMonitoring (AuditLogger, ThreatDetector, SecurityAlerts)

**Use Cases Supported**: UC-003, UC-004, UC-005, UC-006

### Subsystem 5: Menu Management Subsystem

**Purpose**: Manages restaurant and menu data, including browsing, search, and verification.

**Responsibilities**:
- Menu browsing and display
- Search functionality (location, cuisine, price-based)
- Menu verification (verify menu accuracy and authenticity)
- Restaurant data management
- Content moderation (review and approve menu content)

**Key Components**:
- MenuService (MenuBrowser, MenuSearch, MenuFilter, MenuRanking)
- RestaurantService (RestaurantManager, LocationService, CuisineClassifier, RatingCalculator)
- VerificationService (MenuVerifier, ContentValidator, AuthenticityChecker, ApprovalWorkflow)
- ContentModeration (ContentReviewer, ModerationQueue, ApprovalSystem)

**Use Cases Supported**: UC-001, UC-005, UC-007

### Subsystem 6: User Management Subsystem

**Purpose**: Handles user accounts, profiles, preferences, and favorites management.

**Responsibilities**:
- User registration and account creation
- Profile management (update user information and preferences)
- Favorites management (add, remove, organize favorites)
- User preferences (store and manage user settings)
- Account management (activation, deactivation, deletion)

**Key Components**:
- UserService (UserRegistration, ProfileManager, AccountManager, UserValidator)
- FavoritesService (FavoritesManager, FavoritesOrganizer, FavoritesSharing, FavoritesAnalytics)
- PreferencesService (SettingsManager, NotificationPreferences, PrivacySettings, DisplayPreferences)
- UserAnalytics (UsageTracker, BehaviorAnalyzer, RecommendationEngine)

**Use Cases Supported**: UC-002, UC-004, UC-007

### Subsystem 7: Notification Subsystem

**Purpose**: Handles all types of notifications including email, SMS, and in-app notifications.

**Responsibilities**:
- Email delivery (password reset, confirmation emails)
- System notifications (in-app notifications and alerts)
- Real-time updates (WebSocket-based real-time notifications)
- Notification management (queue, schedule, track notifications)
- Template management (manage notification templates)

**Key Components**:
- EmailService (EmailSender, TemplateEngine, EmailQueue, DeliveryTracker)
- NotificationService (InAppNotifications, PushNotifications, NotificationQueue, NotificationHistory)
- RealTimeService (WebSocketManager, EventBroadcaster, ConnectionManager, MessageRouter)
- TemplateManager (EmailTemplates, NotificationTemplates, TemplateEngine, TemplateVersioning)

**Use Cases Supported**: UC-003, UC-004, UC-005, UC-006

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

The MenuMap system is deployed on **Amazon Web Services (AWS)** cloud infrastructure, utilizing a microservices architecture with containerized deployment.

### Deployment Architecture

**Cloud Infrastructure Provider**: Amazon Web Services (AWS)
- Primary deployment: AWS (US-East-1 region)
- Secondary: Google Cloud Platform (GCP) for disaster recovery
- CDN: CloudFront for global content delivery

**Architecture Pattern**: Microservices Architecture with containerized deployment
- Event-driven architecture for real-time features
- API Gateway pattern for service orchestration
- Database per service pattern for data isolation

### Hardware Infrastructure

**Web Tier (Load Balancer & API Gateway)**:
- AWS Application Load Balancer: 10,000+ concurrent connections, SSL termination
- AWS API Gateway: Regional API Gateway, 10,000 requests/second, 5GB cache
- CloudFront CDN: 200+ edge locations globally, 1TB cache capacity

**Application Tier (Microservices)**:
- Presentation Service: t3.large instances (2 vCPU, 8GB RAM), auto-scaling 2-10 instances
- Business Logic Service: t3.xlarge instances (4 vCPU, 16GB RAM), auto-scaling 3-15 instances
- Security Service: t3.large instances (2 vCPU, 8GB RAM), auto-scaling 2-8 instances
- Menu Management Service: t3.xlarge instances (4 vCPU, 16GB RAM), auto-scaling 3-12 instances
- User Management Service: t3.large instances (2 vCPU, 8GB RAM), auto-scaling 2-10 instances
- Notification Service: t3.medium instances (2 vCPU, 4GB RAM), auto-scaling 2-6 instances

**Data Tier (Databases & Storage)**:
- Primary Database (PostgreSQL): db.r5.xlarge (4 vCPU, 32GB RAM), 1TB SSD, Multi-AZ for high availability
- Cache Layer (Redis): cache.r6g.large (2 vCPU, 13GB RAM), cluster mode with 3 nodes
- Search Engine (Elasticsearch): r6g.large (2 vCPU, 16GB RAM), 3 master nodes + 3 data nodes
- File Storage (S3): Unlimited capacity, versioning enabled, AES-256 encryption

### Software Technology Stack

**Frontend Technologies**:
- Web Application: React 18.x, TypeScript 4.x, Redux Toolkit, Material-UI, React Router v6
- Mobile Application: React Native 0.72.x, TypeScript 4.x, React Navigation v6, NativeBase

**Backend Technologies**:
- Runtime: Node.js 18.x LTS
- Framework: Express.js 4.x
- Language: TypeScript 4.x
- ORM: Prisma 5.x
- Authentication: JWT + Passport.js
- Logging: Winston
- Monitoring: Prometheus + Grafana

**Database Technologies**:
- Primary Database: PostgreSQL 15.x with PgBouncer connection pooling
- Cache: Redis 7.x with Redis Cluster
- Search: Elasticsearch 8.x with Kibana visualization

**DevOps & Infrastructure**:
- Containerization: Docker 24.x
- Orchestration: Kubernetes 1.28.x
- Service Mesh: Istio 1.19.x
- CI/CD: GitHub Actions with AWS ECR
- Monitoring: Prometheus, Grafana, ELK Stack, New Relic

### Software Component Mapping

**Presentation Layer**: React SPA deployed on AWS S3 + CloudFront, domain: www.menumap.com

**Business Logic Layer**: Node.js microservices deployed on AWS ECS (Fargate) with auto-scaling

**Data Access Layer**: Data access services on AWS ECS (Fargate) with AWS RDS PostgreSQL

**Security Subsystem**: Auth microservice on AWS ECS (Fargate) with AWS Secrets Manager

**Menu Management Subsystem**: Menu microservice on AWS ECS (Fargate) with AWS OpenSearch

**User Management Subsystem**: User microservice on AWS ECS (Fargate) with AWS ElastiCache Redis

**Notification Subsystem**: Email microservice on AWS ECS (Fargate) with AWS SES

---

## 5.4 Persistent Data Management

The MenuMap system uses **PostgreSQL** as the primary database for persistent data storage, with **Redis** for caching and **Elasticsearch** for search functionality.

### Database Design

**Primary Database: PostgreSQL 15.x**
- Relational database management system
- ACID compliance for data integrity
- Support for complex queries and transactions
- Multi-AZ deployment for high availability

**Database Schema**:
- **Users Table**: User accounts, authentication data, profile information
- **Restaurants Table**: Restaurant information, location, contact details
- **Menu Items Table**: Menu items, descriptions, prices, categories
- **Favorites Table**: User favorites relationships
- **Sessions Table**: User session management
- **Verification Table**: Menu verification records
- **Notifications Table**: Notification history and tracking

**Data Access Patterns**:
- **Repository Pattern**: Consistent interface for data access operations
- **Data Mappers**: Convert between database and domain objects
- **Connection Pooling**: PgBouncer for efficient connection management
- **Transaction Management**: Ensure data consistency across operations

### Data Storage Strategy

**Storage Architecture**:
- **Primary Storage**: PostgreSQL database with automated daily backups
- **Cache Storage**: Redis for frequently accessed data (menu items, user sessions)
- **Search Index**: Elasticsearch for full-text search capabilities
- **File Storage**: AWS S3 for images and static content

**Data Backup and Recovery**:
- Automated daily backups with 30-day retention
- Cross-region replication for disaster recovery
- Point-in-time recovery capability
- Backup encryption with AWS KMS

### Data Access Patterns

**Read Operations**:
- Primary database for complex queries
- Redis cache for frequently accessed data
- Elasticsearch for search queries
- Connection pooling for efficient resource utilization

**Write Operations**:
- Primary database with transaction support
- Cache invalidation on data updates
- Search index updates for menu changes
- Asynchronous processing for non-critical updates

**Data Consistency**:
- ACID transactions for critical operations
- Eventual consistency for cache updates
- Optimistic locking for concurrent updates
- Data validation at multiple layers

---

## 5.5 Security Management

The MenuMap system implements comprehensive security measures to protect user data, ensure system integrity, and prevent unauthorized access.

### Security Architecture

**Authentication & Authorization**:
- **Multi-Factor Authentication (MFA)**: Username/password with optional SMS/Email OTP and Authenticator App
- **Session Management**: JWT tokens with RS256 signing, 15-minute access token expiration, 7-day refresh token
- **Role-Based Access Control (RBAC)**: Guest User, Registered User, Premium User, Restaurant Owner, Administrator roles
- **Password Security**: bcrypt hashing with 12 rounds, password complexity requirements, password history enforcement

**Data Protection**:
- **Encryption at Rest**: AES-256 encryption for database, S3 storage, and Redis cache
- **Encryption in Transit**: TLS 1.3 for web traffic, HTTPS for API calls, SSL/TLS for database connections
- **Key Management**: AWS KMS for encryption key management and rotation
- **Field-Level Encryption**: Sensitive fields encrypted at application level

### Security Controls

**Threat Detection & Prevention**:
- **Web Application Firewall (WAF)**: OWASP Top 10 protection, rate limiting (10,000 requests/minute)
- **DDoS Protection**: AWS Shield Advanced
- **Spam Protection**: Multi-layer spam detection with content analysis, behavioral analysis, and machine learning
- **SQL Injection Prevention**: Parameterized queries and input validation
- **XSS Protection**: Input sanitization and output encoding

**Security Monitoring**:
- **Real-time Threat Detection**: Automated alerts for security events
- **Audit Logging**: Comprehensive logging of security events and user actions
- **Incident Response**: 15-minute detection time, 1-hour response time, 24-hour resolution time
- **Security Metrics**: Vulnerability tracking, incident metrics, compliance monitoring

### Compliance & Privacy

**Privacy Compliance**:
- **GDPR Compliance**: Data minimization, consent management, right to access/rectification/erasure, data portability
- **CCPA Compliance**: Consumer rights (access, deletion, opt-out), transparent data sharing policies
- **Data Retention**: 3 years for confidential data, 1 year for restricted data after account deletion

**Security Policies**:
- Information Security Policy
- Acceptable Use Policy
- Password Policy
- Data Protection Policy

**Security Testing**:
- Static Application Security Testing (SAST)
- Dynamic Application Security Testing (DAST)
- Penetration Testing
- Security Code Reviews

---

## References

- Appendix D: Detailed Class Diagrams
- Deliverable 2: Design Document (Architecture sections)
- Chapter 4: System Requirements

---

**Note**: This content should be integrated into the Final Systems Document Word file, maintaining the required formatting (1.5 line spacing, 16pt chapter headings, 13pt section headings, 11pt text). All diagrams referenced should be inserted as PNG images from `Deliverable2_Design/UML_Diagrams/Diagrams_Only/`.



