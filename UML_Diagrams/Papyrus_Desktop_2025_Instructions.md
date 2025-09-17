# Papyrus-Desktop 2025-06 (4.36) - Complete UML Creation Guide

## 🚀 **Getting Started with Papyrus-Desktop 2025**

### **Step 1: Create New Project**
1. **File → New → Project...**
2. **Expand "Papyrus"** → **Select "Papyrus Project"**
3. **Click Next**
4. **Project Name**: `MenuMap_UML_Design`
5. **Modeling Language**: Select **UML** from dropdown
6. **Click Next → Finish**

### **Step 2: Create UML Model**
1. **Right-click your project** in Project Explorer
2. **New → Papyrus Model**
3. **Name**: `MenuMap_Model`
4. **Template**: Select **Empty Model**
5. **Click Next → Finish**

## 🎭 **Creating Use Case Diagram (Papyrus-Desktop 2025)**

### **Step 3: Create Use Case Diagram**
1. **Right-click MenuMap_Model** in Project Explorer
2. **New Diagram → Use Case Diagram** (this is available in your version)
3. **Name**: `MenuMap_UseCase_Diagram`
4. **Click OK**

### **Step 4: Access the Palette**
1. **If Palette is not visible**: **Window → Show View → Palette**
2. **Palette should appear** on the right side
3. **Look for "Use Case" section** in the palette

### **Step 5: Add Actors**
1. **From Palette** → **Drag "Actor"** to diagram canvas
2. **Double-click the actor** to rename:
   - First actor: `User`
   - Second actor: `Restaurant Owner`
   - Third actor: `Administrator`
3. **Position actors** on left and right sides of diagram

### **Step 6: Add Use Cases**
1. **From Palette** → **Drag "Use Case"** to diagram canvas
2. **Double-click each use case** to rename:
   - `Browse Menus`
   - `Search Restaurants`
   - `TM901 - Menu Verification`
   - `TM902 - Spam Protection`
   - `Password Reset`
   - `Manage Favorites`
   - `Delete Meal Entry`
   - `User Registration`
   - `User Login`

### **Step 7: Add Relationships**
1. **From Palette** → **Drag "Association"**
2. **Connect User to use cases**:
   - Click on User actor, then drag to each use case
   - User → Browse Menus
   - User → Search Restaurants
   - User → Password Reset
   - User → Manage Favorites
   - User → Delete Meal Entry
   - User → User Registration
   - User → User Login

3. **Connect Restaurant Owner**:
   - Restaurant Owner → TM901 - Menu Verification
   - Restaurant Owner → Browse Menus

4. **Connect Administrator**:
   - Administrator → TM902 - Spam Protection
   - Administrator → TM901 - Menu Verification

### **Step 8: Add Include/Extend Relationships**
1. **From Palette** → **Drag "Include"**
2. **Connect**: User Login → Password Reset
3. **From Palette** → **Drag "Extend"**
4. **Connect**: Password Reset → User Login

## 🏗️ **Creating Class Diagram (Papyrus-Desktop 2025)**

### **Step 9: Create Class Diagram**
1. **Right-click MenuMap_Model** in Project Explorer
2. **New Diagram → Class Diagram** (this is available in your version)
3. **Name**: `MenuMap_Class_Diagram`
4. **Click OK**

### **Step 10: Add Classes**
1. **From Palette** → **Drag "Class"** to diagram canvas
2. **Double-click each class** to rename:
   - `User`
   - `AuthenticationService`
   - `Restaurant`
   - `Menu`
   - `MenuItem`
   - `Favorite`
   - `VerificationSystem`
   - `SpamProtection`
   - `Report`
   - `Alert`

### **Step 11: Add Attributes and Methods**
1. **Select a class** (e.g., User)
2. **Right-click** → **Edit** or **Double-click**
3. **In Properties view** (if not visible: **Window → Show View → Properties**)
4. **Attributes tab** → **Click "+" to add**:
   ```
   - userID: String
   - username: String
   - email: String
   - password: String
   - registrationDate: Date
   - lastLogin: Date
   - isActive: Boolean
   ```

5. **Operations tab** → **Click "+" to add**:
   ```
   + login(): Boolean
   + logout(): void
   + updateProfile(): void
   + changePassword(): void
   + getFavorites(): List<Favorite>
   ```

### **Step 12: Add Relationships**
1. **From Palette** → **Drag "Association"**
2. **Connect classes** with proper multiplicities:
   - User 1..* → 0..* Favorite
   - Restaurant 1 → 1..* Menu
   - Menu 1 → 1..* MenuItem
   - User 1 → 1 AuthenticationService

3. **To set multiplicities**:
   - **Select association end** (the end of the line)
   - **In Properties view** → **Multiplicity**
   - **Set values** (e.g., 1..*)

## 📊 **Creating Sequence Diagrams (Papyrus-Desktop 2025)**

### **Step 13: Create Sequence Diagram**
1. **Right-click MenuMap_Model** in Project Explorer
2. **New Diagram → Sequence Diagram** (this is available in your version)
3. **Name**: `User_Login_Sequence`
4. **Click OK**

### **Step 14: Add Lifelines**
1. **From Palette** → **Drag "Lifeline"** to diagram canvas
2. **Double-click each lifeline** to rename:
   - `User` (Actor)
   - `WebInterface`
   - `AuthenticationService`
   - `Database`

### **Step 15: Add Messages**
1. **From Palette** → **Drag "Message"**
2. **Connect lifelines** with messages:
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

### **Step 16: Add Activation Boxes**
1. **Select message** → **In Properties view**
2. **Check "Activation"** for synchronous calls
3. **Adjust activation box size** by dragging

## 🎨 **Formatting and Styling (Papyrus-Desktop 2025)**

### **Step 17: Format Diagrams**
1. **Select elements** → **Right-click** → **Format**
2. **Adjust colors, fonts, sizes**
3. **Use alignment tools** in toolbar
4. **Add notes** for clarification

### **Step 18: Add Notes**
1. **From Palette** → **Drag "Note"**
2. **Add explanatory text**
3. **Connect notes** to relevant elements using **"Note Attachment"**

## 📤 **Exporting Diagrams (Papyrus-Desktop 2025)**

### **Step 19: Export as Images**
1. **Right-click diagram** in Project Explorer
2. **Export** → **Export as Image**
3. **Choose format**: PNG or PDF
4. **Set resolution**: 300 DPI for quality
5. **Save to**: Desktop/CEN4010_UML_Documentation/Exports/

### **Step 20: Export Project**
1. **Right-click project** in Project Explorer
2. **Export** → **Archive File**
3. **Include**: All UML files and diagrams
4. **Save as**: MenuMap_UML_Project.zip

## 🔧 **Papyrus-Desktop 2025 Specific Tips**

### **Interface Differences:**
- **Project Explorer** is on the left
- **Palette** is on the right
- **Properties view** is at the bottom
- **Diagram canvas** is in the center

### **Keyboard Shortcuts:**
- **Ctrl+S**: Save
- **Ctrl+Z**: Undo
- **Ctrl+Y**: Redo
- **F5**: Refresh
- **Ctrl+Shift+P**: Show Palette

### **Troubleshooting:**
- **If Palette disappears**: Window → Show View → Palette
- **If Properties view disappears**: Window → Show View → Properties
- **If Project Explorer disappears**: Window → Show View → Project Explorer
- **To reset perspective**: Window → Reset Perspective

## ✅ **Quality Checklist for Papyrus-Desktop 2025**

### **Before Exporting:**
- [ ] All actors and use cases labeled clearly
- [ ] All relationships properly connected
- [ ] Class attributes and methods included
- [ ] Sequence diagrams show complete flows
- [ ] Diagrams are visually appealing and readable
- [ ] All specifications from requirements document covered
- [ ] High resolution export (300 DPI)

## 🆘 **Common Issues and Solutions**

### **Issue: Can't find Palette**
**Solution**: Window → Show View → Palette

### **Issue: Elements not connecting**
**Solution**: Ensure proper selection and drag from source to target

### **Issue: Export not working**
**Solution**: Check file permissions and disk space

### **Issue: Diagram too cluttered**
**Solution**: Use packages or separate diagrams

---

**You're now ready to create professional UML diagrams in Papyrus-Desktop 2025!** 🎓
