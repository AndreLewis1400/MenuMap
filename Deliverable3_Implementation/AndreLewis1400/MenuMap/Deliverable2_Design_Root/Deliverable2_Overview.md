# MenuMap Deliverable 2 - Design Document
## CEN4010 Software Engineering - Team 9

**Project:** MenuMap Application 
**Team:** Team 9 
**Software Architecture & Design Lead:** Andre Lewis 
**Date:** [Current Date] 
**Version:** 1.0 

---

## Deliverable 2 Overview

This document outlines the design phase for the MenuMap application, focusing on software architecture, detailed design, and UML modeling for the 7 use cases selected for implementation.

---

## 7 Use Cases Selected for Implementation

Based on the deliverable 2 requirements, we will implement the following 7 use cases:

### **Core Use Cases (3 from Deliverable 1)**
1. **UC-001: Browse Restaurant Menus** (Normal Use Case)
2. **UC-002: Manage Favorites** (Normal Use Case) 
3. **UC-003: Secure Password Reset** (Security Use Case)

### **Additional Use Cases (4 to be defined)**
4. **UC-004: User Registration & Login** (Normal Use Case)
5. **UC-005: Menu Verification System** (Security Use Case - TM901)
6. **UC-006: Spam Protection System** (Security Use Case - TM902)
7. **UC-007: Restaurant Owner Menu Management** (Normal Use Case)

---

## Architectural Patterns Selected

### **Primary Pattern: Layered Architecture**
**Reasons for Selection:**
1. **Separation of Concerns**: Clear separation between presentation, business logic, and data layers
2. **Maintainability**: Easy to modify individual layers without affecting others
3. **Scalability**: Each layer can be scaled independently
4. **Team Development**: Different team members can work on different layers

### **Secondary Pattern: Model-View-Controller (MVC)**
**Reasons for Selection:**
1. **User Interface Separation**: Clean separation between UI and business logic
2. **Reusability**: Business logic can be reused across different interfaces
3. **Testing**: Each component can be tested independently
4. **Industry Standard**: Well-established pattern with extensive tooling support

---

## Deliverable 2 Structure

```
Deliverable2_Design/
├── Architecture/
│ ├── Package_Diagram.md
│ ├── Subsystem_Decomposition.md
│ ├── Hardware_Software_Mapping.md
│ └── Security_Management.md
├── UML_Diagrams/
│ ├── Use_Case_Diagram.md
│ ├── Architecture_Package_Diagram.md
│ ├── Minimal_Class_Diagram.md
│ ├── Detailed_Class_Diagram.md
│ ├── State_Machine_Diagram.md
│ └── Sequence_Diagrams.md
├── Design_Patterns/
│ ├── Observer_Pattern.md
│ ├── Factory_Pattern.md
│ └── Strategy_Pattern.md
└── Documentation/
 ├── Design_Document.md
 ├── Meeting_Diary.md
 └── OCL_Statements.md
```

---

## Next Steps

1. **Create Package Diagram** - Define major subsystems
2. **Design Subsystem Decomposition** - Detail each subsystem
3. **Select 3 Design Patterns** - Observer, Factory, Strategy
4. **Create UML Diagrams in Papyrus** - All 6 required diagrams
5. **Write OCL Statements** - For control objects
6. **Complete Design Document** - All sections

---

*This overview provides the foundation for MenuMap's deliverable 2 design phase.*
