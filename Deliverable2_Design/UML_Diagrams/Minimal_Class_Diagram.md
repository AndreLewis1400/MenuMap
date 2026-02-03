# MenuMap Minimal Class Diagram
## CEN4010 Software Engineering - Team 9

**Author:** Andre Lewis (Software Architecture & Design Lead)  
**Date:** [Current Date]  
**Version:** 1.0  

---

## Minimal Class Diagram Overview

This minimal class diagram shows all classes in the MenuMap system without attributes or methods, focusing on class relationships and design pattern identification.

---

## Core Classes

### **User Management Classes**
- **User** - Base class for all user types
- **RegularUser** - Standard application users
- **PremiumUser** - Users with premium features
- **RestaurantOwner** - Restaurant owners and managers
- **Admin** - System administrators

### **Menu Management Classes**
- **Restaurant** - Restaurant information and data
- **Menu** - Restaurant menu container
- **MenuItem** - Individual menu items
- **Category** - Menu item categories
- **Review** - User reviews and ratings

### **Favorites Management Classes**
- **FavoritesManager** - Manages user favorites
- **FavoriteRestaurant** - User's favorite restaurants
- **FavoriteMenuItem** - User's favorite menu items
- **FavoriteCategory** - User-defined favorite categories

### **Security Classes**
- **AuthenticationManager** - Handles user authentication
- **PasswordResetManager** - Manages password reset process
- **SecurityToken** - Security tokens for authentication
- **SpamDetector** - Detects and prevents spam content

### **Search Classes**
- **SearchManager** - Coordinates search operations
- **SearchStrategy** - Abstract search strategy
- **LocationSearchStrategy** - Location-based search
- **CuisineSearchStrategy** - Cuisine-based search
- **PriceSearchStrategy** - Price-based search

### **Notification Classes**
- **NotificationManager** - Manages all notifications
- **EmailNotification** - Email notification service
- **SMSNotification** - SMS notification service
- **PushNotification** - Push notification service

### **Factory Classes**
- **UserFactory** - Creates different user types
- **MenuItemFactory** - Creates different menu item types
- **NotificationFactory** - Creates different notification types

### **Observer Classes**
- **MenuObserver** - Observes menu changes
- **UserObserver** - Observes user activity
- **SecurityObserver** - Observes security events

### **Controller Classes**
- **MenuController** - Handles menu-related requests
- **UserController** - Handles user-related requests
- **SearchController** - Handles search requests
- **SecurityController** - Handles security-related requests

### **Data Access Classes**
- **DatabaseManager** - Manages database connections
- **UserRepository** - User data access
- **MenuRepository** - Menu data access
- **FavoritesRepository** - Favorites data access

---

## Class Relationships

### **Inheritance Relationships**
```
User
├── RegularUser
├── PremiumUser
├── RestaurantOwner
└── Admin

SearchStrategy
├── LocationSearchStrategy
├── CuisineSearchStrategy
└── PriceSearchStrategy

NotificationService
├── EmailNotification
├── SMSNotification
└── PushNotification
```

### **Composition Relationships**
```
Restaurant
├── Menu
│   └── MenuItem
│       └── Category

User
├── FavoritesManager
│   ├── FavoriteRestaurant
│   └── FavoriteMenuItem

MenuController
├── MenuManager
├── SearchManager
└── FavoritesManager
```

### **Association Relationships**
```
User ↔ Restaurant (reviews)
User ↔ MenuItem (favorites)
Restaurant ↔ Menu (contains)
Menu ↔ MenuItem (contains)
```

---

## Design Pattern Identification

### **Observer Pattern**
- **Subject**: MenuManager, UserManager, SecurityManager
- **Observer**: MenuObserver, UserObserver, SecurityObserver
- **Purpose**: Real-time updates and notifications

### **Factory Pattern**
- **Factory**: UserFactory, MenuItemFactory, NotificationFactory
- **Product**: User, MenuItem, NotificationService
- **Purpose**: Object creation without specifying exact classes

### **Strategy Pattern**
- **Context**: SearchManager
- **Strategy**: SearchStrategy (Location, Cuisine, Price)
- **Purpose**: Interchangeable search algorithms

---

## Class Responsibilities

### **User Classes**
- **User**: Base user functionality and common attributes
- **RegularUser**: Standard user features and limitations
- **PremiumUser**: Enhanced features and unlimited access
- **RestaurantOwner**: Restaurant management capabilities
- **Admin**: System administration and moderation

### **Menu Classes**
- **Restaurant**: Restaurant information and location data
- **Menu**: Menu structure and organization
- **MenuItem**: Individual food/beverage items with details
- **Category**: Menu organization and classification
- **Review**: User feedback and rating system

### **Management Classes**
- **FavoritesManager**: User favorites organization and access
- **AuthenticationManager**: User login and session management
- **SearchManager**: Search coordination and result processing
- **NotificationManager**: Multi-channel notification delivery

### **Security Classes**
- **PasswordResetManager**: Secure password reset process
- **SecurityToken**: Authentication and authorization tokens
- **SpamDetector**: Content validation and spam prevention

---

## Security Considerations

### **Authentication Flow**
1. User → AuthenticationManager → SecurityToken
2. SecurityToken → User → Authorized Access
3. PasswordResetManager → SecurityToken → User

### **Data Protection**
- All user data encrypted
- Secure token generation
- Audit logging for all operations
- Role-based access control

---

## Class Diagram Benefits

### **Maintainability**
- Clear separation of concerns
- Easy to modify individual classes
- Well-defined interfaces

### **Scalability**
- Modular design allows independent scaling
- Factory pattern enables easy extension
- Observer pattern supports dynamic features

### **Testability**
- Each class has single responsibility
- Dependencies are clearly defined
- Mock objects easy to create

---

*This minimal class diagram provides the foundation for MenuMap's detailed class design and implementation.*
