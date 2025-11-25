# Test Case Assignments - Chapter 7.1.3
## MenuMap Deliverable 3 - Team 9

**Group Lead:** Andre Lewis  
**Team Leader (Chapter 7 Primary):** Alexandra Cozar  
**Date:** [Current Date]  
**Status:** ✅ Assignments Complete

---

## 📋 Assignment Overview

According to Deliverable 3 requirements:
- **Each team member** must write **at least 3 test cases** per assigned use case
- **2 sunny day** test cases (happy path)
- **1 rainy day** test case (error/edge case)
- Test cases should follow format: `SystemTest-XXX-UCXXX` (matching lecture example)

---

## 👥 Team Member Assignments

### **Andre Lewis (Group Lead)**
**Assigned Use Cases:**
- ✅ **UC-005: User Login** - **COMPLETED**
  - 10 test cases total (2 sunny day, 8 rainy day)
  - File: `MenuMap_Test_Cases_Login_UC001.md`
  - Test Case IDs: SystemTest-001-UC005 through SystemTest-010-UC005

- ✅ **UC-001: Browse Restaurant Menus** - **COMPLETED**
  - 8 test cases total (2 sunny day, 6 rainy day)
  - File: `MenuMap_Test_Cases_Login_UC001.md`
  - Test Case IDs: SystemTest-011-UC001 through SystemTest-018-UC001

**Status:** ✅ Complete (18 test cases total - exceeds minimum requirement)

---

### **Alexandra Cozar (Team Leader - Chapter 7 Primary)**
**Assigned Use Cases:**
- **UC-002: Manage Favorites**
  - Required: 3 test cases minimum (2 sunny day, 1 rainy day)
  - Test Case IDs: SystemTest-019-UC002, SystemTest-020-UC002, SystemTest-021-UC002

- **UC-006: User Logout**
  - Required: 3 test cases minimum (2 sunny day, 1 rainy day)
  - Test Case IDs: SystemTest-022-UC006, SystemTest-023-UC006, SystemTest-024-UC006

**Total Required:** 6 test cases minimum  
**Status:** ⏳ Pending

**Responsibilities:**
- Primary owner of Chapter 7: Testing Process
- Coordinate test case collection from all team members
- Compile all test cases into Chapter 7.1.3
- Ensure format consistency across all test cases

---

### **Kamal Ayoub**
**Assigned Use Cases:**
- **UC-003: Secure Password Reset**
  - Required: 3 test cases minimum (2 sunny day, 1 rainy day)
  - Test Case IDs: SystemTest-025-UC003, SystemTest-026-UC003, SystemTest-027-UC003

- **UC-005: User Registration** (if not already covered)
  - Required: 3 test cases minimum (2 sunny day, 1 rainy day)
  - Test Case IDs: SystemTest-028-UC005, SystemTest-029-UC005, SystemTest-030-UC005

**Total Required:** 6 test cases minimum  
**Status:** ⏳ Pending

---

### **Alfonso Oramas**
**Assigned Use Cases:**
- **UC-007: Restaurant Owner Menu Management**
  - Required: 3 test cases minimum (2 sunny day, 1 rainy day)
  - Test Case IDs: SystemTest-031-UC007, SystemTest-032-UC007, SystemTest-033-UC007

**Total Required:** 3 test cases minimum  
**Status:** ⏳ Pending

---

## 📊 Test Case Summary

| Team Member | Use Cases Assigned | Test Cases Required | Test Cases Completed | Status |
|-------------|-------------------|---------------------|---------------------|--------|
| **Andre Lewis** | UC-005, UC-001 | 6 minimum | 18 | ✅ Complete |
| **Alexandra Cozar** | UC-002, UC-006 | 6 minimum | 0 | ⏳ Pending |
| **Kamal Ayoub** | UC-003, UC-005 | 6 minimum | 0 | ⏳ Pending |
| **Alfonso Oramas** | UC-007 | 3 minimum | 0 | ⏳ Pending |
| **TOTAL** | 7 use cases | 21 minimum | 18 | 86% Complete |

---

## 📝 Test Case Format Requirements

Each test case must include:

1. **Test Case ID:** `SystemTest-XXX-UCXXX (sunny day scenario)` or `(rainy day scenario)`
2. **Purpose:** What the test case validates
3. **Test Setup:** Preconditions including database state (reference tables)
4. **Test Input:** Step-by-step actions (numbered)
5. **Expected Output:** Expected results
6. **Postconditions:** System state after test

### **Database State Tables Required:**
- All test cases must reference database state tables in Section 7.1.2
- Tables should show data before test execution
- Format: Table 1, Table 2, etc.

---

## 📁 File Organization

### **Individual Test Case Files:**
- `MenuMap_Test_Cases_Login_UC001.md` - Andre Lewis (UC-005, UC-001) ✅
- `MenuMap_Test_Cases_Favorites_Logout.md` - Alexandra Cozar (UC-002, UC-006) ⏳
- `MenuMap_Test_Cases_PasswordReset_Registration.md` - Kamal Ayoub (UC-003, UC-005) ⏳
- `MenuMap_Test_Cases_MenuManagement.md` - Alfonso Oramas (UC-007) ⏳

### **Compiled in Chapter 7.1.3:**
All test cases will be compiled into the Final Document Chapter 7.1.3:
- Section 7.1.3.1: UC-001 Test Cases (Andre)
- Section 7.1.3.2: UC-002 Test Cases (Alexandra)
- Section 7.1.3.3: UC-003 Test Cases (Kamal)
- Section 7.1.3.4: UC-005 Test Cases (Andre - Login)
- Section 7.1.3.5: UC-005 Test Cases (Kamal - Registration)
- Section 7.1.3.6: UC-006 Test Cases (Alexandra)
- Section 7.1.3.7: UC-007 Test Cases (Alfonso)

---

## ✅ Checklist for Each Team Member

### **Before Writing Test Cases:**
- [ ] Review assigned use case documentation
- [ ] Understand use case flow (main and alternative flows)
- [ ] Review database schema for test data
- [ ] Review existing test case format (see `MenuMap_Test_Cases_Login_UC001.md`)

### **While Writing Test Cases:**
- [ ] Follow `SystemTest-XXX-UCXXX` format
- [ ] Include database state tables
- [ ] Write 2 sunny day scenarios (successful paths)
- [ ] Write 1 rainy day scenario (error/edge case)
- [ ] Include all required sections (ID, Purpose, Setup, Input, Output, Postconditions)

### **Before Submission:**
- [ ] Review test cases for completeness
- [ ] Verify format matches requirements
- [ ] Check database table references
- [ ] Submit to Alexandra Cozar for Chapter 7 compilation

---

## 📅 Timeline

- **Week 3:** All team members write their assigned test cases
- **Deadline:** [Set by Alexandra Cozar]
- **Compilation:** Alexandra compiles all test cases into Chapter 7.1.3
- **Review:** Group Lead reviews compiled Chapter 7

---

## 📞 Contact & Coordination

- **Chapter 7 Primary Owner:** Alexandra Cozar
- **Group Lead:** Andre Lewis
- **Questions about test case format:** See `MenuMap_Test_Cases_Login_UC001.md` for reference
- **Questions about use cases:** Review use case documentation in `Deliverable1_Requirements/Use_Cases/`

---

## 🎯 Next Steps

1. ✅ **Andre Lewis:** Test cases complete - ready for Chapter 7 inclusion
2. ⏳ **Alexandra Cozar:** Write test cases for UC-002 and UC-006
3. ⏳ **Kamal Ayoub:** Write test cases for UC-003 and UC-005 (Registration)
4. ⏳ **Alfonso Oramas:** Write test cases for UC-007
5. ⏳ **Alexandra Cozar:** Compile all test cases into Chapter 7.1.3

---

**Last Updated:** [Current Date]  
**Updated By:** Andre Lewis (Group Lead)

