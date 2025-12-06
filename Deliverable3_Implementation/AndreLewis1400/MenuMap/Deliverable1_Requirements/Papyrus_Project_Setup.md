# Eclipse Papyrus UML Project Setup Guide

## Project Structure for MenuMap UML Design

### 1. Eclipse Papyrus Project Creation
1. Open Eclipse IDE
2. Install Papyrus if not already installed:
   - Help → Eclipse Marketplace
   - Search for "Papyrus"
   - Install "Papyrus for UML"

### 2. Create New Papyrus Project
1. File → New → Papyrus Project
2. Project Name: `MenuMap_UML_Design`
3. Select UML as the modeling language
4. Choose appropriate UML profiles

### 3. Required UML Diagrams

#### 3.1 Use Case Diagram
- **File**: `MenuMap_UseCase_Diagram.uml`
- **Actors**: 
  - User (Primary)
  - Restaurant Owner (Secondary)
  - Administrator (Secondary)
- **Use Cases**:
  - TM901 - Menu Verification
  - TM902 - Spam Protection
  - Password Reset
  - Manage Favorites
  - Delete Meal Entry
  - Browse Menus
  - Search Restaurants

#### 3.2 Class Diagram
- **File**: `MenuMap_Class_Diagram.uml`
- **Key Classes**:
  - User
  - Restaurant
  - MenuItem
  - Favorite
  - VerificationSystem
  - SpamProtection
  - AuthenticationService

#### 3.3 Sequence Diagrams
- **File**: `MenuMap_Sequence_Diagrams.uml`
- **Scenarios**:
  - User Login Process
  - Menu Verification Process
  - Spam Detection Process
  - Password Reset Process

#### 3.4 Activity Diagrams
- **File**: `MenuMap_Activity_Diagrams.uml`
- **Processes**:
  - User Registration Flow
  - Menu Search Flow
  - Favorites Management Flow

#### 3.5 Component Diagram
- **File**: `MenuMap_Component_Diagram.uml`
- **Components**:
  - Web Interface
  - Mobile App
  - Database
  - Authentication Service
  - Email Service

### 4. Project Organization
```
MenuMap_UML_Design/
├── diagrams/
│   ├── usecase/
│   │   └── MenuMap_UseCase_Diagram.uml
│   ├── class/
│   │   └── MenuMap_Class_Diagram.uml
│   ├── sequence/
│   │   └── MenuMap_Sequence_Diagrams.uml
│   ├── activity/
│   │   └── MenuMap_Activity_Diagrams.uml
│   └── component/
│       └── MenuMap_Component_Diagram.uml
├── models/
│   └── MenuMap_Model.uml
└── profiles/
    └── MenuMap_Profile.uml
```

### 5. Export Requirements
- Export all diagrams as PNG/PDF for documentation
- Maintain .uml files for future modifications
- Create a comprehensive model overview

### 6. Integration with Requirements Document
- Link UML elements to specific requirements
- Maintain traceability between use cases and implementation
- Document design decisions and rationale

## Next Steps
1. Create the Papyrus project in Eclipse
2. Develop each UML diagram according to specifications
3. Export diagrams for inclusion in final submission
4. Review and validate against requirements document
