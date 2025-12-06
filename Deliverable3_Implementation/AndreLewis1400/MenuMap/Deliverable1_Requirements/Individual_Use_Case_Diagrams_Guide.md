# Individual Use Case Diagrams Guide
## Creating 3 Separate Use Case Diagrams in Papyrus

**Purpose**: Create individual use case diagrams for each of the 3 use cases as required by the assignment  
**Tool**: Eclipse Papyrus  
**Author**: Andre Lewis (UML Diagrams Coordinator)  

---

## 🎯 **What You Need to Create**

You need to create **3 separate use case diagrams** in Papyrus:

1. **UC-001: Browse Restaurant Menus** (Normal Use Case)
2. **UC-002: Manage Favorites** (Normal Use Case)  
3. **UC-003: Secure Password Reset** (Security Use Case)

---

## 📋 **Step-by-Step Instructions**

### **Step 1: Open Eclipse Papyrus**
1. Launch Eclipse IDE
2. Open your existing Papyrus project: `MenuMap_UML_Design`
3. Or create a new Papyrus project if needed

### **Step 2: Create Individual Use Case Diagrams**

#### **For UC-001: Browse Restaurant Menus**

1. **Right-click** on your Papyrus project
2. **Select**: New → Papyrus Model
3. **Choose**: UML as the modeling language
4. **Name**: `UC001_Browse_Restaurant_Menus`
5. **Select**: Use Case Diagram as the initial diagram

**Elements to Add:**
- **Actors**:
  - User (Primary Actor)
  - Restaurant Owner (Secondary Actor)
  - MenuMap System (System Actor)
- **Use Case**: Browse Restaurant Menus
- **Relationships**:
  - User → Browse Restaurant Menus (Association)
  - Restaurant Owner → Browse Restaurant Menus (Association)
  - MenuMap System → Browse Restaurant Menus (Association)

#### **For UC-002: Manage Favorites**

1. **Right-click** on your Papyrus project
2. **Select**: New → Papyrus Model
3. **Choose**: UML as the modeling language
4. **Name**: `UC002_Manage_Favorites`
5. **Select**: Use Case Diagram as the initial diagram

**Elements to Add:**
- **Actors**:
  - Registered User (Primary Actor)
  - MenuMap System (System Actor)
- **Use Case**: Manage Favorites
- **Relationships**:
  - Registered User → Manage Favorites (Association)
  - MenuMap System → Manage Favorites (Association)

#### **For UC-003: Secure Password Reset**

1. **Right-click** on your Papyrus project
2. **Select**: New → Papyrus Model
3. **Choose**: UML as the modeling language
4. **Name**: `UC003_Secure_Password_Reset`
5. **Select**: Use Case Diagram as the initial diagram

**Elements to Add:**
- **Actors**:
  - User (Primary Actor)
  - MenuMap System (System Actor)
  - Email Service (External Actor)
- **Use Case**: Secure Password Reset
- **Relationships**:
  - User → Secure Password Reset (Association)
  - MenuMap System → Secure Password Reset (Association)
  - Email Service → Secure Password Reset (Association)

---

## 🎨 **Visual Design Guidelines**

### **Actor Styling:**
- **Primary Actors**: Larger, more prominent
- **Secondary Actors**: Medium size
- **System Actors**: Smaller, different color
- **External Actors**: Distinct styling

### **Use Case Styling:**
- **Normal Use Cases**: Standard oval shape
- **Security Use Case**: Highlighted with different color or border
- **Clear labels**: Use case names should be readable

### **Relationship Styling:**
- **Associations**: Solid lines with arrows
- **Include/Extend**: Dashed lines if applicable
- **Clear direction**: Arrows point to use cases

---

## 📐 **Layout Suggestions**

### **UC-001: Browse Restaurant Menus**
```
[User] ──────────→ [Browse Restaurant Menus] ←────────── [Restaurant Owner]
                           ↑
                    [MenuMap System]
```

### **UC-002: Manage Favorites**
```
[Registered User] ──────────→ [Manage Favorites] ←────────── [MenuMap System]
```

### **UC-003: Secure Password Reset**
```
[User] ──────────→ [Secure Password Reset] ←────────── [MenuMap System]
                           ↑
                    [Email Service]
```

---

## 🔧 **Technical Steps in Papyrus**

### **Adding Actors:**
1. **Drag** "Actor" from the palette
2. **Place** on the diagram
3. **Double-click** to edit name
4. **Right-click** → Properties to change styling

### **Adding Use Cases:**
1. **Drag** "Use Case" from the palette
2. **Place** on the diagram
3. **Double-click** to edit name
4. **Resize** as needed

### **Adding Relationships:**
1. **Select** "Association" from the palette
2. **Click** on source actor
3. **Drag** to target use case
4. **Add** arrow if needed

### **Exporting Diagrams:**
1. **Right-click** on diagram
2. **Select** "Export as Image"
3. **Choose** PNG format
4. **Save** with descriptive name

---

## 📁 **File Organization**

### **Save As:**
- `UC001_Browse_Restaurant_Menus.PNG`
- `UC002_Manage_Favorites.PNG`
- `UC003_Secure_Password_Reset.PNG`

### **Copy to Project:**
Copy the exported PNG files to:
`/Users/andrelewis/HomeProjects/COP4610_Operating_Systems/Classes/CEN4010_Software_Engineering/Projects/MenuMap_Project/UML_Design/Exports/`

---

## ✅ **Quality Checklist**

### **Before Exporting:**
- [ ] All actors are clearly labeled
- [ ] Use case names are descriptive
- [ ] Relationships are properly drawn
- [ ] Diagram is well-organized and readable
- [ ] Security use case is highlighted
- [ ] No overlapping elements

### **After Exporting:**
- [ ] PNG files are clear and readable
- [ ] File names are descriptive
- [ ] Files are saved in the correct location
- [ ] All 3 diagrams are created

---

## 🚀 **Quick Start Commands**

### **If you need to create a new Papyrus project:**
1. File → New → Papyrus Project
2. Name: `MenuMap_Individual_Use_Cases`
3. Select UML as modeling language
4. Create the 3 diagrams as described above

### **If using existing project:**
1. Open existing `MenuMap_UML_Design` project
2. Create new models for each use case
3. Follow the element guidelines above

---

## 💡 **Pro Tips**

1. **Start Simple**: Create basic diagrams first, then add styling
2. **Use Templates**: Copy elements from your existing diagrams
3. **Consistent Styling**: Use the same colors and fonts across all diagrams
4. **Clear Labels**: Make sure all text is readable
5. **Test Export**: Export one diagram first to check quality

---

*Follow this guide to create the 3 individual use case diagrams required for your assignment. Each diagram should focus on one specific use case and show the relevant actors and relationships.*
