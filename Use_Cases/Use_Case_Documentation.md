# MenuMap Use Case Documentation
## CEN4010 Software Engineering - Team 9

**Project:** MenuMap Application  
**Team:** Team 9  
**Document Author:** Andre Lewis  
**Date:** [Current Date]  
**Version:** 1.0  

---

## 📋 Use Case Overview

This document contains three detailed use cases for the MenuMap application as required for the CEN4010 Software Engineering course:

1. **UC-001: Browse Restaurant Menus** (Normal Use Case)
2. **UC-002: Manage Favorites** (Normal Use Case)  
3. **UC-003: Secure Password Reset** (Security Use Case)

Each use case includes detailed descriptions, actors, preconditions, main flow, alternative flows, and postconditions.

---

## 🍽️ UC-001: Browse Restaurant Menus

### Use Case Information
- **Use Case ID**: UC-001
- **Use Case Name**: Browse Restaurant Menus
- **Type**: Normal Use Case
- **Priority**: High
- **Complexity**: Medium

### Description
This use case describes how a user browses and searches for restaurant menus within the MenuMap application. The user can search by location, cuisine type, restaurant name, or specific menu items.

### Actors
- **Primary Actor**: User (Food enthusiast, restaurant customer)
- **Secondary Actor**: Restaurant Owner (provides menu data)
- **System**: MenuMap Application

### Preconditions
1. User has access to the MenuMap application
2. User is connected to the internet
3. Restaurant menu data is available in the system
4. User has a valid session (if logged in)

### Main Flow
1. User opens the MenuMap application
2. System displays the main search interface
3. User enters search criteria (location, cuisine, restaurant name, or menu item)
4. System validates the search input
5. System queries the database for matching restaurants and menus
6. System displays search results with restaurant information
7. User selects a restaurant from the results
8. System displays the restaurant's detailed menu
9. User browses through menu categories and items
10. User can view detailed information for specific menu items
11. System displays menu item details (description, price, ingredients, etc.)
12. Use case ends successfully

### Alternative Flows

#### A1: No Search Results Found
- **A1.1**: If no restaurants match the search criteria, system displays "No results found" message
- **A1.2**: System suggests alternative search terms or nearby locations
- **A1.3**: User can modify search criteria and try again
- **A1.4**: Flow returns to step 3

#### A2: User Not Logged In
- **A2.1**: If user is not logged in, system displays limited menu information
- **A2.2**: System prompts user to log in for full access to features
- **A2.3**: User can continue browsing or choose to log in
- **A2.4**: Flow continues from step 6

#### A3: Menu Data Unavailable
- **A3.1**: If menu data is temporarily unavailable, system displays error message
- **A3.2**: System suggests trying again later
- **A3.3**: Use case ends with error

### Postconditions
1. User has successfully browsed restaurant menus
2. Search results are displayed and accessible
3. User session is maintained (if logged in)
4. System logs user browsing activity for analytics

### Business Rules
- Search results are limited to 50 restaurants per page
- Menu information is updated daily from restaurant sources
- Users can access basic menu information without registration
- Full features require user registration and login

### Non-Functional Requirements
- Search results must be displayed within 3 seconds
- System must support 1000+ concurrent users browsing
- Menu data must be accurate and up-to-date
- Interface must be responsive on mobile and desktop devices

---

## ⭐ UC-002: Manage Favorites

### Use Case Information
- **Use Case ID**: UC-002
- **Use Case Name**: Manage Favorites
- **Type**: Normal Use Case
- **Priority**: High
- **Complexity**: Medium

### Description
This use case describes how a registered user manages their favorite restaurants and menu items within the MenuMap application. Users can add, remove, organize, and access their saved favorites.

### Actors
- **Primary Actor**: Registered User
- **Secondary Actor**: System (MenuMap Application)

### Preconditions
1. User is registered and logged into the MenuMap application
2. User has a valid user account with favorites storage capability
3. Restaurant and menu data is available in the system
4. User has previously browsed restaurants or menu items

### Main Flow
1. User logs into their MenuMap account
2. System displays the user's dashboard
3. User navigates to the "My Favorites" section
4. System displays the user's current favorites organized by category
5. User can perform one of the following actions:
   - **Add to Favorites**: User selects a restaurant or menu item and clicks "Add to Favorites"
   - **Remove from Favorites**: User selects a favorite item and clicks "Remove"
   - **Organize Favorites**: User creates custom categories or moves items between categories
   - **View Favorites**: User browses through their saved favorites
6. System processes the user's action
7. System updates the user's favorites list
8. System displays confirmation of the action
9. User can continue managing favorites or navigate to other sections
10. Use case ends successfully

### Alternative Flows

#### A1: Adding Restaurant to Favorites
- **A1.1**: User is browsing a restaurant's menu
- **A1.2**: User clicks "Add Restaurant to Favorites" button
- **A1.3**: System adds the restaurant to user's favorites
- **A1.4**: System displays "Restaurant added to favorites" confirmation
- **A1.5**: Flow continues from step 9

#### A2: Adding Menu Item to Favorites
- **A2.1**: User is viewing a specific menu item
- **A2.2**: User clicks "Add Item to Favorites" button
- **A2.3**: System prompts user to select a category for the item
- **A2.4**: User selects or creates a category
- **A2.5**: System adds the menu item to the specified category
- **A2.6**: System displays "Menu item added to favorites" confirmation
- **A2.7**: Flow continues from step 9

#### A3: Organizing Favorites
- **A3.1**: User clicks "Organize Favorites" option
- **A3.2**: System displays drag-and-drop interface for organizing
- **A3.3**: User creates new categories or moves items between categories
- **A3.4**: System saves the new organization
- **A3.5**: System displays "Favorites organized" confirmation
- **A3.6**: Flow continues from step 9

#### A4: Favorites Storage Limit Reached
- **A4.1**: If user tries to add more than 100 favorites, system displays limit message
- **A4.2**: System suggests removing old favorites or upgrading account
- **A4.3**: User can remove existing favorites or cancel the action
- **A4.4**: Flow returns to step 5

### Postconditions
1. User's favorites list is updated according to their actions
2. Favorites are properly organized and categorized
3. User can access their favorites from any device
4. System maintains favorites data consistency

### Business Rules
- Users can have up to 100 favorites (free account)
- Premium users can have unlimited favorites
- Favorites are synchronized across all user devices
- Deleted favorites are moved to a "Recently Deleted" section for 30 days

### Non-Functional Requirements
- Favorites must be saved and retrieved within 2 seconds
- Favorites must be available offline (cached)
- System must support real-time synchronization across devices
- Favorites data must be backed up daily

---

## 🔒 UC-003: Secure Password Reset

### Use Case Information
- **Use Case ID**: UC-003
- **Use Case Name**: Secure Password Reset
- **Type**: Security Use Case (Misuse Case Prevention)
- **Priority**: High
- **Complexity**: High

### Description
This use case describes the secure password reset functionality that prevents unauthorized access to user accounts. It addresses the misuse case of account takeover through password reset attacks by implementing multiple security layers and verification steps.

### Actors
- **Primary Actor**: User (Account owner)
- **Secondary Actor**: System (MenuMap Application)
- **External Actor**: Email Service Provider

### Preconditions
1. User has a registered account in the MenuMap system
2. User has access to their registered email address
3. System has email service configured and operational
4. User is not currently logged into their account

### Main Flow
1. User navigates to the login page
2. User clicks "Forgot Password" link
3. System displays the password reset request form
4. User enters their registered email address
5. System validates the email format and existence
6. System checks if the email is associated with an active account
7. System generates a secure, time-limited reset token
8. System sends a password reset email to the user's registered address
9. System displays confirmation message (without revealing email address)
10. User receives the password reset email
11. User clicks the secure reset link in the email
12. System validates the reset token and checks expiration
13. System displays the new password entry form
14. User enters a new password meeting security requirements
15. System validates password strength and complexity
16. User confirms the new password
17. System encrypts and stores the new password
18. System invalidates the reset token
19. System logs the password reset event
20. System sends confirmation email to user
21. System displays success message and redirects to login
22. Use case ends successfully

### Alternative Flows

#### A1: Invalid Email Address
- **A1.1**: If email format is invalid, system displays error message
- **A1.2**: User corrects the email address
- **A1.3**: Flow returns to step 4

#### A2: Email Not Found
- **A2.1**: If email is not associated with any account, system displays generic message
- **A2.2**: System does not reveal whether the email exists in the system
- **A2.3**: System logs the failed attempt for security monitoring
- **A2.4**: Use case ends (security measure to prevent email enumeration)

#### A3: Reset Token Expired
- **A3.1**: If user clicks reset link after token expiration (24 hours), system displays error
- **A3.2**: System prompts user to request a new password reset
- **A3.3**: Flow returns to step 1

#### A4: Invalid Reset Token
- **A4.1**: If reset token is invalid or tampered with, system displays error
- **A4.2**: System logs the suspicious activity
- **A4.3**: System may temporarily lock the account for security
- **A4.4**: Use case ends with security alert

#### A5: Password Does Not Meet Requirements
- **A5.1**: If new password doesn't meet complexity requirements, system displays error
- **A5.2**: System shows password requirements (length, characters, etc.)
- **A5.3**: User enters a compliant password
- **A5.4**: Flow continues from step 15

#### A6: Rate Limiting Triggered
- **A6.1**: If user exceeds reset request limit (5 per hour), system displays rate limit message
- **A6.2**: System temporarily blocks further reset requests
- **A6.3**: User must wait before requesting another reset
- **A6.4**: Use case ends with rate limit notification

### Security Measures (Misuse Case Prevention)

#### Fraud Prevention
- **Email Verification**: Reset links only work with registered email addresses
- **Token Security**: Reset tokens are cryptographically secure and time-limited
- **Rate Limiting**: Prevents brute force attacks on password reset
- **Account Lockout**: Suspicious activity triggers temporary account lockout

#### Abuse Prevention
- **No Email Enumeration**: System doesn't reveal if email exists in database
- **Audit Logging**: All reset attempts are logged for security monitoring
- **Token Invalidation**: Used tokens are immediately invalidated
- **Secure Communication**: All reset communications use HTTPS encryption

#### Data Protection
- **Password Encryption**: New passwords are encrypted before storage
- **Session Invalidation**: All existing sessions are invalidated after reset
- **Confirmation Notifications**: User is notified of password changes via email

### Postconditions
1. User's password is successfully updated
2. All existing user sessions are invalidated
3. Reset token is permanently invalidated
4. Security audit log is updated
5. User receives confirmation of password change
6. User can log in with new password

### Business Rules
- Reset tokens expire after 24 hours
- Users can request maximum 5 password resets per hour
- Password must meet minimum complexity requirements
- All password changes trigger security notifications
- Suspicious reset attempts are flagged for review

### Non-Functional Requirements
- Reset emails must be delivered within 5 minutes
- Password reset process must complete within 10 minutes
- System must handle 100+ concurrent reset requests
- All security events must be logged in real-time
- System must be available 99.9% of the time

### Security Compliance
- **OWASP Guidelines**: Follows OWASP password reset best practices
- **GDPR Compliance**: Handles personal data according to privacy regulations
- **Encryption Standards**: Uses industry-standard encryption algorithms
- **Audit Requirements**: Maintains comprehensive security audit trails

---

## 📊 Use Case Summary

| Use Case ID | Name | Type | Priority | Complexity | Security Level |
|-------------|------|------|----------|------------|----------------|
| UC-001 | Browse Restaurant Menus | Normal | High | Medium | Standard |
| UC-002 | Manage Favorites | Normal | High | Medium | Standard |
| UC-003 | Secure Password Reset | Security | High | High | Enhanced |

---

## 🔗 Related Documentation

- **Software Requirements Document (SRD)**: Detailed functional and non-functional requirements
- **UML Diagrams**: Visual representations of use cases and system interactions
- **Security Specifications**: Detailed security implementation guidelines
- **User Interface Mockups**: Visual design for use case interactions

---

*This document provides comprehensive use case documentation for the MenuMap application. Each use case includes detailed flows, security considerations, and business rules to ensure proper system implementation and user experience.*
