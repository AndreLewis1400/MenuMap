# MenuMap Application
## CEN4010 Software Engineering - Team 9

[![Project Status](https://img.shields.io/badge/Status-In%20Development-blue.svg)](https://github.com/AndreLewis1400/MenuMap)
[![Course](https://img.shields.io/badge/Course-CEN4010%20Software%20Engineering-green.svg)](https://github.com/AndreLewis1400/MenuMap)
[![Team](https://img.shields.io/badge/Team-Team%209-orange.svg)](https://github.com/AndreLewis1400/MenuMap)

---

## 🍽️ Project Overview

**MenuMap** is a comprehensive restaurant discovery and menu management application designed to help users find, explore, and manage restaurant menus and meal information. Think of it as a "Google Maps for restaurant menus" - a centralized platform where food enthusiasts can discover new restaurants, browse detailed menus, save their favorites, and verify menu information accuracy.

### 🎯 Mission Statement
Create a user-friendly platform that bridges the gap between restaurants and customers by providing accurate, up-to-date menu information in an easily accessible format.

---

## 📋 Project Information

| Field | Details |
|-------|---------|
| **Project Name** | MenuMap |
| **Course** | CEN4010 Software Engineering |
| **Team** | Team 9 |
| **Project Lead** | Alfonso Oramas Jr. |
| **UML Diagrams Coordinator** | Andre Lewis |
| **Repository** | [AndreLewis1400/MenuMap](https://github.com/AndreLewis1400/MenuMap) |
| **Documentation Status** | ✅ Complete |
| **UML Diagrams** | ✅ Complete |
| **Use Cases** | ✅ Complete |

---

## 🚀 Core Features

### 🔍 **Menu Discovery & Browsing**
- Browse restaurant menus by location, cuisine type, or restaurant name
- View detailed menu items with descriptions, prices, and nutritional information
- Advanced search functionality with filters (price range, dietary restrictions, ratings)

### ⭐ **Favorites Management**
- Save favorite restaurants and specific menu items
- Organize favorites into custom categories
- Quick access to saved items for easy reordering

### ✅ **Content Verification System (TM901)**
- Automated verification of menu information accuracy
- Flag suspicious or inconsistent data
- Community-driven verification process
- Restaurant owner verification capabilities

### 🛡️ **Spam Protection System (TM902)**
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

## 📚 Documentation Structure

```
MenuMap_Project/
├── README.md                           # This file - Project overview
├── MenuMap_Project_Overview.md         # Comprehensive project overview
├── Requirements_Document/
│   └── Software_Requirements_Document.md  # Complete SRD
├── Use_Cases/
│   ├── Use_Case_Documentation.md       # 3 detailed use cases
│   └── Use_Case_Diagrams.md           # Visual use case diagrams
├── UML_Design/
│   ├── Use_Case_Diagram_Specification.md
│   ├── Class_Diagram_Specification.md
│   ├── Sequence_Diagram_Specifications.md
│   └── Step_by_Step_Papyrus_Instructions.md
└── SUBMISSION_CHECKLIST.md            # Project completion checklist
```

---

## 🎯 Required Use Cases

This project includes **3 comprehensive use cases** as required for CEN4010:

### 1. **UC-001: Browse Restaurant Menus** (Normal Use Case)
- **Description**: Users search and browse restaurant menus
- **Actors**: User, Restaurant Owner, MenuMap System
- **Priority**: High
- **Complexity**: Medium

### 2. **UC-002: Manage Favorites** (Normal Use Case)
- **Description**: Registered users save and organize favorite restaurants and meals
- **Actors**: Registered User, MenuMap System
- **Priority**: High
- **Complexity**: Medium

### 3. **UC-003: Secure Password Reset** (Security Use Case)
- **Description**: Secure password reset with fraud prevention
- **Actors**: User, MenuMap System, Email Service
- **Priority**: High
- **Complexity**: High
- **Security Focus**: Prevents misuse cases like account takeover

---

## 🏗️ Technical Architecture

### **Platform & Technology Stack**
- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Backend**: Node.js/Python/Java (to be determined)
- **Database**: MySQL/PostgreSQL
- **Authentication**: OAuth 2.0, JWT tokens
- **Security**: HTTPS encryption, secure authentication protocols

### **System Requirements**
- **Performance**: Page loads within 3 seconds
- **Scalability**: Support 1,000 concurrent users
- **Availability**: 99.9% uptime
- **Security**: OWASP security guidelines compliance
- **Usability**: WCAG 2.1 AA accessibility compliance

---

## 👥 Team Structure

### **Team 9 Members**
- **Alfonso Oramas Jr.**: Project Lead
- **Andre Lewis**: UML Diagrams Coordinator & Document Editor
- **Eve**: Team Member
- **Alex**: Team Member
- **Kamal**: Team Member

### **Responsibilities**
- **Alfonso Oramas Jr.**: Project coordination, presentation leadership, overall project management
- **Andre Lewis**: UML diagram creation and maintenance, documentation, system design
- **Eve**: [Role to be assigned]
- **Alex**: [Role to be assigned]
- **Kamal**: [Role to be assigned]

---

## 📊 Project Status

### ✅ **Completed Deliverables**
- [x] Software Requirements Document (SRD)
- [x] Use Case Documentation (3 use cases)
- [x] Use Case Diagrams (Individual diagrams for each use case)
- [x] UML Design Specifications
- [x] Project Overview Documentation
- [x] GitHub Repository Setup

### 🔄 **In Progress**
- [ ] Eclipse Papyrus UML Diagrams
- [ ] Presentation Materials
- [ ] Final Documentation Review

### ⏳ **Upcoming**
- [ ] Prototype Development
- [ ] User Interface Design
- [ ] Database Schema Implementation
- [ ] Security Implementation

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

## 🚀 Getting Started

### **For Team Members**
1. Clone the repository: `git clone https://github.com/AndreLewis1400/MenuMap.git`
2. Review the documentation in the `Requirements_Document/` folder
3. Check the `Use_Cases/` folder for detailed use case information
4. Follow the UML design specifications in the `UML_Design/` folder

### **For Stakeholders**
1. Read the `MenuMap_Project_Overview.md` for comprehensive project information
2. Review the `Software_Requirements_Document.md` for technical specifications
3. Check the use case documentation for feature details

---

## 📞 Contact & Support

**Project Repository**: [AndreLewis1400/MenuMap](https://github.com/AndreLewis1400/MenuMap)  
**Course**: CEN4010 Software Engineering  
**Team**: Team 9  
**Project Lead**: Andre Lewis  

---

## 📄 License

This project is developed for educational purposes as part of the CEN4010 Software Engineering course. All documentation and code are created by Team 9 members.

---

## 🙏 Acknowledgments

- **Course Instructor**: [Instructor Name]
- **Team 9 Members**: [Team Member Names]
- **CEN4010 Software Engineering Course**: Florida International University

---

*This repository contains all documentation, use cases, and design specifications for the MenuMap application developed by Team 9 for CEN4010 Software Engineering.*
