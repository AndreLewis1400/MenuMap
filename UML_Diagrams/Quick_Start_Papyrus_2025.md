# Quick Start Guide - Papyrus-Desktop 2025-06

## 🚀 **5-Minute Setup**

### **1. Create Project (1 minute)**
```
File → New → Project → Papyrus → Papyrus Project
Name: MenuMap_UML_Design
Modeling Language: UML
```

### **2. Create Model (1 minute)**
```
Right-click project → New → Papyrus Model
Name: MenuMap_Model
Template: Empty Model
```

### **3. Create Use Case Diagram (2 minutes)**
```
Right-click model → New Diagram → Use Case Diagram
Name: MenuMap_UseCase_Diagram
```

### **4. Add Elements (1 minute)**
- **Drag 3 Actors** from Palette: User, Restaurant Owner, Administrator
- **Drag 9 Use Cases** from Palette: Browse Menus, TM901, TM902, etc.
- **Connect with Associations**

## 🎯 **Key Elements to Create**

### **Use Case Diagram:**
- **3 Actors**: User, Restaurant Owner, Administrator
- **9 Use Cases**: Browse Menus, Search Restaurants, TM901, TM902, Password Reset, Manage Favorites, Delete Meal Entry, User Registration, User Login
- **Relationships**: Connect User to all use cases, Restaurant Owner to TM901, Administrator to TM902

### **Class Diagram:**
- **10 Classes**: User, AuthenticationService, Restaurant, Menu, MenuItem, Favorite, VerificationSystem, SpamProtection, Report, Alert
- **Key Relationships**: User→Favorite, Restaurant→Menu, Menu→MenuItem

### **Sequence Diagrams:**
- **User Login**: User → WebInterface → AuthenticationService → Database
- **Menu Verification**: Restaurant Owner → WebInterface → VerificationSystem → Database
- **Spam Detection**: User → WebInterface → SpamProtection → Database

## 🔧 **Papyrus-Desktop 2025 Interface**

### **Main Areas:**
- **Left**: Project Explorer (your files)
- **Center**: Diagram Canvas (where you draw)
- **Right**: Palette (tools to drag)
- **Bottom**: Properties (element details)

### **Essential Tools:**
- **Actor**: For use case diagrams
- **Use Case**: For use case diagrams
- **Class**: For class diagrams
- **Lifeline**: For sequence diagrams
- **Association**: For connecting elements
- **Message**: For sequence diagrams

## ⚡ **Quick Tips**

### **Navigation:**
- **Zoom**: Mouse wheel or Ctrl + Mouse wheel
- **Pan**: Middle mouse button drag
- **Select All**: Ctrl+A
- **Delete**: Delete key

### **Editing:**
- **Rename**: Double-click element
- **Properties**: Right-click → Properties
- **Copy**: Ctrl+C
- **Paste**: Ctrl+V

### **Export:**
- **Right-click diagram** → Export → Export as Image
- **Format**: PNG
- **Resolution**: 300 DPI
- **Save to**: Desktop/CEN4010_UML_Documentation/Exports/

## 🎨 **Professional Formatting**

### **Layout:**
- **Actors**: Left and right sides
- **Use Cases**: Center area
- **Classes**: Group related classes together
- **Sequence**: Lifelines evenly spaced

### **Styling:**
- **Colors**: Use consistent color scheme
- **Fonts**: Keep readable and professional
- **Sizes**: Make important elements larger
- **Alignment**: Use alignment tools for neat appearance

## ✅ **30-Minute Complete Creation Plan**

### **Minutes 1-5**: Project Setup
- Create project and model
- Set up workspace

### **Minutes 6-15**: Use Case Diagram
- Add all actors and use cases
- Connect relationships
- Format and style

### **Minutes 16-25**: Class Diagram
- Add all classes
- Add key attributes and methods
- Connect relationships
- Format and style

### **Minutes 26-30**: Sequence Diagrams
- Create User Login sequence
- Create Menu Verification sequence
- Format and style
- Export all diagrams

## 🆘 **Emergency Troubleshooting**

### **Can't see Palette?**
Window → Show View → Palette

### **Can't see Properties?**
Window → Show View → Properties

### **Can't see Project Explorer?**
Window → Show View → Project Explorer

### **Everything looks wrong?**
Window → Reset Perspective

---

**You're ready to create professional UML diagrams in 30 minutes!** 🎓
