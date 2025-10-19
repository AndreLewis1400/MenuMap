# MenuMap Package Diagram - Software Architecture
## CEN4010 Software Engineering - Team 9

**Author:** Andre Lewis (Software Architecture & Design Lead)  
**Date:** [Current Date]  
**Version:** 1.0  

---

## 🏗️ Package Diagram Overview

The MenuMap application follows a **Layered Architecture** pattern with **MVC** as the secondary pattern. The system is decomposed into major subsystems that handle specific functional areas.

---

## 📦 Major Subsystems (Packages)

### **1. Presentation Layer**
- **Purpose**: Handles user interface and user interactions
- **Responsibilities**: 
  - Web interface rendering
  - User input validation
  - Response formatting
  - Mobile responsiveness

### **2. Business Logic Layer**
- **Purpose**: Contains core business rules and application logic
- **Responsibilities**:
  - Use case orchestration
  - Business rule enforcement
  - Data validation
  - Workflow management

### **3. Data Access Layer**
- **Purpose**: Manages data persistence and retrieval
- **Responsibilities**:
  - Database operations
  - Data mapping
  - Transaction management
  - Cache management

### **4. Security Subsystem**
- **Purpose**: Handles authentication, authorization, and security
- **Responsibilities**:
  - User authentication
  - Password reset security
  - Spam protection
  - Access control

### **5. Menu Management Subsystem**
- **Purpose**: Manages restaurant and menu data
- **Responsibilities**:
  - Menu browsing and search
  - Menu verification
  - Restaurant data management
  - Content moderation

### **6. User Management Subsystem**
- **Purpose**: Handles user accounts and preferences
- **Responsibilities**:
  - User registration
  - Profile management
  - Favorites management
  - User preferences

### **7. Notification Subsystem**
- **Purpose**: Handles email and system notifications
- **Responsibilities**:
  - Email delivery
  - Password reset emails
  - System notifications
  - Alert management

---

## 🔗 Package Dependencies

```
Presentation Layer
    ↓ (depends on)
Business Logic Layer
    ↓ (depends on)
Data Access Layer
    ↓ (depends on)
Database

Security Subsystem
    ↓ (provides services to)
Business Logic Layer

Menu Management Subsystem
    ↓ (provides services to)
Business Logic Layer

User Management Subsystem
    ↓ (provides services to)
Business Logic Layer

Notification Subsystem
    ↓ (provides services to)
Business Logic Layer
```

---

## 📋 Use Case Mapping to Subsystems

### **UC-001: Browse Restaurant Menus**
- **Primary**: Menu Management Subsystem
- **Secondary**: Business Logic Layer, Data Access Layer

### **UC-002: Manage Favorites**
- **Primary**: User Management Subsystem
- **Secondary**: Business Logic Layer, Data Access Layer

### **UC-003: Secure Password Reset**
- **Primary**: Security Subsystem
- **Secondary**: Notification Subsystem, Business Logic Layer

### **UC-004: User Registration & Login**
- **Primary**: User Management Subsystem, Security Subsystem
- **Secondary**: Business Logic Layer, Data Access Layer

### **UC-005: Menu Verification System**
- **Primary**: Menu Management Subsystem, Security Subsystem
- **Secondary**: Business Logic Layer, Data Access Layer

### **UC-006: Spam Protection System**
- **Primary**: Security Subsystem
- **Secondary**: Business Logic Layer, Data Access Layer

### **UC-007: Restaurant Owner Menu Management**
- **Primary**: Menu Management Subsystem, User Management Subsystem
- **Secondary**: Business Logic Layer, Data Access Layer

---

## 🎯 Architectural Benefits

### **Layered Architecture Benefits:**
1. **Separation of Concerns**: Each layer has distinct responsibilities
2. **Maintainability**: Changes in one layer don't affect others
3. **Testability**: Each layer can be tested independently
4. **Scalability**: Layers can be scaled based on demand

### **MVC Pattern Benefits:**
1. **UI Flexibility**: Multiple interfaces can use same business logic
2. **Code Reusability**: Business logic is independent of presentation
3. **Team Development**: UI and business logic can be developed in parallel
4. **Testing**: Each component can be unit tested separately

---

## 🔒 Security Considerations

- **Authentication**: Handled by Security Subsystem
- **Authorization**: Role-based access control
- **Data Encryption**: All sensitive data encrypted
- **Audit Logging**: All security events logged
- **Rate Limiting**: Prevents abuse and attacks

---

*This package diagram provides the foundation for MenuMap's software architecture design.*
