# UC-005: User Registration Sequence Diagram

## Use Case: User Registration
**Actor:** Guest User  
**Goal:** Create new user account with secure credentials  
**Precondition:** User is not already registered  

**Design Pattern:** Factory Pattern  
**3-Tier Architecture:** MM_Client → MM_Logic → MM_DataStore

---

## 🎯 **Lifelines (Participants) - Factory Pattern Implementation**

```
User | RegistrationForm | UserManager_CMD | UserRepository | Database
```

**Tier Mapping:**
- **MM_Client (Presentation):** RegistrationForm
- **MM_Logic (Business Logic):** UserManager_CMD (Factory)
- **MM_DataStore (Data):** UserRepository, Database

**Pattern Roles:**
- **Factory:** UserManager_CMD
- **Products:** RegularUser, PremiumUser, RestaurantOwner

---

## Sequence Flow - Factory Pattern

```
User -> RegistrationForm: Enter registration details (userType, email, password)
RegistrationForm -> UserManager_CMD: validateRegistrationData(formData)
UserManager_CMD -> UserRepository: checkEmailExists(email)
UserRepository -> Database: SELECT email FROM users WHERE email=?
Database -> UserRepository: return null (email doesn't exist)
UserRepository -> UserManager_CMD: return emailAvailable

alt Valid Registration Data
    UserManager_CMD -> UserManager_CMD: hashPassword(password)
    UserManager_CMD -> UserManager_CMD: createUser(userType, userData, hashedPassword)
    
    alt userType == "RegularUser"
        UserManager_CMD -> UserManager_CMD: createRegularUser(userData)
    else userType == "PremiumUser"
        UserManager_CMD -> UserManager_CMD: createPremiumUser(userData)
    else userType == "RestaurantOwner"
        UserManager_CMD -> UserManager_CMD: createRestaurantOwner(userData)
    end
    
    UserManager_CMD -> UserRepository: saveUser(newUser)
    UserRepository -> Database: INSERT INTO users (email, password, userType, ...)
    Database -> UserRepository: return userId
    UserRepository -> UserManager_CMD: return userId
    UserManager_CMD -> RegistrationForm: return success + userId
    RegistrationForm -> User: display "Check email for verification"
else Invalid Data
    UserManager_CMD -> RegistrationForm: return validationErrors
    RegistrationForm -> User: display error messages
end
```

---

## Alternative Flows

### A1: Email Already Exists
```
UserManager -> UserDatabase: checkEmailExists(email)
UserDatabase -> UserManager: return "EXISTS"
UserManager -> RegistrationForm: return "Email already registered"
RegistrationForm -> User: display "Email already exists"
```

### A2: Weak Password
```
ValidationService -> UserManager: return "WEAK_PASSWORD"
UserManager -> RegistrationForm: return "Password too weak"
RegistrationForm -> User: display password requirements
```

### A3: Email Verification Required
```
User -> EmailService: click verification link
EmailService -> UserManager: verifyEmail(userId, token)
UserManager -> UserDatabase: updateAccountStatus(userId, "VERIFIED")
UserDatabase -> UserManager: return success
UserManager -> User: redirect to Login page
```

---

## Postconditions
- **Success:** User account created, verification email sent
- **Failure:** User remains on registration page with errors
- **Security:** Password is hashed before storage
- **Verification:** Account requires email verification before login

---

## Business Rules
- Email must be unique across system
- Password must be 8+ characters with mixed case and numbers
- Email verification required within 24 hours
- Account remains inactive until email verified
