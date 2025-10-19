# UC-003: Secure Password Reset - Sequence Diagram Quick Reference
## MenuMap Application - Team 9

**Use Case:** UC-003: Secure Password Reset  
**Complexity:** High  
**Priority:** Start with this one for practice  

---

## 🎯 **Lifelines (Participants)**

```
User | WebInterface | AuthenticationService | EmailService | Database | SecurityLogger
```

---

## 📋 **Message Flow (Step by Step)**

### **Phase 1: Password Reset Request**
```
1. User -> WebInterface: click "Forgot Password"
2. WebInterface -> User: display reset form
3. User -> WebInterface: enter email address
4. WebInterface -> AuthenticationService: requestPasswordReset(email)
5. AuthenticationService -> Database: checkUserExists(email)
6. Database -> AuthenticationService: return userExists
```

### **Phase 2: Token Generation & Email**
```
7. AuthenticationService -> AuthenticationService: generateResetToken()
8. AuthenticationService -> Database: saveResetToken(userID, token)
9. AuthenticationService -> EmailService: sendResetEmail(email, token)
10. EmailService -> User: deliver reset email
11. AuthenticationService -> WebInterface: return success message
12. WebInterface -> User: display "Check your email"
```

### **Phase 3: Password Reset Execution**
```
13. User -> WebInterface: click reset link
14. WebInterface -> AuthenticationService: validateResetToken(token)
15. AuthenticationService -> Database: verifyToken(token)
16. Database -> AuthenticationService: return tokenValid
17. User -> WebInterface: enter new password
18. WebInterface -> AuthenticationService: resetPassword(token, newPassword)
19. AuthenticationService -> Database: updatePassword(userID, newPassword)
20. AuthenticationService -> Database: invalidateToken(token)
21. AuthenticationService -> SecurityLogger: logPasswordReset(userID)
22. AuthenticationService -> WebInterface: return success
23. WebInterface -> User: display "Password reset successful"
```

---

## 🔄 **Alternative Flows (Alt Frames)**

### **Alt Frame 1: Email Not Found**
```
alt Email Not Found
    Database -> AuthenticationService: return false
    AuthenticationService -> WebInterface: return genericMessage
    WebInterface -> User: display "Check your email" (same message for security)
```

### **Alt Frame 2: Token Expired**
```
alt Token Expired
    Database -> AuthenticationService: return tokenExpired
    AuthenticationService -> WebInterface: return tokenExpired
    WebInterface -> User: display "Token expired, request new reset"
```

### **Alt Frame 3: Invalid Token**
```
alt Invalid Token
    Database -> AuthenticationService: return invalidToken
    AuthenticationService -> SecurityLogger: logSuspiciousActivity(token)
    AuthenticationService -> WebInterface: return securityError
    WebInterface -> User: display "Invalid reset link"
```

---

## 🎨 **Visual Layout in Papyrus**

### **Lifeline Order (Left to Right):**
```
User | WebInterface | AuthenticationService | EmailService | Database | SecurityLogger
```

### **Message Types:**
- **Solid Arrow**: Synchronous calls
- **Dashed Arrow**: Return messages
- **Self Arrow**: Internal method calls (steps 7, 21)

### **Activation Boxes:**
- **WebInterface**: Steps 1-3, 13, 17, 23
- **AuthenticationService**: Steps 4-11, 14-22
- **EmailService**: Steps 9-10
- **Database**: Steps 5-6, 8, 15-16, 19-20
- **SecurityLogger**: Step 21

---

## 🔧 **Papyrus Implementation Tips**

### **Step 1: Create Lifelines**
1. Drag "Lifeline" from palette
2. Name each lifeline
3. Space evenly across diagram

### **Step 2: Add Messages**
1. Use "Message" tool
2. Click from source to target lifeline
3. Label with step number and method name

### **Step 3: Add Self Messages**
1. Use "Self Message" tool
2. Click on AuthenticationService lifeline
3. Label as "generateResetToken()" and "logPasswordReset()"

### **Step 4: Add Alt Frames**
1. Use "Interaction Use" tool
2. Draw rectangle around alternative flow
3. Label as "alt [condition]"

### **Step 5: Add Activation Boxes**
1. Right-click on each message
2. Check "Activation" in properties
3. Adjust length to show execution duration

---

## ✅ **Validation Checklist**

- [ ] All 6 lifelines created
- [ ] 23 main flow messages added
- [ ] 3 alternative flows (alt frames) included
- [ ] Self messages for internal calls
- [ ] Activation boxes showing method execution
- [ ] Return messages as dashed arrows
- [ ] Professional formatting applied
- [ ] No syntax errors in validation

---

## 🎯 **Why Start with UC-003?**

1. **Most Complex**: Good practice for advanced features
2. **Security Focus**: Important for understanding security flows
3. **Multiple Actors**: Practice with external services
4. **Alternative Flows**: Learn alt frame implementation
5. **Self Messages**: Practice internal method calls

---

*This quick reference provides everything needed to implement UC-003 sequence diagram in Papyrus. Once mastered, the other 6 diagrams will be much easier to create.*
