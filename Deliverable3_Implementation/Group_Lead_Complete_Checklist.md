# Group Lead Complete Checklist - Deliverable 3
## Andre Lewis - Final Action Plan

**Last Updated:** Today 
**Status:** Test Cases Updated | Chapters 5 & 6 Pending

---

## COMPLETED TASKS

### **1. Test Cases (Chapter 7 Contribution)** 
- **UC-005: User Login** - 10 test cases (2 sunny day, 8 rainy day)
- **UC-001: Browse Restaurant Menus** - 8 test cases (2 sunny day, 6 rainy day)
- **Updated:** All test cases now specify user names (e.g., "janedoe", "johndoe") and restaurant names (e.g., "Joe's Pizza", "Burger Palace")
- **File:** `MenuMap_Test_Cases_Login_UC001.md`
- **Pushed to GitHub:** Yes
- **Status:** Complete and ready for Chapter 7.1.3 inclusion

### **2. Team Coordination** 
- Created `Test_Case_Assignments.md` - Team member assignments
- Created `Chapter_7_Test_Cases_Structure.md` - Compilation guide
- Created `Test_Cases_Summary.md` - Quick reference
- Created `Group_Lead_Remaining_Tasks.md` - Task checklist

---

## REMAINING TASKS (Your Primary Responsibilities)

### **Chapter 5: Software Architecture** (7 points) HIGH PRIORITY
**Status:** Pending 
**Timeline:** Complete Today/Tomorrow 
**Reference:** `Deliverable2_Design/Architecture/` - Use as starting point with corrections

#### **Required Sections:**

**5.0 Introduction** (1-2 paragraphs)
- [ ] Write introduction to software architecture chapter
- [ ] Overview of architectural decisions for MenuMap

**5.1 Overview** (2 points)
- [ ] Reference: `Deliverable2_Design/Architecture/Package_Diagram.md`
- [ ] High-level architecture description
- [ ] Architectural patterns used (3-tier: MM_Client, MM_Logic, MM_DataStore)
- [ ] Secondary patterns (MVC, Observer, Factory, Strategy)

**5.2 Subsystem Decomposition** (2 points)
- [ ] Reference: `Deliverable2_Design/Architecture/Subsystem_Decomposition.md`
- [ ] Break down system into 7 subsystems:
 - Presentation Layer
 - Business Logic Layer
 - Data Access Layer
 - Security Subsystem
 - Menu Management Subsystem
 - User Management Subsystem
 - Notification Subsystem
- [ ] Describe subsystem responsibilities
- [ ] Show subsystem relationships

**5.3 Hardware and Software Mapping** (1 point)
- [ ] Reference: `Deliverable2_Design/Architecture/Hardware_Software_Mapping.md`
- [ ] Map software components to hardware
- [ ] Deployment architecture (AWS cloud infrastructure)
- [ ] Technology stack (React, Node.js, PostgreSQL, etc.)

**5.4 Persistent Data Management** (1 point)
- [ ] Database design (PostgreSQL)
- [ ] Data storage strategy
- [ ] Data access patterns (Repository pattern)
- [ ] Cache management (Redis)

**5.5 Security Management** (1 point)
- [ ] Reference: `Deliverable2_Design/Architecture/Security_Management.md`
- [ ] Security architecture
- [ ] Authentication/authorization (JWT, Passport.js)
- [ ] Data protection (encryption, hashing)

**Action Items:**
- [ ] Review Deliverable 2 Design Document architecture sections
- [ ] Write Chapter 5 introduction
- [ ] Write Section 5.1 Overview
- [ ] Write Section 5.2 Subsystem Decomposition
- [ ] Write Section 5.3 Hardware and Software Mapping
- [ ] Write Section 5.4 Persistent Data Management
- [ ] Write Section 5.5 Security Management
- [ ] Review and update content (make corrections from Design Document)
- [ ] Add to Final Document (Word document)

---

### **Chapter 6: Detailed Design** (9 points) HIGH PRIORITY
**Status:** Pending 
**Timeline:** Complete Today/Tomorrow 
**Reference:** `Deliverable2_Design/UML_Diagrams/` - Use sequence diagrams and class diagrams 
**Support:** Alfonso Oramas (Class diagrams for Section 6.4)

#### **Required Sections:**

**6.0 Introduction** (1-2 paragraphs)
- [ ] Write introduction to detailed design chapter
- [ ] Overview of design decisions

**6.1 Overview (Minimum Class Diagram)** (2 points)
- [ ] Reference: `Deliverable2_Design/UML_Diagrams/Diagrams_Only/Package_MM_Clent_MM_Client_Class_Dia.PNG`
- [ ] High-level class diagram showing:
 - MM_Client package classes
 - MM_Logic package classes
 - MM_DataStore package classes
- [ ] Key classes and relationships
- [ ] Design patterns overview

**6.2 State Machine Model** (1 point)
- [ ] Reference: `Deliverable2_Design/UML_Diagrams/Diagrams_Only/State_Machine_UserAuthentication_StateMachine_MM_State_Machine_Dia.PNG`
- [ ] State diagrams for key entities (User Authentication)
- [ ] State transitions
- [ ] State management

**6.3 Object Interaction (Sequence Diagrams)** (3 points)
- [ ] Reference: `Deliverable2_Design/UML_Diagrams/` - Sequence diagrams for implemented use cases
- [ ] Include sequence diagrams for:
 - UC-001: Browse Restaurant Menus
 - UC-005: User Login
 - UC-004: User Registration (if implemented)
 - Other implemented use cases
- [ ] Show object interactions (3-tier architecture)
- [ ] Message flows between Presentation, Business Logic, and Data layers

**6.4 Detailed Class Design (Detailed Class Diagram)** (3 points)
- [ ] **Coordinate with Alfonso Oramas** - He's assigned to Appendix D (Detailed Class Diagrams)
- [ ] Reference: `Deliverable2_Design/UML_Diagrams/Diagrams_Only/`
- [ ] Detailed class diagrams with:
 - All attributes
 - All methods
 - Relationships and associations
 - Full class details
- [ ] Include diagrams for all three tiers:
 - MM_Client classes
 - MM_Logic classes
 - MM_DataStore classes

**Action Items:**
- [ ] Review Deliverable 2 Design Document UML diagrams
- [ ] Coordinate with Alfonso Oramas for class diagrams (Chapter 6.4)
- [ ] Write Chapter 6 introduction
- [ ] Write Section 6.1 Overview (with minimum class diagram)
- [ ] Write Section 6.2 State Machine Model
- [ ] Write Section 6.3 Object Interaction (sequence diagrams)
- [ ] Write Section 6.4 Detailed Class Design (with Alfonso's diagrams)
- [ ] Review and update content (make corrections from Design Document)
- [ ] Add to Final Document (Word document)

---

## ADDITIONAL GROUP LEAD RESPONSIBILITIES

### **1. Review & Coordination** MEDIUM PRIORITY
- [ ] Review all team members' test cases (Chapter 7) for quality
- [ ] Ensure format consistency across chapters
- [ ] Coordinate with team members on dependencies
- [ ] Review compiled Final Document before submission

### **2. Final Document Compilation** MEDIUM PRIORITY
- [ ] Ensure all chapters are complete
- [ ] Verify format requirements are met:
 - 1.5 line spacing
 - Chapter headings: 16 pt
 - Section headings: 13 pt
 - Text: 11pt Arial or 12pt Times
- [ ] Check table of contents accuracy
- [ ] Final review before submission

### **3. Team Support** LOW PRIORITY
- [ ] Answer questions from team members
- [ ] Provide guidance on format and requirements
- [ ] Resolve blockers and issues
- [ ] Coordinate deadlines

---

## REFERENCE DOCUMENTS

### **For Chapters 5 & 6:**
- **Deliverable 2 Design Document** - Primary reference
 - Location: `C:\Users\alewi\MenuMap\Deliverable2_Design\`
 - Architecture folder: `Architecture/`
 - UML Diagrams: `UML_Diagrams/`
 - Use similar content but make corrections/updates

### **For Format Requirements:**
- **CEN4010-Final.docx** - Format document (in Downloads folder)
- **CEN4010-GradeSheet_Deliver-3.docx** - Grading rubric (in Downloads folder)
- **Correct_Chapter_Structure.md** - Chapter structure requirements
- **Task_Delegation_By_Chapters.md** - Detailed requirements

### **For Test Cases:**
- **MenuMap_Test_Cases_Login_UC001.md** - Your completed test cases
- **Test_Case_Assignments.md** - Team assignments

---

## TODAY/TOMORROW ACTION PLAN

### **Priority 1: Complete Chapter 5 (7 points)**
1. [ ] Open Deliverable 2 Design Document architecture sections
2. [ ] Copy relevant content to Final Document Chapter 5
3. [ ] Make corrections and updates
4. [ ] Write introduction (5.0)
5. [ ] Complete all 5 sections (5.1-5.5)
6. [ ] Review for format compliance

### **Priority 2: Complete Chapter 6 (9 points)**
1. [ ] Coordinate with Alfonso for class diagrams (6.4)
2. [ ] Open Deliverable 2 Design Document UML diagrams
3. [ ] Copy relevant sequence diagrams to Final Document Chapter 6
4. [ ] Write introduction (6.0)
5. [ ] Complete all 4 sections (6.1-6.4)
6. [ ] Review for format compliance

### **Priority 3: Review & Finalize**
1. [ ] Review team members' test cases
2. [ ] Ensure format consistency
3. [ ] Final document review
4. [ ] Prepare for submission

---

## PROGRESS SUMMARY

| Task | Status | Points | Priority |
|------|--------|--------|----------|
| Test Cases (UC-005, UC-001) | Complete | - | Done |
| Chapter 5: Software Architecture | Pending | 7 | High |
| Chapter 6: Detailed Design | Pending | 9 | High |
| Team Coordination | Complete | - | Done |
| Final Review | Pending | - | Medium |

**Total Points for Your Chapters:** 16 points 
**Completed:** 0/16 (0%) 
**Remaining:** 16/16 (100%)

---

## QUICK START GUIDE FOR CHAPTERS 5 & 6

### **Step 1: Open Reference Documents**
```
1. Navigate to: C:\Users\alewi\MenuMap\Deliverable2_Design\
2. Open Architecture folder for Chapter 5
3. Open UML_Diagrams folder for Chapter 6
```

### **Step 2: Open Final Document**
```
1. Open the Final Document Word file (CEN4010 Final Document)
2. Navigate to Chapter 5
3. Start with Section 5.0 Introduction
```

### **Step 3: Copy & Adapt Content**
```
1. Copy relevant sections from Deliverable 2
2. Make corrections and updates
3. Ensure present tense (not future tense)
4. Follow format requirements strictly
```

### **Step 4: Add Diagrams**
```
1. Insert PNG diagrams from Deliverable2_Design/UML_Diagrams/Diagrams_Only/
2. Reference diagrams in text
3. Ensure diagrams are clear and readable
```

### **Step 5: Review & Format**
```
1. Check line spacing (1.5)
2. Check font sizes (16pt headings, 13pt sections, 11pt text)
3. Check table of contents
4. Review for consistency
```

---

## IMPORTANT REMINDERS

1. **Chapters 5 & 6 are your primary responsibility** - 16 points total
2. **Content should be similar to Design Document** but with corrections
3. **Coordinate with Alfonso** for class diagrams in Chapter 6.4
4. **Follow format requirements** strictly (you'll lose points if not followed)
5. **Use present tense** (not future tense) - system is implemented
6. **Reference other chapters and appendices** where appropriate
7. **Include diagrams** where specified (PNG files from Deliverable 2)

---

## NOTES

- **Word Documents:** I cannot read .docx files directly. If you need me to review the CEN4010-Final.docx or CEN4010-GradeSheet_Deliver-3.docx files, please copy and paste the text content.

- **Format Requirements:** Based on the images you shared:
 - 1.5 line spacing
 - Chapter headings: 16 pt
 - Section headings: 13 pt
 - Text: 11pt Arial or 12pt Times
 - Table of Contents must be accurate

- **Content Requirements:**
 - Similar to Design Document (with corrections)
 - Include diagrams where specified
 - Reference other chapters and appendices
 - Use present tense (not future tense)

---

## COMPLETION CHECKLIST

### **Before Submission:**
- [ ] Chapter 5: Software Architecture complete (all 6 sections)
- [ ] Chapter 6: Detailed Design complete (all 5 sections)
- [ ] Format requirements met (spacing, fonts, headings)
- [ ] Diagrams included and referenced
- [ ] Table of contents updated
- [ ] Content reviewed for consistency
- [ ] Team members' work reviewed
- [ ] Final document review completed

---

**Focus:** Complete Chapters 5 & 6 today/tomorrow - these are your main deliverables as Group Lead!

**Total Points at Stake:** 16 points (7 + 9)

**Estimated Time:** 4-6 hours for both chapters

---

*This checklist will help you complete everything needed as Group Lead for Deliverable 3.*

