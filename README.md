# MenuMap Application
## CEN4010 Software Engineering - Team 9

[![Project Status](https://img.shields.io/badge/Status-Deliverable%202%20Complete-green.svg)](https://github.com/AndreLewis1400/MenuMap)
[![Course](https://img.shields.io/badge/Course-CEN4010%20Software%20Engineering-green.svg)](https://github.com/AndreLewis1400/MenuMap)
[![Team](https://img.shields.io/badge/Team-Team%209-orange.svg)](https://github.com/AndreLewis1400/MenuMap)

**Project:** MenuMap Application  
**Team:** Team 9  
**Software Architecture & Design Lead:** Andre Lewis  
**Repository:** AndreLewis1400/MenuMap  
**Date:** [Current Date]  
**Version:** 1.0  

---

## 🎯 Project Overview

MenuMap is a comprehensive restaurant menu browsing and management system designed to connect users with restaurant menus while providing restaurant owners with tools to manage their digital presence. Think of it as a "Google Maps for restaurant menus" - a centralized platform where food enthusiasts can discover new restaurants, browse detailed menus, save their favorites, and verify menu information accuracy.

### **Mission Statement**
Create a user-friendly platform that bridges the gap between restaurants and customers by providing accurate, up-to-date menu information in an easily accessible format.

---

## 📋 Project Information

| Field | Details |
|-------|---------|
| **Project Name** | MenuMap |
| **Course** | CEN4010 Software Engineering |
| **Team** | Team 9 |
| **Software Architecture & Design Lead** | Andre Lewis |
| **Repository** | [AndreLewis1400/MenuMap](https://github.com/AndreLewis1400/MenuMap) |
| **Documentation Status** | ✅ Complete |
| **UML Diagrams** | ✅ Complete |
| **Use Cases** | ✅ Complete (7 use cases) |
| **Deliverable 1** | ✅ Complete |
| **Deliverable 2** | ✅ Complete |

---

## 🚀 Core Features

### **7 Comprehensive Use Cases:**

- **UC-001**: Browse Restaurant Menus
- **UC-002**: Manage Favorites
- **UC-003**: Secure Password Reset
- **UC-004**: Registration & Login
- **UC-005**: Menu Verification System
- **UC-006**: Spam Protection System
- **UC-007**: Menu Management

### 🔍 **Menu Discovery & Browsing**
- Browse restaurant menus by location, cuisine type, or restaurant name
- View detailed menu items with descriptions, prices, and nutritional information
- Advanced search functionality with filters (price range, dietary restrictions, ratings)

### ⭐ **Favorites Management**
- Save favorite restaurants and specific menu items
- Organize favorites into custom categories
- Quick access to saved items for easy reordering

### ✅ **Content Verification System (UC-005)**
- Automated verification of menu information accuracy
- Flag suspicious or inconsistent data
- Community-driven verification process
- Restaurant owner verification capabilities

### 🛡️ **Spam Protection System (UC-006)**
- Advanced spam detection algorithms
- Rate limiting for submissions
- Blacklist management for known spam sources
- User reporting system for suspicious content

### 🔒 **Security Features**
- Secure user authentication and authorization
- Password reset functionality with email verification
- Data encryption and privacy protection
- Audit trails for all user actions

---

## 📁 Project Structure

```
MenuMap_Project/
├── README.md                           # This file - Project overview
├── Deliverable1_Requirements/          # Requirements and Analysis
│   ├── Software_Requirements_Document.md
│   ├── Use_Cases/
│   │   ├── UC-001-Browse_Restaurant_Menus.md
│   │   ├── UC-002-Manage_Favorites.md
│   │   ├── UC-003-Secure_Password_Reset.md
│   │   ├── UC-004-Registration_Login.md
│   │   ├── UC-005-Menu_Verification_System.md
│   │   ├── UC-006-Spam_Protection_System.md
│   │   └── UC-007-Menu_Management.md
│   ├── UML_Diagrams/
│   │   ├── Use_Case_Diagram.md
│   │   ├── Class_Diagram.md
│   │   └── Sequence_Diagrams.md
│   └── Documentation/
│       ├── Requirements_Analysis.md
│       └── Use_Case_Specifications.md
└── Deliverable2_Design/                # Design and Architecture (CLEAN)
    ├── README.md                        # Clean overview
    ├── PRIMARY_SECONDARY_COMPONENTS.md  # Clear primary/secondary explanation
    ├── Architecture/                    # 4 essential files
    │   ├── Package_Diagram.md
    │   ├── Subsystem_Decomposition.md
    │   ├── Hardware_Software_Mapping.md
    │   └── Security_Management.md
    ├── UML_Diagrams/                    # Essential diagrams only
    │   ├── Use_Case_Diagram.md
    │   ├── UC-001-Browse_Restaurant_Menus_Sequence.md
    │   ├── UC-002-Manage_Favorites_Sequence.md
    │   ├── UC-006-User_Logout_Sequence.md
    │   └── Diagrams_Only/               # PNG files
    │       ├── Model_Static_Menu_map_3_tier.PNG
    │       ├── Package_MM_Client_MM_Client_Class_Dia.PNG
    │       ├── Package_MM_Logic_MM_Logic_Class_Dia.PNG
    │       └── Package_MM_DataStore_MM_Data_Store_Dia.PNG
    ├── Design_Patterns/                 # 3 pattern files
    │   ├── Observer_Pattern.md
    │   ├── Factory_Pattern.md
    │   └── Strategy_Pattern.md
    └── Documentation/                   # 3 doc files
        ├── Design_Document.md
        ├── Meeting_Diary.md
        └── OCL_Statements.md
```

---

## 🚀 Getting Started

### **Prerequisites**
- Java 11+
- Spring Boot 2.7+
- PostgreSQL 13+
- Redis 6+
- Node.js 16+
- React 18+

### **Installation**
1. Clone the repository: `git clone https://github.com/AndreLewis1400/MenuMap.git`
2. Set up the database
3. Configure environment variables
4. Run the application

### **Development**
- Follow the design specifications in Deliverable2_Design/
- Use the UML diagrams for implementation guidance
- Follow the OCL constraints for business rules

---

## 📊 Deliverables

### **Deliverable 1: Requirements & Analysis** ✅ Complete
- ✅ Software Requirements Document
- ✅ Use Case Specifications (7 use cases)
- ✅ UML Use Case Diagram
- ✅ Requirements Analysis

### **Deliverable 2: Design & Architecture** ✅ Complete
- ✅ Software Architecture Design
- ✅ Detailed Design Specifications
- ✅ UML Diagrams (7 sequence diagrams)
- ✅ Design Patterns Implementation
- ✅ OCL Statements (100+ constraints)
- ✅ Comprehensive Documentation

---

## 🎯 Use Cases

| Use Case | Description | Status | Complexity |
|----------|-------------|--------|------------|
| UC-001 | Browse Restaurant Menus | ✅ Complete | Medium |
| UC-002 | Manage Favorites | ✅ Complete | Medium |
| UC-003 | Secure Password Reset | ✅ Complete | High |
| UC-004 | Registration & Login | ✅ Complete | Medium |
| UC-005 | Menu Verification System | ✅ Complete | High |
| UC-006 | Spam Protection System | ✅ Complete | High |
| UC-007 | Menu Management | ✅ Complete | Medium |

---

## 🏗️ Architecture

### **Architectural Patterns**
- **Primary**: 3-Tier Architecture (MM_Client, MM_Logic, MM_DataStore)
- **Secondary**: Model-View-Controller (MVC)

### **Design Patterns**
- **Observer Pattern**: Real-time updates and notifications
- **Factory Pattern**: Object creation without specifying classes
- **Strategy Pattern**: Interchangeable algorithms

### **Technology Stack**
- **Backend**: Java Spring Boot
- **Frontend**: React with TypeScript
- **Database**: PostgreSQL with Redis caching
- **Security**: Spring Security with JWT

### **System Requirements**
- **Performance**: Page loads within 3 seconds
- **Scalability**: Support 1,000 concurrent users
- **Availability**: 99.9% uptime
- **Security**: OWASP security guidelines compliance
- **Usability**: WCAG 2.1 AA accessibility compliance

---

## 📈 Project Status

### **Completed** ✅
- ✅ Requirements Analysis
- ✅ Use Case Specifications (7 use cases)
- ✅ Software Architecture Design
- ✅ Detailed Design
- ✅ UML Modeling (7 sequence diagrams)
- ✅ Design Patterns
- ✅ Security Design
- ✅ OCL Statements (100+ constraints)
- ✅ Comprehensive Documentation
- ✅ Meeting Diary
- ✅ Final Review & Validation

### **In Progress** 🔄
- 🔄 Implementation (Ready to begin)

### **Planned** ⏳
- ⏳ Testing
- ⏳ Deployment
- ⏳ User Acceptance Testing

---

## 👥 Team

### **Team 9 Members**
- **Andre Lewis**: Software Architecture & Design Lead
- **Alfonso Oramas Jr.**: Project Lead
- **Alex**: Team Member
- **Eve**: Team Member
- **Kamal**: Team Member

### **Responsibilities**
- **Andre Lewis**: UML diagram creation, system design, architecture, documentation
- **Alfonso Oramas Jr.**: Project coordination, presentation leadership
- **Alex**: [Role to be assigned]
- **Eve**: [Role to be assigned]
- **Kamal**: [Role to be assigned]

---

## 🔒 Security & Compliance

### **Security Features**
- **Data Protection**: GDPR and CCPA compliance
- **Authentication**: Secure user login and session management
- **Authorization**: Role-based access control
- **Audit Trail**: Comprehensive logging of user actions
- **Encryption**: Industry-standard encryption algorithms

### **Misuse Case Prevention**
- **Password Reset Security**: Multi-layer verification to prevent account takeover
- **Spam Protection**: Advanced algorithms to detect and prevent malicious content
- **Rate Limiting**: Prevents brute force attacks
- **Content Verification**: Ensures menu information accuracy

---

## 📈 Success Metrics

### **Technical Metrics**
- System performance benchmarks
- Security compliance scores
- Code quality metrics
- Test coverage percentages

### **User Experience Metrics**
- User satisfaction ratings
- Feature adoption rates
- System usability scores
- Accessibility compliance

---

## 📞 Contact & Support

**Project Repository**: [AndreLewis1400/MenuMap](https://github.com/AndreLewis1400/MenuMap)  
**Course**: CEN4010 Software Engineering  
**Team**: Team 9  
**Software Architecture & Design Lead**: Andre Lewis  

---

## 📄 License

This project is developed for educational purposes as part of the CEN4010 Software Engineering course. All documentation and code are created by Team 9 members.

---

## 🙏 Acknowledgments

- **Course Instructor**: [Instructor Name]
- **Team 9 Members**: [Team Member Names]
- **CEN4010 Software Engineering Course**: Florida International University

---

*This repository contains all documentation, use cases, UML diagrams, and design specifications for the MenuMap application developed by Team 9 for CEN4010 Software Engineering. Both Deliverable 1 and Deliverable 2 are complete with professional-grade architecture, design, and documentation.*