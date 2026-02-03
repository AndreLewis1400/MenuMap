# MenuMap Design Patterns
## CEN4010 Software Engineering - Team 9

**Author:** Andre Lewis (Software Architecture & Design Lead) 
**Date:** [Current Date] 
**Version:** 1.0 

---

## Design Patterns Overview

The MenuMap application implements three key design patterns to ensure maintainable, scalable, and flexible code architecture.

---

## Required Design Patterns (3+)

### **1. Observer Pattern**
**Purpose**: Handle real-time updates and notifications
**Implementation**: 
- User favorites updates
- Menu changes notifications
- Security alerts
- System status updates

**Benefits**:
- Loose coupling between components
- Dynamic subscription/unsubscription
- One-to-many dependency relationships
- Easy to add new observers

### **2. Factory Pattern**
**Purpose**: Create objects without specifying their exact classes
**Implementation**:
- User type creation (Regular, Premium, Restaurant Owner)
- Menu item creation (Food, Beverage, Dessert)
- Notification creation (Email, SMS, Push)
- Search strategy creation (Location, Cuisine, Price)

**Benefits**:
- Encapsulates object creation logic
- Easy to add new product types
- Centralized creation logic
- Reduces code duplication

### **3. Strategy Pattern**
**Purpose**: Define a family of algorithms and make them interchangeable
**Implementation**:
- Search algorithms (Location-based, Cuisine-based, Price-based)
- Authentication strategies (Email, OAuth, Two-factor)
- Payment processing strategies (Credit Card, PayPal, Apple Pay)
- Spam detection strategies (Content-based, Behavior-based, ML-based)

**Benefits**:
- Algorithm flexibility at runtime
- Easy to add new strategies
- Eliminates conditional statements
- Promotes code reusability

---

## Pattern Integration in Architecture

### **Observer Pattern in Menu Management**
```
MenuManager (Subject)
├── UserFavorites (Observer)
├── RestaurantOwner (Observer)
├── AdminDashboard (Observer)
└── NotificationService (Observer)
```

### **Factory Pattern in User Management**
```
UserFactory
├── createRegularUser()
├── createPremiumUser()
├── createRestaurantOwner()
└── createAdminUser()
```

### **Strategy Pattern in Search System**
```
SearchContext
├── LocationSearchStrategy
├── CuisineSearchStrategy
├── PriceSearchStrategy
└── RatingSearchStrategy
```

---

## Pattern Benefits for MenuMap

### **Observer Pattern Benefits:**
1. **Real-time Updates**: Users get instant notifications of menu changes
2. **Scalability**: Easy to add new notification types
3. **Maintainability**: Changes to notification logic don't affect other components
4. **Performance**: Efficient event handling without polling

### **Factory Pattern Benefits:**
1. **User Management**: Easy creation of different user types
2. **Extensibility**: Simple to add new user roles or menu item types
3. **Consistency**: Standardized object creation process
4. **Testing**: Easy to mock different object types

### **Strategy Pattern Benefits:**
1. **Search Flexibility**: Multiple search algorithms for different needs
2. **Authentication Options**: Support for various login methods
3. **Payment Integration**: Easy integration of new payment providers
4. **Spam Protection**: Multiple detection algorithms for better security

---

## Pattern Relationships

### **Observer + Factory Integration**
- Factory creates Observer objects
- Observer pattern manages Factory-created objects
- Dynamic observer registration/unregistration

### **Strategy + Factory Integration**
- Factory creates Strategy objects
- Strategy pattern uses Factory-created algorithms
- Runtime strategy selection and switching

### **Observer + Strategy Integration**
- Observer pattern notifies of strategy changes
- Strategy pattern affects observer behavior
- Dynamic strategy updates with real-time notifications

---

## Implementation Guidelines

### **Observer Pattern Implementation:**
1. Define Subject interface with attach/detach/notify methods
2. Create concrete Subject classes (MenuManager, UserManager)
3. Define Observer interface with update method
4. Implement concrete Observer classes
5. Register observers with subjects

### **Factory Pattern Implementation:**
1. Define Product interface/abstract class
2. Create concrete Product classes
3. Define Factory interface with creation methods
4. Implement concrete Factory classes
5. Use factory to create products

### **Strategy Pattern Implementation:**
1. Define Strategy interface with algorithm method
2. Create concrete Strategy classes
3. Define Context class with strategy reference
4. Implement strategy selection logic
5. Use context to execute strategies

---

## Pattern Selection Rationale

### **Why These Patterns?**
1. **Observer**: Essential for real-time features in a restaurant app
2. **Factory**: Needed for diverse user types and menu items
3. **Strategy**: Required for flexible search and authentication

### **Alternative Patterns Considered:**
- **Singleton**: For database connections (rejected - not needed for stateless design)
- **Command**: For user actions (rejected - overkill for simple operations)
- **Decorator**: For user features (rejected - inheritance hierarchy is sufficient)

---

*These design patterns provide a solid foundation for MenuMap's flexible and maintainable architecture.*
