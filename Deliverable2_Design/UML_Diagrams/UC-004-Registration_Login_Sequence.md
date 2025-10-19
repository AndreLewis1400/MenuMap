# UC-004: Registration & Login - Sequence Diagram
## MenuMap Application - Team 9

**Use Case:** UC-004: Registration & Login  
**Complexity:** Medium  
**Priority:** Core authentication functionality  

---

## 🎯 **Lifelines (Participants)**

```
User | WebInterface | AuthenticationService | UserController | Database | EmailService
```

---

## 📋 **Message Flow (Step by Step)**

### **Phase 1: User Registration**
```
1. User -> WebInterface: click "Register"
2. WebInterface -> User: display registration form
3. User -> WebInterface: submit registration data
4. WebInterface -> UserController: registerUser(userData)
5. UserController -> Database: checkUserExists(username, email)
6. Database -> UserController: return userExists

7. UserController -> AuthenticationService: hashPassword(password)
8. AuthenticationService -> UserController: return hashedPassword
9. UserController -> Database: createUser(userData, hashedPassword)
10. Database -> UserController: return userID
11. UserController -> EmailService: sendWelcomeEmail(email)
12. EmailService -> User: deliver welcome email
13. UserController -> WebInterface: return success
14. WebInterface -> User: display "Registration successful"
```

### **Phase 2: User Login**
```
15. User -> WebInterface: enter credentials
16. WebInterface -> AuthenticationService: authenticateUser(username, password)
17. AuthenticationService -> Database: getUserData(username)
18. Database -> AuthenticationService: return userData
19. AuthenticationService -> Database: verifyPassword(username, password)
20. Database -> AuthenticationService: return passwordValid

21. AuthenticationService -> AuthenticationService: generateSessionToken(userID)
22. AuthenticationService -> Database: saveSession(userID, sessionToken)
23. AuthenticationService -> WebInterface: return sessionToken
24. WebInterface -> User: display dashboard
```

---

## 🔄 **Alternative Flows (Alt Frames)**

### **Alt Frame 1: User Already Exists**
```
alt User Already Exists
    Database -> UserController: return true
    UserController -> WebInterface: return userExists
    WebInterface -> User: display "User already exists"
```

### **Alt Frame 2: Invalid Credentials**
```
alt Invalid Credentials
    Database -> AuthenticationService: return false
    AuthenticationService -> WebInterface: return authenticationFailed
    WebInterface -> User: display "Invalid credentials"
```

### **Alt Frame 3: Email Delivery Failed**
```
alt Email Delivery Failed
    EmailService -> UserController: return deliveryFailed
    UserController -> WebInterface: return emailError
    WebInterface -> User: display "Registration successful, check email"
```

---

## 🎨 **Visual Layout in Papyrus**

### **Lifeline Order (Left to Right):**
```
User | WebInterface | AuthenticationService | UserController | Database | EmailService
```

### **Message Types:**
- **Solid Arrow**: Synchronous calls
- **Dashed Arrow**: Return messages
- **Self Arrow**: Internal method calls (step 21)

### **Activation Boxes:**
- **WebInterface**: Steps 1-3, 14-16, 24
- **UserController**: Steps 4-14
- **AuthenticationService**: Steps 7-8, 16-23
- **Database**: Steps 5-6, 9-10, 17-20, 22
- **EmailService**: Steps 11-12

---

## ✅ **Validation Checklist**

- [ ] All 6 lifelines created
- [ ] 24 main flow messages added
- [ ] 3 alternative flows (alt frames) included
- [ ] Self messages for internal calls
- [ ] Activation boxes showing method execution
- [ ] Return messages as dashed arrows
- [ ] Professional formatting applied
- [ ] No syntax errors in validation

---

*This sequence diagram provides detailed interaction flow for UC-004: Registration & Login use case.*
