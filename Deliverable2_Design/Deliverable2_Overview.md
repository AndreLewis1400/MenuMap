# MenuMap Deliverable 2 - Design Document
## CEN4010 Software Engineering - Team 9

**Project:** MenuMap Application  
**Team:** Team 9  
**Software Architecture & Design Lead:** Andre Lewis  
**Date:** [Current Date]  
**Version:** 1.0  

---

## 🎯 Deliverable 2 Overview

This document outlines the design phase for the MenuMap application, focusing on software architecture, detailed design, and UML modeling for the 7 use cases selected for implementation.

---

## 📋 7 Use Cases Selected for Implementation

Based on the deliverable 2 requirements, we will implement the following 7 use cases:

### **Core Use Cases (3 from Deliverable 1)**
1. **UC-001: Browse Restaurant Menus** (Normal Use Case)
2. **UC-002: Manage Favorites** (Normal Use Case)  
3. **UC-003: Secure Password Reset** (Security Use Case)

### **Additional Use Cases (4 to be defined)**
4. **UC-004: User Registration** (Normal Use Case)
5. **UC-005: User Login** (Normal Use Case)
6. **UC-006: User Logout** (Normal Use Case)
7. **UC-007: Restaurant Owner Menu Management** (Normal Use Case)

---

## 🏗️ Architectural Patterns Selected

### **Primary Pattern: 3-Tier Architecture**
**Reasons for Selection:**
1. **Clear Separation**: Distinct separation between Presentation, Business Logic, and Data tiers
2. **Scalability**: Each tier can be scaled independently based on demand
3. **Maintainability**: Changes in one tier don't affect others
4. **Team Development**: Different teams can work on different tiers
5. **Technology Flexibility**: Each tier can use optimal technologies

### **Secondary Pattern: Model-View-Controller (MVC)**
**Reasons for Selection:**
1. **User Interface Separation**: Clean separation between UI and business logic
2. **Reusability**: Business logic can be reused across different interfaces
3. **Testing**: Each component can be tested independently
4. **Industry Standard**: Well-established pattern with extensive tooling support

### **3-Tier Architecture Overview:**
- **Tier 1 (Presentation)**: Web Interface, Mobile Interface, API Interface
- **Tier 2 (Business Logic)**: Use Case Controllers, Business Services, Security Services
- **Tier 3 (Data)**: Database, Cache Layer, File Storage

---

## 📊 Deliverable 2 Structure

```
Deliverable2_Design/
├── Architecture/
│   ├── Package_Diagram.md
│   ├── Subsystem_Decomposition.md
│   ├── Hardware_Software_Mapping.md
│   └── Security_Management.md
├── UML_Diagrams/
│   ├── Use_Case_Diagram.md
│   ├── Architecture_Package_Diagram.md
│   ├── Minimal_Class_Diagram.md
│   ├── Detailed_Class_Diagram.md
│   ├── State_Machine_Diagram.md
│   └── Sequence_Diagrams.md
├── Design_Patterns/
│   ├── Observer_Pattern.md
│   ├── Factory_Pattern.md
│   └── Strategy_Pattern.md
└── Documentation/
    ├── Design_Document.md
    ├── Meeting_Diary.md
    └── OCL_Statements.md
```

---

## 🎯 Next Steps

1. **Create Package Diagram** - Define major subsystems
2. **Design Subsystem Decomposition** - Detail each subsystem
3. **Select 3 Design Patterns** - Observer, Factory, Strategy
4. **Create UML Diagrams in Papyrus** - All 6 required diagrams
5. **Write OCL Statements** - For control objects
6. **Complete Design Document** - All sections

---

*This overview provides the foundation for MenuMap's deliverable 2 design phase.*
