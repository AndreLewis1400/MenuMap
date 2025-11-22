# Deliverable 2 Requirements Checklist
## Based on Design Document Outline and Grading Rubric

### ✅ **Pre-Chapter 1 Sections (6 points)**
- [ ] **Cover Page** (1 pt) - Course, section, system name, team #, members, date, professor
- [ ] **Abstract** (3 pts) - Brief overview (1-2 paragraphs)
- [ ] **Table of Contents** (2 pts)

### ✅ **Chapter 1: Introduction (14 points)**
- [ ] **1. Introduction** - Introductory section (1-2 paragraphs)
- [ ] **1.1 Purpose of System** (2 pts) - Similar to SRD
- [ ] **1.2 Requirements** (4 pts)
  - [ ] **1.2.1 Functional Requirements** - High-level for ALL use cases, refer to first 7 use cases in Appendix B
  - [ ] **1.2.2 Nonfunctional Requirements** - Summary for ALL use cases (max 2 pages)
- [ ] **1.3 Design Methodology** (4 pts) - Software process model, ease of design from SRD, UML models used
- [ ] **1.4 Definitions, Acronyms, Abbreviations** (2 pts)
- [ ] **1.5 Overview of Document** (2 pts)

### ✅ **Chapter 2: Proposed Software Architecture (20 points)**
- [ ] **Introduction** - One or two paragraphs, focus on 7 use cases (3 security use cases)
- [ ] **2.1 Overview** (4 pts)
  - [ ] Package diagram showing major subsystems
  - [ ] Overview of each subsystem
  - [ ] **At least 2 architectural patterns** (primary + secondary)
  - [ ] **At least 2 reasons for selecting each pattern**
  - [ ] How architecture supports nonfunctional requirements
  - [ ] Reference to use case diagram in Appendix A
- [ ] **2.2 Subsystem Decomposition** (4 pts)
  - [ ] Describe each major subsystem in detail
  - [ ] Identify use cases associated with each subsystem
  - [ ] Reference to use case diagram in Appendix A
- [ ] **2.3 Hardware and Software Mapping** (4 pts)
  - [ ] Map subsystems to hardware and software
  - [ ] **UML Deployment Diagram required**
- [ ] **2.4 Persistent Data Management** (4 pts)
  - [ ] Identify data to be stored
  - [ ] Similar to data dictionary
  - [ ] Structure of data used in entity objects
  - [ ] Database model encouraged
- [ ] **2.5 Security Management** (4 pts)
  - [ ] Security protocols
  - [ ] User authentication
  - [ ] Encryption
  - [ ] Firewalls
  - [ ] Global access table

### ✅ **Chapter 3: Detailed Design (16 points)**
- [ ] **Introduction** - Brief introduction (1-2 paragraphs)
- [ ] **3.1 Overview** (4 pts)
  - [ ] **Minimal class diagram** for implemented subsystem(s)
  - [ ] All classes but no attributes or methods
  - [ ] Each class purpose described in one sentence
  - [ ] **At least 3 design patterns** identified in minimal class diagram
- [ ] **3.2 State Machine** (4 pts)
  - [ ] **One state machine** for overall system
  - [ ] Based on application's menu system
- [ ] **3.3 Object Interaction** (4 pts)
  - [ ] Refinement of sequence diagrams from SRD
  - [ ] Redo sequence diagrams from analysis model
  - [ ] Add additional "solution objects"
  - [ ] **7 Sequence Diagrams required**
- [ ] **3.4 Detailed Class Design** (4 pts)
  - [ ] **3.4.1** - Purpose of each class, refer to class diagram in Appendix C
  - [ ] **3.4.1** - Explain why each of 3 design patterns was used
  - [ ] **3.4.2** - **OCL statements** for main control object:
    - [ ] Class invariants
    - [ ] Pre-conditions
    - [ ] Post-conditions for methods
    - [ ] Class containing OCL statements must be identified

### ✅ **Chapter 4: Glossary (2 points)**
- [ ] Define terms, especially domain-specific ones

### ✅ **Chapter 5: Approval Page (2 points)**
- [ ] Signatures and date

### ✅ **Chapter 6: References (2 points)**
- [ ] Standard citations section

### ✅ **Chapter 7: Appendices (20 points)**
- [ ] **7.1 Appendix A** (3 pts) - Use case diagram (for use cases to be implemented only)
- [ ] **7.2 Appendix B** (3 pts) - Use cases with nonfunctional requirements (from SRD), only use cases being implemented
- [ ] **7.3 Appendix C** (5 pts) - Detail class diagrams showing attributes and methods for each class
  - [ ] **One class diagram per main subsystem package**
  - [ ] Annotate diagram to illustrate design patterns used
- [ ] **7.4 Appendix D** (4 pts) - Diary of meetings and tasks

### ✅ **UML Diagrams in Papyrus (18 points)**
- [ ] **1. Use Case Diagram** (2 pts)
- [ ] **2. Architecture (Package Diagram)** (3 pts)
- [ ] **3. Minimal Class Diagram** (3 pts)
- [ ] **4. Detailed Class Diagram** (4 pts)
- [ ] **5. State Machine** (3 pts)
- [ ] **6. Sequence Diagrams** (3 pts) - 7 sequence diagrams

---

## Current Status Assessment

### ✅ **What You Have:**

**UML Diagrams (13 PNG files):**
- ✅ Use Case Diagram
- ✅ 3-Tier Architecture Diagram (Package Diagram equivalent)
- ✅ 3 Detailed Class Diagrams (Client, Logic, DataStore)
- ✅ State Machine Diagram
- ✅ 7 Sequence Diagrams (UC-001 through UC-007)

**Documentation Files:**
- ✅ Design_Document.md (comprehensive)
- ✅ Architecture documents (Package, Subsystem, Hardware/Software, Security)
- ✅ Design Patterns Overview (3 patterns: Observer, Factory, Strategy)
- ✅ OCL Statements (comprehensive)
- ✅ Use Case documentation (all 7 use cases)
- ✅ Meeting Diary
- ✅ Primary/Secondary Components

**Required Documents:**
- ✅ 2.CEN4010-DD (1).docx (Design Document)
- ✅ GradeSheet_Deliver2 (1).docx (Grade Sheet)

### ⚠️ **Potential Gaps:**

1. **Design Document Structure** - The markdown Design_Document.md may not match the exact chapter structure required (Chapters 1-7)
2. **Cover Page** - Need to verify if the .docx has proper cover page
3. **Abstract** - Need to verify if present in .docx
4. **Table of Contents** - Need to verify if present in .docx
5. **Glossary** - May need to be added
6. **Approval Page** - May need to be added
7. **References** - May need to be added
8. **Minimal Class Diagram** - Need to verify if separate from detailed diagrams
9. **Deployment Diagram** - May be missing (required in 2.3)

### 📋 **Recommendations:**

1. **Verify .docx Content** - Check if the Word document has all required sections in proper format
2. **Add Missing Sections** - Glossary, Approval Page, References if not present
3. **Verify Chapter Structure** - Ensure Design Document follows exact chapter numbering (1-7)
4. **Check Appendices** - Ensure all 4 appendices are properly formatted
5. **Verify Minimal Class Diagram** - Ensure you have a separate minimal diagram (no attributes/methods)

