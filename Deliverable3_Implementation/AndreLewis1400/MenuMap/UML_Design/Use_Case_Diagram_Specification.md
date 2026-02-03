# Use Case Diagram Specification - MenuMap

## Diagram Elements to Create in Papyrus

### 🎭 **Actors**
1. **User** (Primary Actor)
   - Stick figure icon
   - Label: "User"
   - Description: "Food enthusiast, restaurant customer"

2. **Restaurant Owner** (Secondary Actor)
   - Stick figure icon
   - Label: "Restaurant Owner"
   - Description: "Food service establishment owner"

3. **Administrator** (Secondary Actor)
   - Stick figure icon
   - Label: "Administrator"
   - Description: "System administrator, content manager"

### 📋 **Use Cases**
1. **Browse Menus**
   - Oval shape
   - Label: "Browse Menus"
   - Description: "View restaurant menus and menu items"

2. **Search Restaurants**
   - Oval shape
   - Label: "Search Restaurants"
   - Description: "Find restaurants by location, cuisine, or name"

3. **TM901 - Menu Verification**
   - Oval shape
   - Label: "TM901 - Menu Verification"
   - Description: "Verify menu information accuracy and authenticity"

4. **TM902 - Spam Protection**
   - Oval shape
   - Label: "TM902 - Spam Protection"
   - Description: "Protect against spam content and malicious entries"

5. **Password Reset**
   - Oval shape
   - Label: "Password Reset"
   - Description: "Secure password reset functionality"

6. **Manage Favorites**
   - Oval shape
   - Label: "Manage Favorites"
   - Description: "Save and organize favorite restaurants and meals"

7. **Delete Meal Entry**
   - Oval shape
   - Label: "Delete Meal Entry"
   - Description: "Remove meal entries from history or favorites"

8. **User Registration**
   - Oval shape
   - Label: "User Registration"
   - Description: "Create new user account"

9. **User Login**
   - Oval shape
   - Label: "User Login"
   - Description: "Authenticate user access"

### 🔗 **Relationships**

#### **User Relationships:**
- User → Browse Menus (Association)
- User → Search Restaurants (Association)
- User → Password Reset (Association)
- User → Manage Favorites (Association)
- User → Delete Meal Entry (Association)
- User → User Registration (Association)
- User → User Login (Association)

#### **Restaurant Owner Relationships:**
- Restaurant Owner → TM901 - Menu Verification (Association)
- Restaurant Owner → Browse Menus (Association)

#### **Administrator Relationships:**
- Administrator → TM902 - Spam Protection (Association)
- Administrator → TM901 - Menu Verification (Association)
- Administrator → User Registration (Association)

#### **Include Relationships:**
- User Login → Password Reset (Include)
- Manage Favorites → Browse Menus (Include)
- Delete Meal Entry → Browse Menus (Include)

#### **Extend Relationships:**
- Password Reset → User Login (Extend)

## 📐 **Layout Suggestions**
```
[User] ←→ [Browse Menus] ←→ [Search Restaurants]
   ↓           ↓
[User Login] [Manage Favorites]
   ↓           ↓
[Password Reset] [Delete Meal Entry]

[Restaurant Owner] → [TM901 - Menu Verification]
[Administrator] → [TM902 - Spam Protection]
```

## 🎨 **Visual Guidelines**
- **Actors**: Place on left and right sides
- **Use Cases**: Arrange in center area
- **Primary Use Cases**: Larger, more prominent
- **Secondary Use Cases**: Smaller, supporting roles
- **Relationships**: Clear, non-overlapping lines
- **Labels**: Readable font size, clear positioning
