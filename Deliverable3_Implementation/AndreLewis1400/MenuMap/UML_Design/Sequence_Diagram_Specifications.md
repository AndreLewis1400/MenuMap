# Sequence Diagram Specifications - MenuMap

## 1. User Login Process

### **Actors & Objects:**
- **User** (Actor)
- **WebInterface** (Object)
- **AuthenticationService** (Object)
- **Database** (Object)

### **Sequence Flow:**
```
User → WebInterface: Enter credentials
WebInterface → AuthenticationService: validateUser(credentials)
AuthenticationService → Database: checkUserExists(username)
Database → AuthenticationService: return userData
AuthenticationService → AuthenticationService: verifyPassword()
AuthenticationService → Database: updateLastLogin()
AuthenticationService → WebInterface: return sessionToken
WebInterface → User: Display dashboard
```

### **Alternative Flows:**
- **Invalid Credentials**: AuthenticationService → WebInterface: return error
- **Account Locked**: AuthenticationService → WebInterface: return lockout message

## 2. Menu Verification Process (TM901)

### **Actors & Objects:**
- **Restaurant Owner** (Actor)
- **WebInterface** (Object)
- **VerificationSystem** (Object)
- **Database** (Object)
- **NotificationService** (Object)

### **Sequence Flow:**
```
Restaurant Owner → WebInterface: Submit menu for verification
WebInterface → VerificationSystem: verifyMenu(menuData)
VerificationSystem → Database: checkExistingMenus()
VerificationSystem → VerificationSystem: validateMenuItems()
VerificationSystem → VerificationSystem: checkPricingConsistency()
VerificationSystem → Database: storeVerificationResult()
VerificationSystem → NotificationService: sendVerificationNotification()
NotificationService → Restaurant Owner: Email verification status
VerificationSystem → WebInterface: return verificationStatus
WebInterface → Restaurant Owner: Display verification results
```

## 3. Spam Detection Process (TM902)

### **Actors & Objects:**
- **User** (Actor)
- **WebInterface** (Object)
- **SpamProtection** (Object)
- **Database** (Object)
- **Administrator** (Actor)

### **Sequence Flow:**
```
User → WebInterface: Submit content
WebInterface → SpamProtection: analyzeContent(content)
SpamProtection → Database: checkBlacklist()
SpamProtection → SpamProtection: calculateSpamScore()
alt [Spam Score > Threshold]
    SpamProtection → Database: flagAsSpam()
    SpamProtection → Administrator: sendSpamAlert()
    SpamProtection → WebInterface: return blocked
    WebInterface → User: Display blocked message
else [Spam Score < Threshold]
    SpamProtection → Database: storeContent()
    SpamProtection → WebInterface: return approved
    WebInterface → User: Display success message
end
```

## 4. Password Reset Process

### **Actors & Objects:**
- **User** (Actor)
- **WebInterface** (Object)
- **AuthenticationService** (Object)
- **EmailService** (Object)
- **Database** (Object)

### **Sequence Flow:**
```
User → WebInterface: Request password reset
WebInterface → AuthenticationService: initiatePasswordReset(email)
AuthenticationService → Database: validateEmail(email)
AuthenticationService → AuthenticationService: generateResetToken()
AuthenticationService → Database: storeResetToken()
AuthenticationService → EmailService: sendResetEmail(token, email)
EmailService → User: Email with reset link
User → WebInterface: Click reset link with token
WebInterface → AuthenticationService: validateResetToken(token)
AuthenticationService → Database: verifyToken(token)
AuthenticationService → WebInterface: return tokenValid
WebInterface → User: Display new password form
User → WebInterface: Submit new password
WebInterface → AuthenticationService: resetPassword(token, newPassword)
AuthenticationService → Database: updatePassword()
AuthenticationService → Database: invalidateToken()
AuthenticationService → WebInterface: return success
WebInterface → User: Display success message
```

## 5. Manage Favorites Process

### **Actors & Objects:**
- **User** (Actor)
- **WebInterface** (Object)
- **FavoriteService** (Object)
- **Database** (Object)

### **Sequence Flow:**
```
User → WebInterface: View favorites
WebInterface → FavoriteService: getUserFavorites(userID)
FavoriteService → Database: queryFavorites(userID)
Database → FavoriteService: return favoritesList
FavoriteService → WebInterface: return favoritesData
WebInterface → User: Display favorites

User → WebInterface: Add to favorites
WebInterface → FavoriteService: addFavorite(userID, itemID)
FavoriteService → Database: checkExistingFavorite()
alt [Favorite exists]
    FavoriteService → WebInterface: return alreadyExists
else [New favorite]
    FavoriteService → Database: createFavorite()
    FavoriteService → WebInterface: return success
end
WebInterface → User: Display updated favorites
```

## 📐 **Layout Guidelines for Each Diagram:**

### **Vertical Layout:**
- **Actors**: Left side, stick figures
- **Objects**: Center, rectangles with object names
- **Lifelines**: Vertical dashed lines
- **Messages**: Horizontal arrows with labels
- **Activation boxes**: Rectangles on lifelines

### **Message Types:**
- **Synchronous**: Solid arrow with filled arrowhead
- **Asynchronous**: Solid arrow with open arrowhead
- **Return**: Dashed arrow
- **Self-call**: Curved arrow back to same lifeline

### **Alternative Flows:**
- Use **alt/else/end** frames for conditional logic
- Use **loop** frames for repetitive processes
- Use **opt** frames for optional steps
