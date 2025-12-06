# Step-by-Step Eclipse Papyrus Instructions

## 🚀 **Getting Started**

### **Step 1: Open Eclipse Papyrus**
1. Launch Eclipse IDE
2. Go to **File → New → Papyrus Project**
3. Project Name: `MenuMap_UML_Design`
4. Select **UML** as modeling language
5. Click **Next** → **Finish**

### **Step 2: Create Use Case Diagram**
1. Right-click project → **New → Papyrus Model**
2. Name: `MenuMap_UseCase_Diagram`
3. Select **Use Case Diagram** template
4. Click **Next** → **Finish**

## 🎭 **Creating Use Case Diagram**

### **Step 3: Add Actors**
1. **Drag Actor** from palette to diagram
2. **Double-click** to rename:
   - "User" (Primary)
   - "Restaurant Owner" (Secondary)
   - "Administrator" (Secondary)
3. **Position actors** on left and right sides

### **Step 4: Add Use Cases**
1. **Drag Use Case** from palette to diagram
2. **Double-click** to rename each use case:
   - "Browse Menus"
   - "Search Restaurants"
   - "TM901 - Menu Verification"
   - "TM902 - Spam Protection"
   - "Password Reset"
   - "Manage Favorites"
   - "Delete Meal Entry"
   - "User Registration"
   - "User Login"

### **Step 5: Add Relationships**
1. **Drag Association** from palette
2. **Connect User to use cases**:
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

### **Step 6: Add Include/Extend Relationships**
1. **Drag Include** from palette
2. Connect: User Login → Password Reset
3. **Drag Extend** from palette
4. Connect: Password Reset → User Login

## 🏗️ **Creating Class Diagram**

### **Step 7: Create Class Diagram**
1. Right-click project → **New → Papyrus Model**
2. Name: `MenuMap_Class_Diagram`
3. Select **Class Diagram** template
4. Click **Next** → **Finish**

### **Step 8: Add Classes**
1. **Drag Class** from palette to diagram
2. **Double-click** each class to rename:
   - User
   - AuthenticationService
   - Restaurant
   - Menu
   - MenuItem
   - Favorite
   - VerificationSystem
   - SpamProtection
   - Report
   - Alert

### **Step 9: Add Attributes and Methods**
1. **Select class** → **Properties view**
2. **Add attributes** in Properties → **Attributes** tab
3. **Add methods** in Properties → **Operations** tab
4. **Use specifications** from Class_Diagram_Specification.md

### **Step 10: Add Relationships**
1. **Drag Association** from palette
2. **Connect classes** with proper multiplicities:
   - User 1..* → 0..* Favorite
   - Restaurant 1 → 1..* Menu
   - Menu 1 → 1..* MenuItem
3. **Add multiplicities** by double-clicking association ends

## 📊 **Creating Sequence Diagrams**

### **Step 11: Create Sequence Diagram**
1. Right-click project → **New → Papyrus Model**
2. Name: `MenuMap_Sequence_Diagrams`
3. Select **Sequence Diagram** template
4. Click **Next** → **Finish**

### **Step 12: Add Lifelines**
1. **Drag Lifeline** from palette
2. **Add actors and objects**:
   - User (Actor)
   - WebInterface
   - AuthenticationService
   - Database
   - EmailService

### **Step 13: Add Messages**
1. **Drag Message** from palette
2. **Connect lifelines** with messages
3. **Label messages** with operation names
4. **Follow specifications** from Sequence_Diagram_Specifications.md

### **Step 14: Add Activation Boxes**
1. **Select message** → **Properties**
2. **Check "Activation"** for synchronous calls
3. **Adjust activation box size** as needed

## 🎨 **Formatting and Styling**

### **Step 15: Format Diagrams**
1. **Select elements** → **Format menu**
2. **Adjust colors, fonts, sizes**
3. **Align elements** using alignment tools
4. **Add notes** for clarification

### **Step 16: Add Notes and Comments**
1. **Drag Note** from palette
2. **Add explanatory text**
3. **Connect notes** to relevant elements

## 📤 **Exporting Diagrams**

### **Step 17: Export as Images**
1. **Right-click diagram** → **Export**
2. **Select "Export as Image"**
3. **Choose format**: PNG or PDF
4. **Set resolution**: 300 DPI for quality
5. **Save to**: UML_Design/Exports/ folder

### **Step 18: Export Project**
1. **Right-click project** → **Export**
2. **Select "Archive File"**
3. **Include**: All UML files and diagrams
4. **Save as**: MenuMap_UML_Project.zip

## ✅ **Quality Checklist**

### **Before Exporting:**
- [ ] All actors and use cases labeled clearly
- [ ] All relationships properly connected
- [ ] Class attributes and methods included
- [ ] Sequence diagrams show complete flows
- [ ] Diagrams are visually appealing and readable
- [ ] All specifications from requirements document covered

### **File Organization:**
```
MenuMap_UML_Project/
├── MenuMap_UseCase_Diagram.uml
├── MenuMap_Class_Diagram.uml
├── MenuMap_Sequence_Diagrams.uml
├── Exports/
│   ├── UseCase_Diagram.png
│   ├── Class_Diagram.png
│   └── Sequence_Diagrams.png
└── README.md
```

## 🆘 **Troubleshooting**

### **Common Issues:**
- **Can't find palette**: Window → Show View → Palette
- **Elements not connecting**: Ensure proper selection and drag
- **Export not working**: Check file permissions and disk space
- **Diagram too cluttered**: Use packages or separate diagrams

### **Tips for Success:**
- **Save frequently** (Ctrl+S)
- **Use zoom** for detailed work
- **Group related elements** together
- **Follow naming conventions** consistently
- **Test export** before final submission
