# UC-006: User Logout Sequence Diagram
## CEN4010 Software Engineering - Team 9

**Author:** Andre Lewis (Software Architecture & Design Lead)  
**Date:** October 19, 2025  
**Version:** 1.0

---

## 🎯 Use Case: UC-006 - User Logout

### **Use Case Description**
A logged-in user wants to securely log out of the MenuMap application and end their session.

### **Actors**
- **Primary Actor**: Logged-in User
- **Secondary Actor**: System

### **Preconditions**
- User must be logged in to the system
- User must have an active session

### **Postconditions**
- User session is terminated
- User is redirected to login page
- All user data is cleared from client-side storage

---

## 🔄 Sequence Diagram

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   WebInterface  │    │ Authentication  │    │ SecurityService │    │   Database      │
│                 │    │ Controller      │    │                 │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │                       │
         │ 1. User clicks        │                       │                       │
         │    "Logout" button    │                       │                       │
         ├──────────────────────▶│                       │                       │
         │                       │                       │                       │
         │                       │ 2. logoutUser()      │                       │
         │                       ├──────────────────────▶│                       │
         │                       │                       │                       │
         │                       │                       │ 3. invalidateSession()│
         │                       │                       ├──────────────────────▶│
         │                       │                       │                       │
         │                       │                       │ 4. Session invalidated│
         │                       │                       │◀──────────────────────┤
         │                       │                       │                       │
         │                       │ 5. logoutSuccess()    │                       │
         │                       │◀──────────────────────┤                       │
         │                       │                       │                       │
         │ 6. redirectToLogin()   │                       │                       │
         │◀──────────────────────┤                       │                       │
         │                       │                       │                       │
         │ 7. Clear session data │                       │                       │
         │    and redirect       │                       │                       │
         │                       │                       │                       │
         │ 8. Display login page │                       │                       │
         │                       │                       │                       │
```

---

## 📋 Detailed Steps

### **Step 1: User Initiates Logout**
- User clicks the "Logout" button in the web interface
- WebInterface component captures the logout request

### **Step 2: Authentication Controller Processing**
- AuthenticationController receives the logout request
- Controller calls the logoutUser() method

### **Step 3: Security Service Session Invalidation**
- SecurityService receives the logout request
- Service calls invalidateSession() to terminate the user's session
- Session data is removed from the database

### **Step 4: Database Session Cleanup**
- Database removes the session record
- Session is marked as invalid
- Confirmation is sent back to SecurityService

### **Step 5: Security Service Response**
- SecurityService confirms successful logout
- Returns logoutSuccess() response to AuthenticationController

### **Step 6: Controller Response**
- AuthenticationController receives logout confirmation
- Controller calls redirectToLogin() to redirect user

### **Step 7: Client-Side Cleanup**
- WebInterface clears all session data from client-side storage
- User is redirected to the login page

### **Step 8: Login Page Display**
- User sees the login page
- User is no longer authenticated
- All user-specific data is cleared

---

## 🔒 Security Considerations

### **Session Management**
- **Session Invalidation**: Server-side session is completely invalidated
- **Token Revocation**: Any authentication tokens are revoked
- **Client Cleanup**: All client-side session data is cleared

### **Data Protection**
- **No Data Persistence**: User data is not persisted after logout
- **Secure Cleanup**: All sensitive data is securely removed
- **Session Timeout**: Automatic session timeout is enforced

---

## 🎯 Business Rules

### **Logout Requirements**
1. **User Authentication**: User must be authenticated to logout
2. **Session Validation**: Active session must exist
3. **Complete Cleanup**: All session data must be cleared
4. **Secure Termination**: Logout must be secure and complete

---

## 📊 Performance Considerations

### **Response Time**
- **Logout Processing**: < 200ms for logout completion
- **Session Cleanup**: < 100ms for database operations
- **Client Redirect**: < 500ms for page redirection

---

*This sequence diagram provides a complete implementation guide for the User Logout use case in the MenuMap application.*
