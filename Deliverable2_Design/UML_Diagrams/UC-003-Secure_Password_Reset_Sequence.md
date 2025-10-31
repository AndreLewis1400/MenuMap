# UC-003: Secure Password Reset Sequence Diagram

## Use Case: Secure Password Reset
**Actor:** Registered User  
**Goal:** Reset forgotten password securely  
**Precondition:** User has valid email address registered  

**3-Tier Architecture:** MM_Client → MM_Logic → MM_DataStore

---

## 🎯 **Lifelines (Participants) - 3-Tier Architecture**

```
User | PasswordResetForm | UserManager_CMD | UserDAO | EmailService | Database
```

**Tier Mapping:**
- **MM_Client (Presentation):** PasswordResetForm
- **MM_Logic (Business Logic):** UserManager_CMD, EmailService
- **MM_DataStore (Data):** UserDAO, Database

---

## Sequence Flow - Secure Password Reset

### **Phase 1: Request Password Reset**
```
User -> PasswordResetForm: Enter email address
PasswordResetForm -> UserManager_CMD: requestPasswordReset(email)
UserManager_CMD -> UserDAO: findUserByEmail(email)
UserDAO -> Database: SELECT * FROM users WHERE email=?
Database -> UserDAO: return userData
UserDAO -> UserManager_CMD: return userData

alt User Exists
    UserManager_CMD -> UserManager_CMD: generateResetToken()
    UserManager_CMD -> UserDAO: saveResetToken(userId, resetToken, expiryTime)
    UserDAO -> Database: UPDATE users SET resetToken=?, tokenExpiry=? WHERE userId=?
    Database -> UserDAO: return success
    UserDAO -> UserManager_CMD: return success
    
    UserManager_CMD -> EmailService: sendPasswordResetEmail(email, resetToken)
    EmailService -> EmailService: sendEmail(email, resetLink)
    EmailService -> UserManager_CMD: return emailSent
    
    UserManager_CMD -> PasswordResetForm: return "Check your email"
    PasswordResetForm -> User: display "Password reset email sent"
else User Not Found
    UserManager_CMD -> PasswordResetForm: return "Email not found"
    PasswordResetForm -> User: display "Email not found" (for security, don't reveal if email exists)
end
```

### **Phase 2: Reset Password with Token**
```
User -> PasswordResetForm: Click reset link (token)
PasswordResetForm -> UserManager_CMD: validateResetToken(token)
UserManager_CMD -> UserDAO: findUserByResetToken(token)
UserDAO -> Database: SELECT * FROM users WHERE resetToken=? AND tokenExpiry > NOW()
Database -> UserDAO: return userData or null
UserDAO -> UserManager_CMD: return userData

alt Valid Token
    PasswordResetForm -> User: Display password reset form
    User -> PasswordResetForm: Enter new password
    PasswordResetForm -> UserManager_CMD: resetPassword(token, newPassword)
    UserManager_CMD -> UserManager_CMD: validatePassword(newPassword)
    UserManager_CMD -> UserManager_CMD: hashPassword(newPassword)
    UserManager_CMD -> UserDAO: updatePassword(userId, hashedPassword)
    UserDAO -> Database: UPDATE users SET password=?, resetToken=NULL, tokenExpiry=NULL WHERE userId=?
    Database -> UserDAO: return success
    UserDAO -> UserManager_CMD: return success
    
    UserManager_CMD -> EmailService: sendPasswordChangedConfirmation(email)
    EmailService -> UserManager_CMD: return emailSent
    
    UserManager_CMD -> PasswordResetForm: return success
    PasswordResetForm -> User: redirect to Login page
else Invalid/Expired Token
    UserManager_CMD -> PasswordResetForm: return "Invalid or expired token"
    PasswordResetForm -> User: display "Reset link expired, request new one"
end
```

---

## Alternative Flows

### A1: Token Expired
```
UserManager_CMD -> UserDAO: findUserByResetToken(token)
UserDAO -> Database: SELECT * FROM users WHERE resetToken=? AND tokenExpiry > NOW()
Database -> UserDAO: return null (expired)
UserDAO -> UserManager_CMD: return null
UserManager_CMD -> PasswordResetForm: return "Token expired"
PasswordResetForm -> User: display "Link expired, request new reset"
```

### A2: Weak Password
```
UserManager_CMD -> UserManager_CMD: validatePassword(newPassword)
UserManager_CMD -> UserManager_CMD: return "WEAK_PASSWORD"
UserManager_CMD -> PasswordResetForm: return "Password too weak"
PasswordResetForm -> User: display password requirements
```

---

## Postconditions
- **Success:** Password reset, old token invalidated, confirmation email sent
- **Failure:** Token invalid/expired, user must request new reset
- **Security:** Token expires after 1 hour, single-use only

---

## Business Rules
- Reset token expires after 1 hour
- Token is single-use (invalidated after password reset)
- Password must meet security requirements
- Email confirmation sent for security

