# UC-005: User Registration Sequence Diagram

## Use Case: User Registration
**Actor:** Guest User  
**Goal:** Create new user account with secure credentials  
**Precondition:** User is not already registered  

---

## Sequence Flow

```
User -> RegistrationForm: Enter registration details
RegistrationForm -> UserManager: validateRegistrationData(formData)
UserManager -> ValidationService: validateEmail(email)
ValidationService -> UserManager: return emailValid
UserManager -> ValidationService: validatePassword(password)
ValidationService -> UserManager: return passwordValid

alt Valid Registration Data
    UserManager -> SecurityService: hashPassword(password)
    SecurityService -> UserManager: return hashedPassword
    UserManager -> UserDatabase: createUser(userData, hashedPassword)
    UserDatabase -> UserManager: return userId
    UserManager -> EmailService: sendVerificationEmail(email, userId)
    EmailService -> UserManager: return emailSent
    UserManager -> RegistrationForm: return success
    RegistrationForm -> User: display "Check email for verification"
else Invalid Data
    UserManager -> RegistrationForm: return validationErrors
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
