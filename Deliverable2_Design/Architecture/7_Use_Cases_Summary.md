# MenuMap 7 Use Cases - 3-Tier Architecture Summary
## CEN4010 Software Engineering - Team 9

**Author:** Andre Lewis (Software Architecture & Design Lead)  
**Date:** October 19, 2025  
**Version:** 1.0

---

## 🎯 7 Use Cases for MenuMap Application

### **Core Use Cases (3 from Deliverable 1)**
1. **UC-001: Browse Restaurant Menus** (Normal Use Case)
2. **UC-002: Manage Favorites** (Normal Use Case)  
3. **UC-003: Secure Password Reset** (Security Use Case)

### **Additional Use Cases (4 to be defined)**
4. **UC-004: User Registration** (Normal Use Case)
5. **UC-005: User Login** (Normal Use Case)
6. **UC-006: User Logout** (Normal Use Case)
7. **UC-007: Restaurant Owner Menu Management** (Normal Use Case)

---

## 🏗️ 3-Tier Architecture Mapping

### **Tier 1: Presentation Tier (Client Tier)**
- **Web Interface**: React components for web browser
- **Mobile Interface**: React Native for mobile devices
- **API Interface**: REST/GraphQL endpoints

### **Tier 2: Business Logic Tier (Application Tier)**
- **Use Case Controllers**: Handle specific use cases
- **Business Services**: Core business logic
- **Security Services**: Authentication and authorization

### **Tier 3: Data Tier**
- **Database**: PostgreSQL for data storage
- **Cache Layer**: Redis for performance
- **File Storage**: AWS S3 for static files

---

## 📋 Use Case to 3-Tier Mapping

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

## 🔄 Data Flow Through 3-Tier Architecture

### **Request Flow**
```
User Request → Presentation Tier → Business Logic Tier → Data Tier
```

### **Response Flow**
```
Data Tier → Business Logic Tier → Presentation Tier → User Response
```

### **Example: UC-001 Browse Restaurant Menus**
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

## 🎯 Key Benefits of 3-Tier Architecture

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

## 📋 Implementation Checklist

### **Tier 1: Presentation Tier**
- [x] Web Interface components (React)
- [x] Mobile Interface components (React Native)
- [x] API Interface (REST/GraphQL)
- [x] Input validation and formatting
- [x] Session management
- [x] Responsive design

### **Tier 2: Business Logic Tier**
- [x] Use Case Controllers (7 controllers)
- [x] Business Services (MenuService, UserService, SecurityService)
- [x] Security Services (Authentication, Authorization)
- [x] Business Rules Engine
- [x] Workflow Management
- [x] Data Validation

### **Tier 3: Data Tier**
- [x] Database schema (PostgreSQL)
- [x] Data Access Layer (Repositories)
- [x] Cache Layer (Redis)
- [x] File Storage (AWS S3)
- [x] Data Mapping and Persistence
- [x] Transaction Management

---

## 🎉 Conclusion

The 3-tier architecture provides a solid foundation for the MenuMap application with exactly 7 use cases:

1. **UC-001**: Browse Restaurant Menus
2. **UC-002**: Manage Favorites
3. **UC-003**: Secure Password Reset
4. **UC-004**: User Registration
5. **UC-005**: User Login
6. **UC-006**: User Logout
7. **UC-007**: Restaurant Owner Menu Management

This architecture ensures clear separation of concerns, scalability, maintainability, and security across all tiers.

---

*This 3-tier architecture provides a comprehensive foundation for MenuMap's software system with exactly 7 use cases as required for CEN4010 Deliverable 2.*
