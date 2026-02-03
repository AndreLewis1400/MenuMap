# UC-004: User Login Sequence Diagram

## Use Case: User Login
**Actor:** Registered User 
**Goal:** Authenticate user and establish secure session 
**Precondition:** User has valid account credentials 

**Design Pattern:** Command Pattern 
**3-Tier Architecture:** MM_Client → MM_Logic → MM_DataStore

---

## **Lifelines (Participants) - Command Pattern Implementation**

```
User | LoginForm | API | Login_CMD | UserManager_CMD | UserRepository | Database
```

**Tier Mapping:**
- **MM_Client (Presentation):** LoginForm
- **MM_Logic (Business Logic):** API, Login_CMD, UserManager_CMD
- **MM_DataStore (Data):** UserRepository, Database

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
UserManager_CMD -> UserRepository: queryUser(username)
UserRepository -> Database: SELECT * FROM users WHERE username=?
Database -> UserRepository: return userData
UserRepository -> UserManager_CMD: return userData
UserManager_CMD -> UserManager_CMD: hashPassword(password)
UserManager_CMD -> UserManager_CMD: comparePasswords(storedHash, inputHash)

alt Valid Credentials
 UserManager_CMD -> UserManager_CMD: generateSessionToken()
 UserManager_CMD -> UserRepository: saveSession(userId, sessionToken)
 UserRepository -> Database: INSERT INTO sessions (userId, token)
 Database -> UserRepository: return success
 UserRepository -> UserManager_CMD: return success
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
UserManager_CMD -> UserRepository: checkAccountStatus(username)
UserRepository -> Database: SELECT accountStatus FROM users WHERE username=?
Database -> UserRepository: return "LOCKED"
UserRepository -> UserManager_CMD: return "LOCKED"
UserManager_CMD -> Login_CMD: return "Account locked"
Login_CMD -> API: return "Account locked"
API -> LoginForm: return "Account locked"
LoginForm -> User: display "Account locked - contact support"
```

### A2: Password Reset Required
```
UserManager_CMD -> UserRepository: checkPasswordExpiry(username)
UserRepository -> Database: SELECT passwordExpiry FROM users WHERE username=?
Database -> UserRepository: return "EXPIRED"
UserRepository -> UserManager_CMD: return "EXPIRED"
UserManager_CMD -> Login_CMD: return "Password expired"
Login_CMD -> API: return "Password expired"
API -> LoginForm: return "Password expired"
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
