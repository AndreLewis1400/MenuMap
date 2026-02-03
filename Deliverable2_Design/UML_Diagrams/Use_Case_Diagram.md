# MenuMap Use Case Diagram
## CEN4010 Software Engineering - Team 9

**Author:** Andre Lewis (Software Architecture & Design Lead)  
**Date:** [Current Date]  
**Version:** 1.0  

---

## Use Case Diagram Overview

This document defines the comprehensive use case diagram for the MenuMap application, covering all 7 selected use cases for implementation. The use cases are categorized into Normal Use Cases and Security Use Cases, with detailed actor definitions and relationships.

---

## Actors Definition

### **Primary Actors**
```
User Types:
├── Guest User
│   ├── Description: Unregistered user browsing the application
│   ├── Permissions: Limited browsing, no personalization
│   ├── Goals: Explore restaurants and menus
│   └── Use Cases: UC-001 (Browse Restaurant Menus)
├── Registered User
│   ├── Description: Authenticated user with account
│   ├── Permissions: Full browsing, favorites, reviews
│   ├── Goals: Personalized restaurant discovery
│   └── Use Cases: UC-001, UC-002, UC-004
├── Premium User
│   ├── Description: Paid subscriber with enhanced features
│   ├── Permissions: Advanced search, priority support
│   ├── Goals: Enhanced restaurant discovery experience
│   └── Use Cases: UC-001, UC-002, UC-004
├── Restaurant Owner
│   ├── Description: Business owner managing restaurant data
│   ├── Permissions: Menu management, analytics, reviews
│   ├── Goals: Manage restaurant presence and menu data
│   └── Use Cases: UC-001, UC-004, UC-007
└── System Administrator
    ├── Description: Technical administrator managing system
    ├── Permissions: Full system access, user management
    ├── Goals: System maintenance and user support
    └── Use Cases: All use cases (administrative access)
```

### **Secondary Actors**
```
External Systems:
├── Email Service
│   ├── Description: External email delivery service
│   ├── Purpose: Send notifications and confirmations
│   └── Use Cases: UC-003, UC-004
├── SMS Service
│   ├── Description: External SMS delivery service
│   ├── Purpose: Send OTP and notifications
│   └── Use Cases: UC-003, UC-004
├── Payment Gateway
│   ├── Description: External payment processing service
│   ├── Purpose: Process subscription payments
│   └── Use Cases: UC-004 (Premium subscription)
├── Map Service
│   ├── Description: External mapping and geolocation service
│   ├── Purpose: Provide location-based services
│   └── Use Cases: UC-001, UC-007
└── Social Media Platform
    ├── Description: External social media integration
    ├── Purpose: Social login and sharing
    └── Use Cases: UC-004, UC-002
```

---

## Use Cases Specification

### **UC-001: Browse Restaurant Menus**
```
Use Case ID: UC-001
Use Case Name: Browse Restaurant Menus
Actor: Guest User, Registered User, Premium User, Restaurant Owner
Type: Normal Use Case
Priority: High
Description: Users can browse and search restaurant menus with various filtering options

Preconditions:
- User has access to the application
- Restaurant and menu data is available in the system

Main Flow:
1. User opens the application
2. System displays available restaurants
3. User can search by location, cuisine, or restaurant name
4. User selects a restaurant
5. System displays restaurant details and menu
6. User can filter menu items by category, price, or dietary restrictions
7. User can view detailed information about menu items
8. System displays menu items with prices and descriptions

Alternative Flows:
- 3a. User uses advanced search filters (Premium Users only)
- 4a. User views restaurant on map
- 6a. User sorts menu items by price or popularity
- 7a. User views nutritional information (if available)

Postconditions:
- User has viewed restaurant menu information
- System has logged user interaction for analytics

Exceptions:
- E1: No restaurants found - System displays "No results found" message
- E2: Network error - System displays error message and retry option
- E3: Restaurant data unavailable - System displays "Menu temporarily unavailable" message
```

### **UC-002: Manage Favorites**
```
Use Case ID: UC-002
Use Case Name: Manage Favorites
Actor: Registered User, Premium User
Type: Normal Use Case
Priority: High
Description: Users can add, remove, and organize their favorite restaurants and menu items

Preconditions:
- User is authenticated
- User has access to favorites functionality

Main Flow:
1. User browses restaurants or menu items
2. User clicks "Add to Favorites" button
3. System adds item to user's favorites list
4. User can view their favorites list
5. User can organize favorites into categories
6. User can remove items from favorites
7. User can share favorites with other users

Alternative Flows:
- 2a. User adds restaurant to favorites
- 2b. User adds specific menu item to favorites
- 5a. User creates custom favorite categories
- 6a. User removes multiple items at once
- 7a. User exports favorites list

Postconditions:
- User's favorites list is updated
- System has recorded the favorite action

Exceptions:
- E1: User not authenticated - System redirects to login
- E2: Item already in favorites - System displays confirmation message
- E3: Favorites limit reached - System displays upgrade option
```

### **UC-003: Secure Password Reset**
```
Use Case ID: UC-003
Use Case Name: Secure Password Reset
Actor: Registered User, Premium User, Restaurant Owner
Type: Security Use Case
Priority: High
Description: Users can securely reset their password through email or SMS verification

Preconditions:
- User has a registered account
- User has access to registered email or phone number

Main Flow:
1. User clicks "Forgot Password" link
2. System displays password reset form
3. User enters email address or phone number
4. System validates the input
5. System sends verification code via email or SMS
6. User enters verification code
7. System validates the code
8. User enters new password
9. System validates password strength
10. System updates user password
11. System sends confirmation email
12. User can log in with new password

Alternative Flows:
- 3a. User enters phone number for SMS verification
- 5a. User requests code resend
- 7a. Code expires - User requests new code
- 9a. Password doesn't meet requirements - System displays requirements

Postconditions:
- User password is updated
- User is logged out of all sessions
- System has logged the password reset event

Exceptions:
- E1: Email/phone not found - System displays error message
- E2: Invalid verification code - System allows retry
- E3: Code expired - System requires new code request
- E4: Account locked - System displays account lockout message
```

### **UC-004: User Registration & Login**
```
Use Case ID: UC-004
Use Case Name: User Registration & Login
Actor: Guest User, Registered User, Premium User, Restaurant Owner
Type: Normal Use Case
Priority: High
Description: Users can register new accounts and log into existing accounts

Preconditions:
- User has access to the application
- System is operational

Main Flow (Registration):
1. User clicks "Register" button
2. System displays registration form
3. User enters personal information (name, email, password)
4. System validates input data
5. User agrees to terms and conditions
6. System creates user account
7. System sends email verification
8. User clicks verification link
9. System activates account
10. User can log in

Main Flow (Login):
1. User enters email and password
2. System validates credentials
3. System checks for MFA requirement
4. User completes MFA if required
5. System creates user session
6. System redirects user to dashboard

Alternative Flows:
- 3a. User registers as Restaurant Owner
- 4a. User chooses social media login
- 7a. User upgrades to Premium subscription
- 8a. User skips email verification (limited access)

Postconditions:
- User account is created or user is logged in
- User session is established
- System has logged the authentication event

Exceptions:
- E1: Email already exists - System displays error message
- E2: Invalid credentials - System displays error message
- E3: Account not verified - System prompts for verification
- E4: Account locked - System displays lockout message
```

### **UC-005: Menu Verification System**
```
Use Case ID: UC-005
Use Case Name: Menu Verification System
Actor: Restaurant Owner, System Administrator
Type: Security Use Case
Priority: Medium
Description: System verifies menu accuracy and authenticity to prevent fraud

Preconditions:
- Restaurant Owner has submitted menu data
- System has verification rules configured

Main Flow:
1. Restaurant Owner submits menu update
2. System analyzes menu content
3. System checks for suspicious patterns
4. System compares with existing data
5. System applies verification rules
6. System determines verification status
7. System notifies Restaurant Owner of status
8. System Administrator reviews flagged items
9. System Administrator approves or rejects changes

Alternative Flows:
- 2a. System detects potential spam content
- 3a. System identifies duplicate content
- 6a. Menu requires manual review
- 8a. System Administrator requests additional information

Postconditions:
- Menu verification status is determined
- Restaurant Owner is notified of status
- System has logged verification events

Exceptions:
- E1: Verification system unavailable - System queues for later processing
- E2: Invalid menu data - System rejects submission
- E3: Verification timeout - System escalates to manual review
```

### **UC-006: Spam Protection System**
```
Use Case ID: UC-006
Use Case Name: Spam Protection System
Actor: System Administrator
Type: Security Use Case
Priority: Medium
Description: System automatically detects and prevents spam content and malicious activities

Preconditions:
- System has spam detection rules configured
- User is attempting to submit content

Main Flow:
1. User submits content (review, menu update, etc.)
2. System analyzes content for spam indicators
3. System checks user behavior patterns
4. System applies spam detection algorithms
5. System determines spam probability
6. System takes appropriate action (allow, flag, block)
7. System logs the detection event
8. System Administrator reviews flagged content

Alternative Flows:
- 2a. System detects suspicious keywords
- 3a. System identifies unusual user behavior
- 5a. Content requires manual review
- 6a. System blocks user temporarily

Postconditions:
- Content is processed according to spam detection results
- System has logged spam detection events
- User is notified of any restrictions

Exceptions:
- E1: Spam detection system unavailable - System allows content with manual review
- E2: False positive detection - System Administrator can override
- E3: Detection timeout - System escalates to manual review
```

### **UC-007: Restaurant Owner Menu Management**
```
Use Case ID: UC-007
Use Case Name: Restaurant Owner Menu Management
Actor: Restaurant Owner, System Administrator
Type: Normal Use Case
Priority: High
Description: Restaurant owners can manage their restaurant information and menu data

Preconditions:
- User is authenticated as Restaurant Owner
- Restaurant account is verified

Main Flow:
1. Restaurant Owner logs into management dashboard
2. System displays restaurant management interface
3. Restaurant Owner selects menu management
4. System displays current menu data
5. Restaurant Owner can add, edit, or remove menu items
6. Restaurant Owner can update restaurant information
7. System validates changes
8. System applies verification rules
9. System saves changes
10. System notifies Restaurant Owner of status

Alternative Flows:
- 3a. Restaurant Owner manages restaurant profile
- 5a. Restaurant Owner bulk imports menu data
- 6a. Restaurant Owner updates business hours
- 8a. Changes require verification approval

Postconditions:
- Restaurant data is updated
- Menu changes are processed
- System has logged management activities

Exceptions:
- E1: User not authorized - System denies access
- E2: Invalid data format - System displays error message
- E3: Verification failed - System requires manual review
- E4: System unavailable - System displays maintenance message
```

---

## Use Case Relationships

### **Include Relationships**
```
UC-001 (Browse Restaurant Menus) includes:
├── UC-004 (User Registration & Login) - For personalized features
├── UC-002 (Manage Favorites) - For adding favorites
└── UC-007 (Restaurant Owner Menu Management) - For menu data

UC-002 (Manage Favorites) includes:
├── UC-004 (User Registration & Login) - For authentication
└── UC-001 (Browse Restaurant Menus) - For browsing items

UC-003 (Secure Password Reset) includes:
├── UC-004 (User Registration & Login) - For account verification
└── Email/SMS Service - For verification delivery

UC-004 (User Registration & Login) includes:
├── Email Service - For verification emails
├── SMS Service - For OTP delivery
└── Payment Gateway - For premium subscriptions

UC-005 (Menu Verification System) includes:
├── UC-006 (Spam Protection System) - For content analysis
└── UC-007 (Restaurant Owner Menu Management) - For menu data

UC-006 (Spam Protection System) includes:
├── UC-001 (Browse Restaurant Menus) - For content analysis
├── UC-002 (Manage Favorites) - For user behavior analysis
└── UC-007 (Restaurant Owner Menu Management) - For content analysis

UC-007 (Restaurant Owner Menu Management) includes:
├── UC-004 (User Registration & Login) - For authentication
├── UC-005 (Menu Verification System) - For content verification
└── UC-006 (Spam Protection System) - For spam detection
```

### **Extend Relationships**
```
UC-001 (Browse Restaurant Menus) extends:
├── UC-002 (Manage Favorites) - When user adds to favorites
└── UC-004 (User Registration & Login) - When user needs to log in

UC-002 (Manage Favorites) extends:
├── UC-001 (Browse Restaurant Menus) - When browsing from favorites
└── UC-004 (User Registration & Login) - When authentication required

UC-003 (Secure Password Reset) extends:
├── UC-004 (User Registration & Login) - When login fails
└── UC-006 (Spam Protection System) - When suspicious activity detected

UC-004 (User Registration & Login) extends:
├── UC-003 (Secure Password Reset) - When password reset needed
└── UC-006 (Spam Protection System) - When suspicious login detected

UC-005 (Menu Verification System) extends:
├── UC-006 (Spam Protection System) - When spam detected
└── UC-007 (Restaurant Owner Menu Management) - When verification required

UC-006 (Spam Protection System) extends:
├── UC-001 (Browse Restaurant Menus) - When spam content detected
├── UC-002 (Manage Favorites) - When suspicious user behavior
├── UC-003 (Secure Password Reset) - When suspicious reset attempts
├── UC-004 (User Registration & Login) - When suspicious registration/login
├── UC-005 (Menu Verification System) - When spam content detected
└── UC-007 (Restaurant Owner Menu Management) - When spam content detected

UC-007 (Restaurant Owner Menu Management) extends:
├── UC-005 (Menu Verification System) - When menu changes made
└── UC-006 (Spam Protection System) - When spam content detected
```

### **Generalization Relationships**
```
Actor Generalizations:
├── Registered User generalizes Premium User
├── Registered User generalizes Restaurant Owner
├── User generalizes Registered User
└── User generalizes Guest User

Use Case Generalizations:
├── UC-004 (User Registration & Login) generalizes UC-003 (Secure Password Reset)
└── UC-001 (Browse Restaurant Menus) generalizes UC-002 (Manage Favorites)
```

---

## Use Case Priority Matrix

### **Priority Classification**
```
High Priority (Must Have):
├── UC-001: Browse Restaurant Menus
├── UC-002: Manage Favorites
├── UC-003: Secure Password Reset
├── UC-004: User Registration & Login
└── UC-007: Restaurant Owner Menu Management

Medium Priority (Should Have):
├── UC-005: Menu Verification System
└── UC-006: Spam Protection System

Low Priority (Could Have):
├── Advanced Search Features
├── Social Media Integration
├── Mobile App Features
└── Analytics Dashboard
```

### **Implementation Phases**
```
Phase 1 (Core Features):
├── UC-001: Browse Restaurant Menus
├── UC-004: User Registration & Login
└── UC-007: Restaurant Owner Menu Management

Phase 2 (User Features):
├── UC-002: Manage Favorites
└── UC-003: Secure Password Reset

Phase 3 (Security Features):
├── UC-005: Menu Verification System
└── UC-006: Spam Protection System
```

---

## Use Case Success Criteria

### **Functional Requirements**
```
UC-001 Success Criteria:
├── User can search restaurants by location, cuisine, name
├── User can view detailed menu information
├── System responds within 2 seconds
└── 99.9% uptime for menu browsing

UC-002 Success Criteria:
├── User can add/remove favorites
├── User can organize favorites into categories
├── Favorites sync across devices
└── 100% data consistency for favorites

UC-003 Success Criteria:
├── Password reset completed within 5 minutes
├── 99.9% email/SMS delivery success rate
├── Secure verification process
└── Account lockout after 5 failed attempts

UC-004 Success Criteria:
├── Registration completed within 2 minutes
├── Login completed within 5 seconds
├── 99.9% authentication success rate
└── Secure session management

UC-005 Success Criteria:
├── 95% automated verification accuracy
├── Manual review within 24 hours
├── 99.9% verification system uptime
└── Zero false positives for critical items

UC-006 Success Criteria:
├── 99% spam detection accuracy
├── False positive rate < 1%
├── Real-time spam detection
└── 100% malicious content blocking

UC-007 Success Criteria:
├── Menu updates processed within 1 hour
├── 99.9% data integrity for menu changes
├── Real-time menu updates
└── 100% authorized access control
```

### **Non-Functional Requirements**
```
Performance Requirements:
├── Response Time: < 2 seconds for all operations
├── Throughput: 1000+ concurrent users
├── Availability: 99.9% uptime
└── Scalability: Auto-scaling to 10,000+ users

Security Requirements:
├── Authentication: Multi-factor authentication
├── Authorization: Role-based access control
├── Data Protection: AES-256 encryption
└── Compliance: GDPR/CCPA compliance

Usability Requirements:
├── User Interface: Intuitive and responsive
├── Accessibility: WCAG 2.1 AA compliance
├── Mobile Support: iOS and Android apps
└── Browser Support: Chrome, Firefox, Safari, Edge
```

---

*This use case diagram provides the comprehensive foundation for MenuMap's functional requirements and system design.*
