# MenuMap 3-Tier Architecture Design
## CEN4010 Software Engineering - Team 9

**Author:** Andre Lewis (Software Architecture & Design Lead)  
**Date:** October 19, 2025  
**Version:** 1.0

---

## 🏗️ 3-Tier Architecture Overview

The MenuMap application follows a **3-Tier Architecture** pattern, providing clear separation of concerns and scalability. This architecture divides the application into three distinct layers, each with specific responsibilities and interfaces.

---

## 📊 Architecture Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                    TIER 1: PRESENTATION                      │
│                     (Client Tier)                            │
├─────────────────────────────────────────────────────────────┤
│  • Web Interface (React/HTML/CSS/JavaScript)                │
│  • Mobile Interface (React Native)                          │
│  • API Interface (REST/GraphQL)                             │
│  • User Interface Components                                │
│  • Input Validation & Formatting                            │
└─────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────┐
│                   TIER 2: BUSINESS LOGIC                    │
│                  (Application Tier)                         │
├─────────────────────────────────────────────────────────────┤
│  • Use Case Controllers                                      │
│  • Business Rules Engine                                    │
│  • Authentication & Authorization                           │
│  • Menu Management Services                                 │
│  • User Management Services                                 │
│  • Notification Services                                     │
│  • Security Services                                        │
└─────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────┐
│                     TIER 3: DATA                            │
│                   (Data Tier)                               │
├─────────────────────────────────────────────────────────────┤
│  • Database (PostgreSQL)                                  │
│  • Data Access Layer (Repositories)                         │
│  • Cache Layer (Redis)                                      │
│  • File Storage (AWS S3)                                    │
│  • Data Mapping & Persistence                               │
└─────────────────────────────────────────────────────────────┘
```

---

## 🎯 Tier 1: Presentation Tier (Client Tier)

### **Purpose**
Handles all user interface components and user interactions across multiple platforms.

### **Responsibilities**
- **User Interface Rendering**: Display web pages, forms, and interactive elements
- **User Input Validation**: Client-side validation of user inputs
- **Response Formatting**: Format data for display to users
- **Session Management**: Handle user sessions and authentication state
- **Mobile Responsiveness**: Ensure consistent experience across devices

### **Key Components**

#### **Web Interface**
```javascript
// React Components
├── LoginForm
├── Dashboard
├── MenuBrowser
├── UserProfile
├── RestaurantOwnerPanel
└── FavoritesManager
```

#### **Mobile Interface**
```javascript
// React Native Components
├── MobileApp
├── ResponsiveDesign
└── TouchOptimization
```

#### **API Interface**
```javascript
// REST/GraphQL Endpoints
├── RESTEndpoints
├── GraphQLQueries
└── AuthenticationEndpoints
```

### **Technologies**
- **Frontend**: React 18+, TypeScript, Material-UI
- **Mobile**: React Native 0.70+
- **API**: RESTful APIs, GraphQL
- **State Management**: Redux Toolkit

### **Interfaces**
- **Input**: User interactions, HTTP requests, WebSocket messages
- **Output**: HTML pages, JSON responses, real-time updates
- **Dependencies**: Business Logic Tier

---

## 🎯 Tier 2: Business Logic Tier (Application Tier)

### **Purpose**
Contains core business rules, application logic, and orchestrates use case execution.

### **Responsibilities**
- **Use Case Orchestration**: Coordinate execution of business processes
- **Business Rule Enforcement**: Apply domain-specific business rules
- **Data Validation**: Server-side validation of business data
- **Workflow Management**: Manage complex business workflows
- **Transaction Coordination**: Coordinate multi-step operations

### **Key Components**

#### **Use Case Controllers**
```java
// Business Logic Controllers
├── MenuBrowsingController
├── FavoritesController
├── AuthenticationController
├── MenuVerificationController
├── SpamProtectionController
└── RestaurantOwnerController
```

#### **Business Services**
```java
// Core Business Services
├── AuthenticationService
├── MenuService
├── UserService
├── SecurityService
└── SpamProtectionService
```

#### **Business Rules Engine**
```java
// Business Rules
├── MenuValidationRules
├── UserPermissionRules
├── SpamDetectionRules
└── SecurityRules
```

### **Technologies**
- **Backend**: Java 11+, Spring Boot 2.7+
- **Security**: Spring Security 5.7+
- **Business Logic**: Domain-driven design patterns
- **Validation**: Bean Validation (JSR-303)

### **Interfaces**
- **Input**: Requests from Presentation Tier
- **Output**: Responses to Presentation Tier, commands to Data Tier
- **Dependencies**: Data Tier, External Services

---

## 🎯 Tier 3: Data Tier

### **Purpose**
Manages data persistence, retrieval, and database operations.

### **Responsibilities**
- **Database Operations**: CRUD operations for all entities
- **Data Mapping**: Convert between database and domain objects
- **Transaction Management**: Ensure data consistency
- **Cache Management**: Optimize data access performance
- **Query Optimization**: Efficient database queries

### **Key Components**

#### **Data Access Layer**
```java
// Repository Pattern
├── UserRepository
├── MenuRepository
├── RestaurantRepository
├── FavoriteRepository
├── VerificationRepository
└── SecurityRepository
```

#### **Data Mappers**
```java
// Object-Relational Mapping
├── UserMapper
├── MenuMapper
├── RestaurantMapper
├── FavoriteMapper
└── VerificationMapper
```

#### **Database Layer**
```sql
-- Database Schema
├── Users Table
├── Restaurants Table
├── Menus Table
├── MenuItems Table
├── Favorites Table
├── Reviews Table
└── SecurityLogs Table
```

### **Technologies**
- **Database**: PostgreSQL 13+
- **Cache**: Redis 6+
- **ORM**: Hibernate/JPA
- **File Storage**: AWS S3

### **Interfaces**
- **Input**: Commands from Business Logic Tier
- **Output**: Data to Business Logic Tier
- **Dependencies**: Database, Cache Systems, File Storage

---

## 🔗 Tier Interactions & Data Flow

### **Primary Data Flow**
```
User Request → Presentation Tier → Business Logic Tier → Data Tier
                ↓
            Response ← Presentation Tier ← Business Logic Tier ← Data Tier
```

### **Detailed Interaction Flow**

#### **1. User Authentication Flow**
```
Web Interface → AuthenticationController → AuthenticationService → UserRepository → Database
                ↓
            Session Token ← AuthenticationController ← AuthenticationService ← UserRepository
```

#### **2. Menu Browsing Flow**
```
MenuBrowser → MenuController → MenuService → MenuRepository → Database
            ↓
        Menu Data ← MenuBrowser ← MenuController ← MenuService ← MenuRepository
```

#### **3. Favorites Management Flow**
```
FavoritesManager → FavoritesController → FavoritesService → FavoriteRepository → Database
                 ↓
             Success Response ← FavoritesController ← FavoritesService ← FavoriteRepository
```

---

## 📋 Use Case Mapping to 3-Tier Architecture

### **UC-001: Browse Restaurant Menus**
- **Presentation Tier**: MenuBrowser component, SearchInterface
- **Business Logic Tier**: MenuBrowsingController, MenuService
- **Data Tier**: MenuRepository, RestaurantRepository

### **UC-002: Manage Favorites**
- **Presentation Tier**: FavoritesManager component
- **Business Logic Tier**: FavoritesController, FavoritesService
- **Data Tier**: FavoriteRepository, UserRepository

### **UC-003: Secure Password Reset**
- **Presentation Tier**: PasswordResetForm
- **Business Logic Tier**: AuthenticationController, SecurityService
- **Data Tier**: UserRepository, SecurityRepository

### **UC-004: User Registration**
- **Presentation Tier**: RegistrationForm
- **Business Logic Tier**: UserRegistrationController, UserService
- **Data Tier**: UserRepository

### **UC-005: User Login**
- **Presentation Tier**: LoginForm
- **Business Logic Tier**: AuthenticationController, SecurityService
- **Data Tier**: UserRepository, SessionRepository

### **UC-006: User Logout**
- **Presentation Tier**: LogoutButton, SessionManager
- **Business Logic Tier**: AuthenticationController, SecurityService
- **Data Tier**: UserRepository, SessionRepository

### **UC-007: Restaurant Owner Menu Management**
- **Presentation Tier**: RestaurantOwnerPanel
- **Business Logic Tier**: RestaurantOwnerController, MenuService
- **Data Tier**: MenuRepository, RestaurantRepository

---

## 🎯 Architectural Benefits

### **3-Tier Architecture Benefits:**

#### **1. Separation of Concerns**
- **Presentation Tier**: Focuses on user interface and user experience
- **Business Logic Tier**: Handles business rules and application logic
- **Data Tier**: Manages data persistence and retrieval

#### **2. Scalability**
- **Independent Scaling**: Each tier can be scaled independently
- **Load Distribution**: Load can be distributed across tiers
- **Performance Optimization**: Each tier can be optimized separately

#### **3. Maintainability**
- **Clear Boundaries**: Well-defined interfaces between tiers
- **Independent Development**: Teams can work on different tiers
- **Easy Testing**: Each tier can be tested independently

#### **4. Technology Flexibility**
- **Technology Independence**: Each tier can use different technologies
- **Easy Migration**: Technologies can be changed without affecting other tiers
- **Best Practices**: Use best technology for each tier's purpose

---

## 🔒 Security Considerations

### **Tier-Specific Security**

#### **Presentation Tier Security**
- **Input Validation**: Client-side and server-side validation
- **XSS Protection**: Cross-site scripting prevention
- **CSRF Protection**: Cross-site request forgery prevention
- **Session Management**: Secure session handling

#### **Business Logic Tier Security**
- **Authentication**: User authentication and authorization
- **Business Rule Enforcement**: Security rules and permissions
- **Data Validation**: Server-side validation of all inputs
- **Audit Logging**: Security event logging

#### **Data Tier Security**
- **Database Security**: Encrypted connections and data
- **Access Control**: Role-based database access
- **Data Encryption**: Encryption at rest and in transit
- **Backup Security**: Secure backup and recovery

---

## 📊 Performance Considerations

### **Tier-Specific Performance**

#### **Presentation Tier Performance**
- **Response Time**: < 200ms for UI updates
- **Caching**: Browser caching and CDN
- **Optimization**: Minification and compression
- **Mobile Performance**: Optimized for mobile devices

#### **Business Logic Tier Performance**
- **Processing Time**: < 500ms for business operations
- **Caching**: Application-level caching
- **Load Balancing**: Multiple application servers
- **Database Connection Pooling**: Efficient connection management

#### **Data Tier Performance**
- **Query Performance**: < 100ms for database queries
- **Indexing**: Strategic database indexing
- **Caching**: Redis caching for frequently accessed data
- **Connection Pooling**: Optimized database connections

---

## 🚀 Deployment Architecture

### **Tier Deployment Strategy**

#### **Presentation Tier Deployment**
- **Web Servers**: NGINX for static content
- **CDN**: Global content delivery network
- **Load Balancer**: Distribute traffic across servers
- **SSL/TLS**: Secure communication

#### **Business Logic Tier Deployment**
- **Application Servers**: Multiple Spring Boot instances
- **Load Balancer**: Distribute application requests
- **Container Orchestration**: Kubernetes for scaling
- **Health Monitoring**: Application health checks

#### **Data Tier Deployment**
- **Database Servers**: PostgreSQL with read replicas
- **Cache Servers**: Redis cluster for high availability
- **File Storage**: AWS S3 for static assets
- **Backup Systems**: Automated backup and recovery

---

## 📈 Scalability Roadmap

### **Horizontal Scaling**
- **Presentation Tier**: Multiple web servers with load balancing
- **Business Logic Tier**: Auto-scaling application servers
- **Data Tier**: Database read replicas and caching

### **Vertical Scaling**
- **CPU Optimization**: Multi-core processing
- **Memory Optimization**: Efficient memory usage
- **Storage Optimization**: SSD storage for better performance

---

## 🎯 Quality Attributes

### **Reliability**
- **99.9% Uptime**: High availability across all tiers
- **Fault Tolerance**: Graceful degradation during failures
- **Backup & Recovery**: Automated backup and disaster recovery
- **Health Monitoring**: Continuous monitoring and alerting

### **Maintainability**
- **Modular Design**: Clear separation of concerns
- **Documentation**: Comprehensive documentation for each tier
- **Testing**: Unit, integration, and end-to-end testing
- **Code Standards**: Consistent coding standards across tiers

### **Usability**
- **Responsive Design**: Works on all devices and screen sizes
- **Intuitive Interface**: User-friendly interface design
- **Accessibility**: WCAG 2.1 compliance
- **Performance**: Fast response times and smooth interactions

---

*This 3-tier architecture provides a solid foundation for MenuMap's scalable, maintainable, and secure software system.*
