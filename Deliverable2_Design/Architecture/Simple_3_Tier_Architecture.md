# MenuMap Simple 3-Tier Architecture
## CEN4010 Software Engineering - Team 9

**Author:** Andre Lewis (Software Architecture & Design Lead)  
**Date:** October 19, 2025  
**Version:** 1.0

---

## 🏗️ Simple 3-Tier Architecture Overview

The MenuMap application follows a **3-Tier Architecture** pattern with clear separation of concerns across three distinct layers.

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
└─────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────┐
│                   TIER 2: BUSINESS LOGIC                    │
│                  (Application Tier)                         │
├─────────────────────────────────────────────────────────────┤
│  • Use Case Controllers                                      │
│  • Business Services                                        │
│  • Security Services                                        │
└─────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────┐
│                     TIER 3: DATA                            │
│                   (Data Tier)                               │
├─────────────────────────────────────────────────────────────┤
│  • Database (PostgreSQL)                                    │
│  • Cache Layer (Redis)                                      │
│  • File Storage (AWS S3)                                    │
└─────────────────────────────────────────────────────────────┘
```

---

## 🎯 Tier 1: Presentation Tier

### **Purpose**
Handles all user interface components and user interactions.

### **Key Components**
- **Web Interface**: React components for web browser
- **Mobile Interface**: React Native for mobile devices
- **API Interface**: REST/GraphQL endpoints

### **Technologies**
- React 18+, TypeScript, Material-UI
- React Native 0.70+
- RESTful APIs, GraphQL

---

## 🎯 Tier 2: Business Logic Tier

### **Purpose**
Contains core business rules, application logic, and use case orchestration.

### **Key Components**
- **Use Case Controllers**: Handle specific use cases
- **Business Services**: Core business logic
- **Security Services**: Authentication and authorization

### **Technologies**
- Java 11+, Spring Boot 2.7+
- Spring Security 5.7+
- Domain-driven design patterns

---

## 🎯 Tier 3: Data Tier

### **Purpose**
Manages data persistence, retrieval, and database operations.

### **Key Components**
- **Database**: PostgreSQL for data storage
- **Cache Layer**: Redis for performance
- **File Storage**: AWS S3 for static files

### **Technologies**
- PostgreSQL 13+
- Redis 6+
- AWS S3
- Hibernate/JPA

---

## 📋 Use Case Mapping to 3-Tier Architecture

### **UC-001: Browse Restaurant Menus**
- **Presentation Tier**: MenuBrowser component
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

## 🔄 Simple Data Flow

### **Request Flow**
```
User Request → Presentation Tier → Business Logic Tier → Data Tier
```

### **Response Flow**
```
Data Tier → Business Logic Tier → Presentation Tier → User Response
```

### **Example: Browse Restaurant Menus**
```
1. User clicks "Browse Menus" in Web Interface
2. Web Interface → MenuController
3. MenuController → MenuService
4. MenuService → MenuRepository
5. MenuRepository → PostgreSQL Database
6. Database returns menu data
7. Data flows back through tiers to user
```

---

## 🎯 Key Benefits

### **1. Separation of Concerns**
- **Presentation Tier**: User interface only
- **Business Logic Tier**: Business rules and logic
- **Data Tier**: Data storage and retrieval

### **2. Scalability**
- Each tier can be scaled independently
- Load can be distributed across multiple servers

### **3. Maintainability**
- Clear boundaries between tiers
- Easy to modify and extend
- Independent testing of each tier

### **4. Technology Flexibility**
- Each tier can use optimal technologies
- Easy to change technologies without affecting other tiers

---

## 🔒 Security Across Tiers

### **Presentation Tier Security**
- Input validation
- XSS protection
- CSRF protection

### **Business Logic Tier Security**
- Authentication
- Authorization
- Business rule enforcement

### **Data Tier Security**
- Database encryption
- Access control
- Data encryption

---

## 📊 Performance Targets

### **Presentation Tier**
- Response time: < 200ms for UI updates
- Load time: < 3 seconds for initial page load

### **Business Logic Tier**
- Processing time: < 500ms for business operations
- Throughput: 1000+ requests per second

### **Data Tier**
- Query time: < 100ms for database queries
- Connection pool: 100+ concurrent connections

---

## 🚀 Deployment Strategy

### **Tier Deployment**
- **Presentation Tier**: Web servers with load balancing
- **Business Logic Tier**: Application servers with auto-scaling
- **Data Tier**: Database servers with read replicas

---

*This simple 3-tier architecture provides a clear, maintainable foundation for the MenuMap application.*
