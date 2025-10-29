# UC-004: User Login Sequence Diagram

## Use Case: User Login
**Actor:** Registered User  
**Goal:** Authenticate user and establish secure session  
**Precondition:** User has valid account credentials  

---

## Sequence Flow

```
User -> LoginForm: Enter username/password
LoginForm -> UserManager: validateCredentials(username, password)
UserManager -> UserDatabase: queryUser(username)
UserDatabase -> UserManager: return userData
UserManager -> SecurityService: hashPassword(password)
SecurityService -> UserManager: return hashedPassword
UserManager -> UserManager: comparePasswords(storedHash, inputHash)

alt Valid Credentials
    UserManager -> SessionManager: createSession(userId)
    SessionManager -> SessionManager: generateSessionToken()
    SessionManager -> UserManager: return sessionToken
    UserManager -> LoginForm: return success + sessionToken
    LoginForm -> User: redirect to Dashboard
else Invalid Credentials
    UserManager -> LoginForm: return error message
    LoginForm -> User: display "Invalid credentials"
end
```

---

## Alternative Flows

### A1: Account Locked
```
UserManager -> UserDatabase: checkAccountStatus(username)
UserDatabase -> UserManager: return "LOCKED"
UserManager -> LoginForm: return "Account locked"
LoginForm -> User: display "Account locked - contact support"
```

### A2: Password Reset Required
```
UserManager -> UserDatabase: checkPasswordExpiry(username)
UserDatabase -> UserManager: return "EXPIRED"
UserManager -> LoginForm: return "Password expired"
LoginForm -> User: redirect to Password Reset
```

---

## Postconditions
- **Success:** User is authenticated and redirected to dashboard
- **Failure:** User remains on login page with error message
- **Security:** Session token is created and stored securely

---

## Business Rules
- Maximum 3 failed login attempts before account lockout
- Session expires after 30 minutes of inactivity
- Password must meet security requirements
- Account lockout lasts 15 minutes
