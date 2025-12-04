# Chapter 7.1.3: Test Cases - Structure & Organization
## MenuMap Deliverable 3 - Final Systems Document

**Chapter:** 7 - Testing Process  
**Section:** 7.1.3 - Test Cases  
**Primary Owner:** Alexandra Cozar  
**Group Lead:** Andre Lewis  
**Points:** 10 points

---

## 📋 Section Structure

### **7.1.3. Test Cases** (10 points)

This section contains all test cases written by team members. Each test case follows the format described in class and includes:
- Unique identifier
- Purpose
- Environment setup (preconditions)
- Input
- Expected output

---

## 📚 Test Case Organization by Use Case

### **7.1.3.1. UC-001: Browse Restaurant Menus** 
**Written by:** Andre Lewis (Group Lead)  
**Test Cases:** 8 total (2 sunny day, 6 rainy day)

**Test Case IDs:**
- SystemTest-011-UC001 (sunny day scenario)
- SystemTest-012-UC001 (sunny day scenario)
- SystemTest-013-UC001 (rainy day scenario)
- SystemTest-014-UC001 (rainy day scenario)
- SystemTest-015-UC001 (rainy day scenario)
- SystemTest-016-UC001 (rainy day scenario)
- SystemTest-017-UC001 (rainy day scenario)
- SystemTest-018-UC001 (rainy day scenario)

**Source File:** `MenuMap_Test_Cases_Login_UC001.md` (Section: UC-001)

---

### **7.1.3.2. UC-002: Manage Favorites**
**Written by:** Alexandra Cozar (Team Leader)  
**Test Cases:** 3 minimum required (2 sunny day, 1 rainy day)

**Test Case IDs:**
- SystemTest-019-UC002 (sunny day scenario)
- SystemTest-020-UC002 (sunny day scenario)
- SystemTest-021-UC002 (rainy day scenario)

**Source File:** `MenuMap_Test_Cases_Favorites_Logout.md` (to be created)

**Status:** ⏳ Pending

---

### **7.1.3.3. UC-003: Secure Password Reset**
**Written by:** Kamal Ayoub  
**Test Cases:** 3 minimum required (2 sunny day, 1 rainy day)

**Test Case IDs:**
- SystemTest-025-UC003 (sunny day scenario)
- SystemTest-026-UC003 (sunny day scenario)
- SystemTest-027-UC003 (rainy day scenario)

**Source File:** `MenuMap_Test_Cases_PasswordReset_Registration.md` (to be created)

**Status:** ⏳ Pending

---

### **7.1.3.4. UC-005: User Login**
**Written by:** Andre Lewis (Group Lead)  
**Test Cases:** 10 total (2 sunny day, 8 rainy day)

**Test Case IDs:**
- SystemTest-001-UC005 (sunny day scenario)
- SystemTest-002-UC005 (sunny day scenario)
- SystemTest-003-UC005 (rainy day scenario)
- SystemTest-004-UC005 (rainy day scenario)
- SystemTest-005-UC005 (rainy day scenario)
- SystemTest-006-UC005 (rainy day scenario)
- SystemTest-007-UC005 (rainy day scenario)
- SystemTest-008-UC005 (rainy day scenario)
- SystemTest-009-UC005 (rainy day scenario)
- SystemTest-010-UC005 (rainy day scenario)

**Source File:** `MenuMap_Test_Cases_Login_UC001.md` (Section: UC-005)

**Status:** ✅ Complete

---

### **7.1.3.5. UC-005: User Registration**
**Written by:** Kamal Ayoub  
**Test Cases:** 3 minimum required (2 sunny day, 1 rainy day)

**Test Case IDs:**
- SystemTest-028-UC005 (sunny day scenario)
- SystemTest-029-UC005 (sunny day scenario)
- SystemTest-030-UC005 (rainy day scenario)

**Source File:** `MenuMap_Test_Cases_PasswordReset_Registration.md` (to be created)

**Status:** ⏳ Pending

**Note:** UC-005 has two different use cases (Login and Registration). Test cases are separated by functionality.

---

### **7.1.3.6. UC-006: User Logout**
**Written by:** Alexandra Cozar (Team Leader)  
**Test Cases:** 3 minimum required (2 sunny day, 1 rainy day)

**Test Case IDs:**
- SystemTest-022-UC006 (sunny day scenario)
- SystemTest-023-UC006 (sunny day scenario)
- SystemTest-024-UC006 (rainy day scenario)

**Source File:** `MenuMap_Test_Cases_Favorites_Logout.md` (to be created)

**Status:** ⏳ Pending

---

### **7.1.3.7. UC-007: Restaurant Owner Menu Management**
**Written by:** Alfonso Oramas  
**Test Cases:** 3 minimum required (2 sunny day, 1 rainy day)

**Test Case IDs:**
- SystemTest-031-UC007 (sunny day scenario)
- SystemTest-032-UC007 (sunny day scenario)
- SystemTest-033-UC007 (rainy day scenario)

**Source File:** `MenuMap_Test_Cases_MenuManagement.md` (to be created)

**Status:** ⏳ Pending

---

## 📊 Test Case Summary Table

| Use Case | Test Case ID Range | Writer | Sunny Day | Rainy Day | Total | Status |
|----------|-------------------|--------|-----------|-----------|-------|--------|
| UC-001 | SystemTest-011 to 018 | Andre Lewis | 2 | 6 | 8 | ✅ Complete |
| UC-002 | SystemTest-019 to 021 | Alexandra Cozar | 2 | 1 | 3 | ⏳ Pending |
| UC-003 | SystemTest-025 to 027 | Kamal Ayoub | 2 | 1 | 3 | ⏳ Pending |
| UC-005 (Login) | SystemTest-001 to 010 | Andre Lewis | 2 | 8 | 10 | ✅ Complete |
| UC-005 (Registration) | SystemTest-028 to 030 | Kamal Ayoub | 2 | 1 | 3 | ⏳ Pending |
| UC-006 | SystemTest-022 to 024 | Alexandra Cozar | 2 | 1 | 3 | ⏳ Pending |
| UC-007 | SystemTest-031 to 033 | Alfonso Oramas | 2 | 1 | 3 | ⏳ Pending |
| **TOTAL** | **SystemTest-001 to 033** | **All Team** | **14** | **19** | **33** | **55% Complete** |

---

## 📝 Format Requirements for Each Test Case

Each test case in Section 7.1.3 must include:

### **1. Test Case ID**
Format: `SystemTest-XXX-UCXXX (sunny day scenario)` or `(rainy day scenario)`

### **2. Purpose**
One sentence describing what the test case validates.

### **3. Test Setup (Preconditions)**
- Environment setup
- Database state (reference tables from Section 7.1.2)
- System state before test execution

### **4. Test Input**
Numbered list of step-by-step actions:
1. User action
2. System response
3. etc.

### **5. Expected Output**
- What should happen
- Expected system behavior
- Expected user feedback
- System state after test execution

---

## 🔗 References to Other Sections

### **Section 7.1.1: Test Identification and Objective (Summary)**
- Lists all test case IDs and their purposes
- Quick reference table

### **Section 7.1.2: Test Criteria and Procedures**
- Each test case includes its own database state table(s)
- Test cases reference their specific tables (e.g., "see Table TC-005-01")

---

## ✅ Compilation Checklist for Alexandra Cozar

Before finalizing Chapter 7.1.3:

- [ ] All team members have submitted their test cases
- [ ] All test cases follow `SystemTest-XXX-UCXXX` format
- [ ] All test cases include required sections (ID, Purpose, Setup, Input, Expected Output)
- [ ] Database state tables are referenced correctly
- [ ] Test cases are organized by use case
- [ ] Test Case IDs are sequential and unique
- [ ] Sunny day and rainy day scenarios are clearly marked
- [ ] Format is consistent across all test cases
- [ ] All test cases are included in Section 7.1.1 summary

---

## 📁 File Organization for Compilation

When compiling into Final Document:

1. **Section 7.1.3.1:** Copy from `MenuMap_Test_Cases_Login_UC001.md` (UC-001 section)
2. **Section 7.1.3.2:** Copy from `MenuMap_Test_Cases_Favorites_Logout.md` (UC-002 section)
3. **Section 7.1.3.3:** Copy from `MenuMap_Test_Cases_PasswordReset_Registration.md` (UC-003 section)
4. **Section 7.1.3.4:** Copy from `MenuMap_Test_Cases_Login_UC001.md` (UC-005 Login section)
5. **Section 7.1.3.5:** Copy from `MenuMap_Test_Cases_PasswordReset_Registration.md` (UC-005 Registration section)
6. **Section 7.1.3.6:** Copy from `MenuMap_Test_Cases_Favorites_Logout.md` (UC-006 section)
7. **Section 7.1.3.7:** Copy from `MenuMap_Test_Cases_MenuManagement.md` (UC-007 section)

---

## 🎯 Next Steps

1. ✅ **Andre Lewis:** Test cases complete - ready for inclusion
2. ⏳ **Alexandra Cozar:** Write UC-002 and UC-006 test cases
3. ⏳ **Kamal Ayoub:** Write UC-003 and UC-005 (Registration) test cases
4. ⏳ **Alfonso Oramas:** Write UC-007 test cases
5. ⏳ **Alexandra Cozar:** Compile all into Chapter 7.1.3
6. ⏳ **Andre Lewis:** Review compiled Chapter 7

---

**This structure ensures all test cases are properly organized and ready for inclusion in the Final Systems Document Chapter 7.1.3.**






