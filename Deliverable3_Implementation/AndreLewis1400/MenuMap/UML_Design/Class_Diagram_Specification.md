# Class Diagram Specification - MenuMap

## Classes to Create in Papyrus

### 👤 **User Management Classes**

#### **User Class**
```
+ userID: String
+ username: String
+ email: String
+ password: String
+ registrationDate: Date
+ lastLogin: Date
+ isActive: Boolean
---
+ login(): Boolean
+ logout(): void
+ updateProfile(): void
+ changePassword(): void
+ getFavorites(): List<Favorite>
```

#### **AuthenticationService Class**
```
+ sessionToken: String
+ loginAttempts: Integer
+ lockoutTime: Date
---
+ authenticateUser(): Boolean
+ generateToken(): String
+ validateToken(): Boolean
+ resetPassword(): void
+ sendResetEmail(): void
```

### 🏪 **Restaurant & Menu Classes**

#### **Restaurant Class**
```
+ restaurantID: String
+ name: String
+ address: String
+ phoneNumber: String
+ cuisineType: String
+ rating: Double
+ isVerified: Boolean
---
+ getMenu(): Menu
+ updateInfo(): void
+ verifyRestaurant(): void
+ calculateRating(): Double
```

#### **Menu Class**
```
+ menuID: String
+ restaurantID: String
+ lastUpdated: Date
+ isActive: Boolean
---
+ getMenuItems(): List<MenuItem>
+ addMenuItem(): void
+ updateMenuItem(): void
+ removeMenuItem(): void
```

#### **MenuItem Class**
```
+ itemID: String
+ menuID: String
+ name: String
+ description: String
+ price: Double
+ category: String
+ isAvailable: Boolean
+ calories: Integer
---
+ updatePrice(): void
+ updateDescription(): void
+ setAvailability(): void
```

### ⭐ **Favorites & User Preferences**

#### **Favorite Class**
```
+ favoriteID: String
+ userID: String
+ itemID: String
+ itemType: String
+ dateAdded: Date
+ notes: String
---
+ addToFavorites(): void
+ removeFromFavorites(): void
+ updateNotes(): void
```

### 🔒 **Security & Verification Classes**

#### **VerificationSystem Class**
```
+ verificationID: String
+ itemID: String
+ verificationStatus: String
+ verifiedBy: String
+ verificationDate: Date
---
+ verifyMenuItem(): Boolean
+ flagSuspiciousContent(): void
+ generateReport(): Report
```

#### **SpamProtection Class**
```
+ protectionID: String
+ contentID: String
+ spamScore: Double
+ isBlocked: Boolean
+ detectionMethod: String
---
+ analyzeContent(): Double
+ blockContent(): void
+ whitelistContent(): void
+ generateAlert(): Alert
```

### 📊 **Supporting Classes**

#### **Report Class**
```
+ reportID: String
+ reportType: String
+ generatedBy: String
+ reportDate: Date
+ content: String
---
+ generateReport(): void
+ exportReport(): File
+ sendReport(): void
```

#### **Alert Class**
```
+ alertID: String
+ alertType: String
+ severity: String
+ message: String
+ timestamp: Date
---
+ sendAlert(): void
+ logAlert(): void
```

## 🔗 **Relationships**

### **Associations:**
- User 1..* → 0..* Favorite
- User 1 → 1 AuthenticationService
- Restaurant 1 → 1..* Menu
- Menu 1 → 1..* MenuItem
- MenuItem 1 → 0..1 VerificationSystem
- MenuItem 1 → 0..1 SpamProtection
- VerificationSystem 1 → 0..* Report
- SpamProtection 1 → 0..* Alert

### **Compositions:**
- Restaurant ◆→ Menu
- Menu ◆→ MenuItem

### **Dependencies:**
- AuthenticationService → User
- VerificationSystem → MenuItem
- SpamProtection → MenuItem

## 📐 **Layout Suggestions**
```
[User] ←→ [AuthenticationService]
   ↓
[Favorite] ←→ [MenuItem] ←→ [Menu] ←→ [Restaurant]
                ↓
        [VerificationSystem] [SpamProtection]
                ↓              ↓
            [Report]        [Alert]
```

## 🎨 **Visual Guidelines**
- **Primary Classes**: Larger rectangles, bold borders
- **Supporting Classes**: Smaller rectangles
- **Relationships**: Clear arrows with proper multiplicities
- **Attributes**: Private (-), Public (+), Protected (#)
- **Methods**: Include return types and parameters
- **Grouping**: Related classes clustered together
