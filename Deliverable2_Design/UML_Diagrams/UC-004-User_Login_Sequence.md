# UC-004: User Login Sequence Diagram

## Use Case: User Login
**Actor:** Registered User  
**Goal:** Authenticate user and establish secure session  
**Precondition:** User has valid account credentials  

**Design Pattern:** Command Pattern  
**3-Tier Architecture:** MM_Client → MM_Logic → MM_DataStore

---

## 🎯 **Lifelines (Participants) - Command Pattern Implementation**

```
User | LoginForm | API | Login_CMD | UserManager_CMD | UserDAO | Database
```

**Tier Mapping:**
- **MM_Client (Presentation):** LoginForm
- **MM_Logic (Business Logic):** API, Login_CMD, UserManager_CMD
- **MM_DataStore (Data):** UserDAO, Database

**Pattern Roles:**
- **Invoker:** API
- **Command:** Login_CMD
- **Receiver:** UserManager_CMD

---

## Sequence Flow - Command Pattern

```
User -> LoginForm: Enter username/password
LoginForm -> API: loginRequest(username, password)
API -> Login_CMD: execute(username, password)
Login_CMD -> UserManager_CMD: validateCredentials(username, password)
UserManager_CMD -> UserDAO: queryUser(username)
UserDAO -> Database: SELECT * FROM users WHERE username=?
Database -> UserDAO: return userData
UserDAO -> UserManager_CMD: return userData
UserManager_CMD -> UserManager_CMD: hashPassword(password)
UserManager_CMD -> UserManager_CMD: comparePasswords(storedHash, inputHash)

alt Valid Credentials
    UserManager_CMD -> UserManager_CMD: generateSessionToken()
    UserManager_CMD -> UserDAO: saveSession(userId, sessionToken)
    UserDAO -> Database: INSERT INTO sessions (userId, token)
    Database -> UserDAO: return success
    UserDAO -> UserManager_CMD: return success
    UserManager_CMD -> Login_CMD: return sessionToken
    Login_CMD -> API: return sessionToken
    API -> LoginForm: return success + sessionToken
    LoginForm -> User: redirect to Dashboard
else Invalid Credentials
    UserManager_CMD -> Login_CMD: return error
    Login_CMD -> API: return error
    API -> LoginForm: return "Invalid credentials"
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
