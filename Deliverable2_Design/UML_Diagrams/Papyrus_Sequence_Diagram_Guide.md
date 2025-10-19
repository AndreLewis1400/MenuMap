# Papyrus Sequence Diagram Implementation Guide
## MenuMap Application - Team 9

**Software Architecture & Design Lead:** Andre Lewis  
**Date:** [Current Date]  
**Version:** 1.0  

---

## 🎯 Overview

This guide provides step-by-step instructions for creating the 7 sequence diagrams in Eclipse Papyrus for the MenuMap application.

---

## 📋 Prerequisites

1. **Eclipse Papyrus** installed and running
2. **MenuMap UML Project** already created
3. **Sequence Diagram Specifications** reviewed (from Sequence_Diagrams.md)

---

## 🚀 Step-by-Step Implementation

### **Step 1: Create Sequence Diagram Files**

For each use case, create a new sequence diagram:

1. **Right-click** on your MenuMap model in Model Explorer
2. **Select** "New Child" → "Sequence Diagram"
3. **Name** each diagram as follows:
   - `UC001_BrowseRestaurantMenus_Sequence`
   - `UC002_ManageFavorites_Sequence`
   - `UC003_SecurePasswordReset_Sequence`
   - `UC004_UserRegistrationLogin_Sequence`
   - `UC005_MenuVerificationSystem_Sequence`
   - `UC006_SpamProtectionSystem_Sequence`
   - `UC007_RestaurantOwnerMenuManagement_Sequence`

### **Step 2: Add Lifelines (Participants)**

For each sequence diagram, add the following lifelines:

#### **UC-001: Browse Restaurant Menus**
```
- User (Actor)
- WebInterface (Boundary)
- MenuController (Control)
- Database (Entity)
- Restaurant (Entity)
- Menu (Entity)
```

#### **UC-002: Manage Favorites**
```
- User (Actor)
- WebInterface (Boundary)
- UserController (Control)
- AuthenticationService (Control)
- Database (Entity)
- Favorite (Entity)
```

#### **UC-003: Secure Password Reset**
```
- User (Actor)
- WebInterface (Boundary)
- AuthenticationService (Control)
- EmailService (External)
- Database (Entity)
- SecurityLogger (Control)
```

#### **UC-004: User Registration & Login**
```
- User (Actor)
- WebInterface (Boundary)
- AuthenticationService (Control)
- UserController (Control)
- Database (Entity)
- EmailService (External)
```

#### **UC-005: Menu Verification System**
```
- Restaurant Owner (Actor)
- Administrator (Actor)
- WebInterface (Boundary)
- MenuController (Control)
- VerificationSystem (Control)
- Database (Entity)
- Report (Entity)
```

#### **UC-006: Spam Protection System**
```
- User (Actor)
- Administrator (Actor)
- WebInterface (Boundary)
- SpamProtection (Control)
- Database (Entity)
- Alert (Entity)
```

#### **UC-007: Restaurant Owner Menu Management**
```
- Restaurant Owner (Actor)
- WebInterface (Boundary)
- MenuController (Control)
- AuthenticationService (Control)
- Database (Entity)
- Menu (Entity)
- MenuItem (Entity)
```

### **Step 3: Add Messages and Interactions**

For each sequence diagram, follow the message flow from the specifications:

#### **Message Types to Use:**
- **Synchronous Call**: Solid arrow with filled arrowhead
- **Asynchronous Call**: Solid arrow with open arrowhead
- **Return Message**: Dashed arrow
- **Self Message**: Arrow pointing back to same lifeline

#### **Message Naming Convention:**
```
1. enterSearchCriteria()
2. searchMenus(query, filters)
3. findRestaurants(criteria)
4. return restaurantList
```

### **Step 4: Add Activation Boxes**

1. **Click** on each message arrow
2. **Right-click** → "Properties"
3. **Check** "Activation" to show activation boxes
4. **Position** activation boxes to show method execution duration

### **Step 5: Add Alternative Flows (Alt Frames)**

For use cases with alternative flows:

1. **Select** "Interaction Use" from the palette
2. **Draw** a rectangle around the alternative flow
3. **Label** it as "alt [condition]"
4. **Add** the alternative message flow inside

#### **Example Alt Frame for UC-001:**
```
alt No Results Found
    Database -> MenuController: return emptyList
    MenuController -> WebInterface: return noResults
    WebInterface -> User: display "No results found"
```

### **Step 6: Add Notes and Comments**

1. **Select** "Comment" from the palette
2. **Add** explanatory notes for complex interactions
3. **Connect** notes to relevant messages with dashed lines

---

## 🎨 Visual Formatting Guidelines

### **Lifeline Spacing:**
- **Actors**: Place on far left and right
- **Boundary Objects**: Place after actors
- **Control Objects**: Place in center
- **Entity Objects**: Place on far right

### **Message Layout:**
- **Top-to-bottom** chronological order
- **Consistent spacing** between messages
- **Clear labeling** with step numbers

### **Color Coding:**
- **Actors**: Light blue
- **Boundary**: Light green
- **Control**: Light yellow
- **Entity**: Light gray

---

## 📊 Implementation Checklist

### **For Each Sequence Diagram:**

- [ ] **Lifelines Created**: All participants added
- [ ] **Messages Added**: All interactions from specifications
- [ ] **Activation Boxes**: Method execution shown
- [ ] **Alternative Flows**: Alt frames for error conditions
- [ ] **Return Messages**: Dashed arrows for responses
- [ ] **Self Messages**: Internal method calls shown
- [ ] **Notes Added**: Complex interactions explained
- [ ] **Formatting Applied**: Consistent spacing and colors
- [ ] **Validation Passed**: No syntax errors

### **Overall Project:**

- [ ] **All 7 Diagrams Created**: Complete set
- [ ] **Consistent Naming**: Following conventions
- [ ] **Professional Appearance**: Clean, readable diagrams
- [ ] **Export Ready**: Diagrams can be exported as images

---

## 🔧 Troubleshooting

### **Common Issues:**

1. **Lifeline Not Showing**: Check if lifeline is properly connected to class
2. **Message Not Appearing**: Ensure message is connected to lifelines
3. **Activation Box Missing**: Check message properties for activation
4. **Alt Frame Not Working**: Ensure proper nesting of messages

### **Papyrus Tips:**

1. **Use Grid**: Enable grid for better alignment
2. **Zoom In**: Use zoom for detailed work
3. **Save Frequently**: Save after each major change
4. **Validate**: Use Model Validation to check for errors

---

## 📤 Export Instructions

### **Export as Images:**

1. **Right-click** on each sequence diagram
2. **Select** "Export" → "Export as Image"
3. **Choose** PNG format for best quality
4. **Set** resolution to 300 DPI for print quality
5. **Save** with descriptive filename

### **Export as PDF:**

1. **Select** all sequence diagrams
2. **Right-click** → "Export" → "Export as PDF"
3. **Choose** "All diagrams in one PDF"
4. **Save** as "MenuMap_Sequence_Diagrams.pdf"

---

## 🎯 Next Steps

After completing all sequence diagrams:

1. **Review** each diagram against specifications
2. **Export** all diagrams as images
3. **Add** to design document
4. **Prepare** for team review
5. **Update** project documentation

---

*This guide provides comprehensive instructions for implementing all 7 sequence diagrams in Eclipse Papyrus for the MenuMap application.*
