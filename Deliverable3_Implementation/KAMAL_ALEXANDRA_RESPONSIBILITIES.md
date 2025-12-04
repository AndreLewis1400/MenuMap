# Kamal and Alexandra - Deliverable 3 Responsibilities
## Team 9 - MenuMap Project
## CEN 4010 - Software Engineering
## Fall 2024

---

## 📋 Overview

This document outlines the specific responsibilities for **Kamal** and **Alexandra** for Deliverable 3: Implementation and Testing. All responsibilities are organized by **Final Document sections** and **Presentation slides**.

---

# 📄 ALEXANDRA'S RESPONSIBILITIES

## 🎯 Final Document Responsibilities

### **Chapter 3: Project Plan** (4 points)
**Status:** ✅ Completed  
**Location:** `Deliverable3_Final_Document_Team9.md` - Chapter 3

#### **Section 3.1: Project Scope**
- Define project scope
- Describe system boundaries
- Identify included/excluded features

#### **Section 3.2: Project Objectives**
- List project objectives (5 objectives)
- Define success criteria
- Align with requirements

#### **Section 3.3: Project Timeline**
- **Phase 1: Requirements and Design (Weeks 1-5)**
  - Deliverable 1 completion
  - SRD completion
  - Use case documentation
- **Phase 2: Detailed Design (Weeks 6-10)**
  - Deliverable 2 completion
  - Architecture design
  - UML diagrams
- **Phase 3: Implementation and Testing (Weeks 11-15)**
  - Deliverable 3 completion
  - System implementation
  - Testing

#### **Section 3.4: Resource Allocation**
- Team member assignments
- Responsibility breakdown
- Task distribution

#### **Section 3.5: Risk Management**
- Risk identification
- Mitigation strategies
- Contingency plans

---

### **Chapter 7: Testing Process** (18 points)
**Status:** ⏳ Structure Complete - Test Cases Pending  
**Location:** `Deliverable3_Final_Document_Team9.md` - Chapter 7

#### **Section 7.1: Testing Overview**
- Testing strategy
- Test coverage
- Testing approach

#### **Section 7.1.1: Test Cases Overview**
- List all use cases tested
- Test case count per use case
- **Note:** Alexandra compiles ALL team test cases

#### **Section 7.1.2: Test Criteria and Procedures**
- Test criteria definition
- Test procedures
- Test environment setup

#### **Section 7.1.3: Detailed Test Cases**
**Alexandra's Test Cases to Complete:**

##### **UC-002: Restaurant Owner Menu Management** (3 test cases)
**Location:** Section 7.1.3 - UC-002

**Required Test Cases:**
- **TC-002-01: Create Menu Item (Sunny Day)**
  - Test Case ID: SystemTest-019-UC002
  - Purpose: Verify restaurant owner can create menu items
  - **Must Include:**
    - Database state table (before test)
    - Test setup with preconditions
    - Test input (step-by-step actions)
    - Expected output
    - Database state table (after test, if applicable)
    - Result: PASS/FAIL

- **TC-002-02: Update Menu Item (Sunny Day)**
  - Test Case ID: SystemTest-020-UC002
  - Purpose: Verify restaurant owner can update menu items
  - **Must Include:**
    - Database state table (before test)
    - Test setup
    - Test input
    - Expected output
    - Result: PASS/FAIL

- **TC-002-03: Unauthorized Access (Rainy Day)**
  - Test Case ID: SystemTest-021-UC002
  - Purpose: Verify non-owners cannot modify menus
  - **Must Include:**
    - Database state table (before test)
    - Test setup
    - Test input
    - Expected output
    - Result: PASS/FAIL

**Format Reference:** See `MenuMap_Test_Cases_Login_UC001.md` for format example

---

##### **UC-006: Menu Verification** (3 test cases)
**Location:** Section 7.1.3 - UC-006

**Required Test Cases:**
- **TC-006-01: Verify Menu (Sunny Day)**
  - Test Case ID: SystemTest-035-UC006
  - Purpose: Verify menu verification process
  - **Must Include:**
    - Database state table (before test)
    - Test setup
    - Test input
    - Expected output
    - Result: PASS/FAIL

- **TC-006-02: Verification Failure (Rainy Day)**
  - Test Case ID: SystemTest-036-UC006
  - Purpose: Verify system handles verification failures
  - **Must Include:**
    - Database state table (before test)
    - Test setup
    - Test input
    - Expected output
    - Result: PASS/FAIL

- **TC-006-03: Unauthorized Verification (Rainy Day)**
  - Test Case ID: SystemTest-037-UC006
  - Purpose: Verify only authorized users can verify menus
  - **Must Include:**
    - Database state table (before test)
    - Test setup
    - Test input
    - Expected output
    - Result: PASS/FAIL

---

#### **Section 7.2: Test Results Summary**
- **Alexandra's Contribution:**
  - Update test results for UC-002 (3 test cases)
  - Update test results for UC-006 (3 test cases)
  - Update overall test summary
  - Include pass/fail rates

#### **Section 7.3: Test Execution Environment**
- Test environment description
- Database setup
- Test data preparation

**Note:** Alexandra is responsible for **compiling ALL team test cases** into Chapter 7.1.3, including:
- Andre's test cases (UC-001, UC-005)
- Kamal's test cases (UC-003, UC-004)
- Alfonso's test cases (UC-007)
- Her own test cases (UC-002, UC-006)

---

### **Appendix A: Project Schedule** (1 point)
**Status:** ✅ Completed  
**Location:** `Deliverable3_Final_Document_Team9.md` - Appendix A

#### **Required Sections:**
- **Project Timeline Table**
  - Week-by-week breakdown
  - Phase identification
  - Milestone tracking

- **Detailed Week-by-Week Schedule**
  - Weeks 1-3: Requirements Phase
  - Weeks 4-10: Design Phase
  - Weeks 11-15: Implementation Phase

- **Milestones**
  - Milestone 1: Deliverable 1 (Week 3)
  - Milestone 2: Deliverable 2 (Week 10)
  - Milestone 3: Deliverable 3 (Week 15)

- **Team Member Contributions Timeline**
  - Individual contributions by phase
  - Task completion tracking

---

## 🎤 Presentation Responsibilities

### **Slides 7-8: Functional Requirements - UC-003 (Security Use Case)**
**Time Allocation:** ~2-3 minutes  
**Status:** ✅ Content Ready

#### **Slide 7: Functional Requirements - Use Case 2 (UC-003) - Security Use Case**

**Alexandra Presents:**
- **UC-003: Secure Password Reset** description
- **Main Flow** (9 steps):
  1. User requests password reset
  2. System validates user email
  3. System generates secure reset token
  4. System sends reset link to user email
  5. User clicks reset link
  6. System validates token
  7. User enters new password
  8. System validates and updates password
  9. System invalidates reset token

- **Functional Requirements:**
  - FR-012: System allows users to request password reset
  - FR-013: System validates user email before sending reset link
  - FR-014: System generates secure, time-limited reset tokens
  - FR-015: System validates reset tokens before allowing password change

- **Non-Functional Requirements:**
  - NFR-003: User passwords shall be hashed and stored securely
  - NFR-004: System shall prevent SQL injection attacks
  - NFR-005: System shall validate and sanitize all user inputs
  - NFR-010: Reset tokens shall expire after 24 hours

**Key Point:** Emphasize this is the **SECURITY USE CASE** (not login/logout)

---

#### **Slide 8: Functional Requirements - Use Case 2 (UC-003) - Continued**

**Alexandra Presents:**
- **Alternative Flows:**
  - Invalid email: System displays generic message (security)
  - Token expired: System prompts user to request new reset
  - Invalid token: System denies password reset
  - Weak password: System enforces password complexity requirements

- **Preconditions:**
  - User has registered account
  - User has access to registered email

- **Postconditions:**
  - Password is updated (if successful)
  - Reset token is invalidated
  - User can log in with new password

- **Security Features:**
  - Secure token generation (cryptographically random)
  - Time-limited tokens (24-hour expiration)
  - Token single-use only
  - Password complexity enforcement
  - Email verification required

**Presentation Tips:**
- Focus on security aspects
- Explain why UC-003 is the security use case
- Be clear and concise (2-3 minutes total)

---

## 📊 Alexandra's Summary

### **Final Document:**
- ✅ Chapter 3: Project Plan (4 points) - **COMPLETE**
- ⏳ Chapter 7: Testing Process (18 points) - **NEEDS TEST CASES**
  - UC-002: 3 test cases - **TO BE COMPLETED**
  - UC-006: 3 test cases - **TO BE COMPLETED**
  - Compile all team test cases - **TO BE COMPLETED**
- ✅ Appendix A: Project Schedule (1 point) - **COMPLETE**

### **Presentation:**
- ✅ Slides 7-8: UC-003 Functional Requirements - **READY**

### **Total Points:**
- **23 points** (4 + 18 + 1)
- **6 test cases** to complete (UC-002: 3, UC-006: 3)

---

# 📄 KAMAL'S RESPONSIBILITIES

## 🎯 Final Document Responsibilities

### **Chapter 7: Testing Process - Test Cases Only**
**Status:** ⏳ Test Cases Pending  
**Location:** `Deliverable3_Final_Document_Team9.md` - Section 7.1.3

#### **UC-003: Secure Password Reset** (3 test cases)
**Location:** Section 7.1.3 - UC-003

**Required Test Cases:**
- **TC-003-01: Successful Password Reset (Sunny Day)**
  - Test Case ID: SystemTest-041-UC003
  - Purpose: Verify user can successfully reset password through secure process
  - **Must Include:**
    - Database state table (before test) - Users table with email, password hash, email verified
    - Test setup with preconditions
    - Test input (step-by-step actions):
      1. User navigates to password reset page
      2. User enters email
      3. System validates email and generates reset token
      4. System sends reset link to email
      5. User clicks reset link
      6. System validates token
      7. User enters new password
      8. System validates and updates password
    - Expected output:
      - Reset link sent successfully
      - Token validated correctly
      - Password updated securely
      - User can log in with new password
    - Database state table (after test) - Updated password hash, token invalidated
    - Result: PASS/FAIL

- **TC-003-02: Expired Token (Rainy Day)**
  - Test Case ID: SystemTest-042-UC003
  - Purpose: Verify system handles expired reset token correctly
  - **Must Include:**
    - Database state table (before test) - User with expired token (older than 24 hours)
    - Test setup
    - Test input:
      1. User navigates to password reset page
      2. User clicks expired reset link
      3. System checks token expiration
      4. System detects token is expired
    - Expected output:
      - Error message: "Reset link has expired. Please request a new password reset."
      - Option to request new reset link
      - User cannot proceed with expired token
      - Security maintained
    - Database state table (after test) - No password changes, token remains expired
    - Result: PASS/FAIL

- **TC-003-03: Invalid Email (Rainy Day)**
  - Test Case ID: SystemTest-043-UC003
  - Purpose: Verify system prevents password reset with invalid email
  - **Must Include:**
    - Database state table (before test) - Show existing users, non-existent email
    - Test setup
    - Test input:
      1. User navigates to password reset page
      2. User enters non-existent email
      3. System processes reset request
    - Expected output:
      - Generic message displayed: "If an account exists with this email, a reset link will be sent."
      - No information leakage (does not reveal if email exists)
      - Security maintained (prevents email enumeration)
    - Database state table (after test) - No reset tokens generated, no changes
    - Result: PASS/FAIL

**Format Reference:** See `MenuMap_Test_Cases_Login_UC001.md` for format example

---

#### **UC-004: User Registration** (10 test cases)
**Location:** Section 7.1.3 - UC-004

**Required Test Cases:**
- **TC-004-01: Successful Registration (Sunny Day)**
  - Test Case ID: SystemTest-025-UC004
  - Purpose: Verify new user can register successfully
  - **Must Include:**
    - Database state table (before test) - Empty or show existing users
    - Test setup: Email is not registered
    - Test input: User enters valid registration data
    - Expected output: Account created, confirmation email sent
    - Database state table (after test) - New user created
    - Result: PASS/FAIL

- **TC-004-02: Email Already Exists (Rainy Day)**
  - Test Case ID: SystemTest-026-UC004
  - Purpose: Verify system prevents duplicate emails
  - **Must Include:**
    - Database state table (before test) - Email already exists
    - Test setup
    - Test input: User attempts to register with existing email
    - Expected output: Error message displayed
    - Result: PASS/FAIL

- **TC-004-03: Weak Password (Rainy Day)**
  - Test Case ID: SystemTest-027-UC004
  - Purpose: Verify system enforces password requirements
  - **Must Include:**
    - Database state table (before test)
    - Test setup: User is on registration page
    - Test input: User enters weak password
    - Expected output: Password requirements message
    - Result: PASS/FAIL

- **TC-004-04: Password Mismatch (Rainy Day)**
  - Test Case ID: SystemTest-028-UC004
  - Purpose: Verify system validates password confirmation
  - **Must Include:**
    - Database state table (before test)
    - Test setup: User is on registration page
    - Test input: Password and confirmation do not match
    - Expected output: Mismatch error displayed
    - Result: PASS/FAIL

- **TC-004-05: Invalid Email Format (Rainy Day)**
  - Test Case ID: SystemTest-029-UC004
  - Purpose: Verify system validates email format
  - **Must Include:**
    - Database state table (before test)
    - Test setup: User is on registration page
    - Test input: User enters invalid email format
    - Expected output: Email format error
    - Result: PASS/FAIL

- **TC-004-06: Missing Required Fields (Rainy Day)**
  - Test Case ID: SystemTest-030-UC004
  - Purpose: Verify system validates required fields
  - **Must Include:**
    - Database state table (before test)
    - Test setup: User is on registration page
    - Test input: User leaves required fields empty
    - Expected output: Required field errors displayed
    - Result: PASS/FAIL

- **TC-004-07: Database Error During Registration (Rainy Day)**
  - Test Case ID: SystemTest-031-UC004
  - Purpose: Verify system handles database errors
  - **Must Include:**
    - Database state table (before test)
    - Test setup: Database is experiencing issues
    - Test input: User attempts to register
    - Expected output: User-friendly error message
    - Result: PASS/FAIL

- **TC-004-08: Registration Timeout (Rainy Day)**
  - Test Case ID: SystemTest-032-UC004
  - Purpose: Verify system handles timeout scenarios
  - **Must Include:**
    - Database state table (before test)
    - Test setup: Database is slow
    - Test input: User attempts to register
    - Expected output: Timeout message, user can retry
    - Result: PASS/FAIL

- **TC-004-09: SQL Injection in Registration (Rainy Day)**
  - Test Case ID: SystemTest-033-UC004
  - Purpose: Verify system prevents SQL injection
  - **Must Include:**
    - Database state table (before test)
    - Test setup: User is on registration page
    - Test input: User enters SQL injection in fields
    - Expected output: Input sanitized, no SQL executed
    - Result: PASS/FAIL

- **TC-004-10: Registration with All Optional Fields (Sunny Day)**
  - Test Case ID: SystemTest-034-UC004
  - Purpose: Verify system handles optional fields
  - **Must Include:**
    - Database state table (before test)
    - Test setup: User is on registration page
    - Test input: User fills all optional fields
    - Expected output: Registration successful with all data saved
    - Result: PASS/FAIL

**Format Reference:** See `MenuMap_Test_Cases_Login_UC001.md` for format example

---

## 🎤 Presentation Responsibilities

### **Slides 20-21, 23: Test Cases - UC-003**
**Time Allocation:** ~3-4 minutes  
**Status:** ✅ Content Ready

#### **Slide 20: Test Cases - UC-003 Sunny Day**

**Kamal Presents:**
- **Test Case ID:** SystemTest-041-UC003
- **Purpose:** Verify user can successfully reset password through secure process
- **Data Model (Before Test):**
  - Show Users table with user data
  - Email, password hash, email verified status
- **Test Steps:**
  1. User navigates to password reset page
  2. User enters email
  3. System validates email and generates reset token
  4. System sends reset link to email
  5. User clicks reset link
  6. System validates token
  7. User enters new password
  8. System validates and updates password
- **Expected Output:**
  - Reset link sent successfully
  - Token validated correctly
  - Password updated securely
  - User can log in with new password
- **Data Model (After Test):**
  - Show updated password hash
  - Token invalidated (NULL)
- **Result:** ✅ PASS

---

#### **Slide 21: Test Cases - UC-003 Rainy Day**

**Kamal Presents:**
- **Test Case ID:** SystemTest-042-UC003
- **Purpose:** Verify system handles expired reset token correctly
- **Data Model (Before Test):**
  - Show Users table with expired token
  - Token created date vs. current time (expired)
- **Test Steps:**
  1. User navigates to password reset page
  2. User clicks expired reset link
  3. System checks token expiration
  4. System detects token is expired
- **Expected Output:**
  - Error message: "Reset link has expired. Please request a new password reset."
  - Option to request new reset link
  - User cannot proceed with expired token
  - Security maintained
- **Data Model (After Test):**
  - No password changes
  - Token remains expired
- **Result:** ✅ PASS

---

#### **Slide 23: Test Cases - UC-003 Additional Test Case**

**Kamal Presents:**
- **Test Case ID:** SystemTest-043-UC003
- **Purpose:** Verify system prevents password reset with invalid email
- **Data Model (Before Test):**
  - Show existing users in database
  - Non-existent email highlighted
- **Test Steps:**
  1. User navigates to password reset page
  2. User enters non-existent email
  3. System processes reset request
- **Expected Output:**
  - Generic message displayed: "If an account exists with this email, a reset link will be sent."
  - No information leakage (does not reveal if email exists)
  - Security maintained (prevents email enumeration)
- **Data Model (After Test):**
  - No reset tokens generated
  - No changes to database
- **Result:** ✅ PASS

**Presentation Tips:**
- Explain data models clearly
- Point to database tables on slides
- Explain why each test is important
- Be clear about security aspects
- Practice timing (3-4 minutes total)

---

## 📊 Kamal's Summary

### **Final Document:**
- ⏳ Chapter 7.1.3: Test Cases - **NEEDS COMPLETION**
  - UC-003: 3 test cases - **TO BE COMPLETED**
  - UC-004: 10 test cases - **TO BE COMPLETED**

### **Presentation:**
- ✅ Slides 20-21, 23: UC-003 Test Cases - **READY**

### **Total Points:**
- **13 test cases** to complete (UC-003: 3, UC-004: 10)
- **Test cases are part of Chapter 7** (compiled by Alexandra)

---

# 📝 FORMAT REQUIREMENTS

## Test Case Format (CEN4010 Standard)

Each test case **MUST** include:

1. **Test Case ID**: Unique identifier (e.g., SystemTest-041-UC003)
2. **Purpose**: What the test case validates
3. **Database State Table (Before Test)**: 
   - Show relevant database tables
   - Include sample data
   - Format as markdown table
4. **Test Setup**: Preconditions including database state
5. **Test Input**: Step-by-step actions
6. **Expected Output**: Expected results
7. **Database State Table (After Test)**: If applicable
8. **Result**: PASS/FAIL

## Reference File

**Format Example:** `MenuMap_Test_Cases_Login_UC001.md`
- Located in: `Deliverable3_Implementation/MenuMap_Test_Cases_Login_UC001.md`
- Contains UC-001 and UC-005 test cases
- Follow this exact format for all test cases

---

# 📁 FILE LOCATIONS

## Final Document
- **Location:** `Deliverable3_Implementation/Deliverable3_Final_Document_Team9.md`
- **Chapter 3:** Lines ~114-170
- **Chapter 7:** Lines ~380-820
- **Appendix A:** Lines ~950-1040

## Test Case Files
- **Reference Format:** `Deliverable3_Implementation/MenuMap_Test_Cases_Login_UC001.md`
- **Alexandra's Test Cases:** Add to Chapter 7.1.3 (UC-002 and UC-006 sections)
- **Kamal's Test Cases:** Add to Chapter 7.1.3 (UC-003 and UC-004 sections)

## Presentation
- **Location:** `Deliverable3_Implementation/Deliverable3_Presentation_Team9.md`
- **Alexandra's Slides:** Slides 7-8
- **Kamal's Slides:** Slides 20-21, 23

---

# ✅ COMPLETION CHECKLIST

## For Alexandra:

### Final Document:
- [x] Chapter 3: Project Plan - **COMPLETE**
- [x] Appendix A: Project Schedule - **COMPLETE**
- [ ] UC-002 Test Cases (3 test cases) - **TO BE COMPLETED**
- [ ] UC-006 Test Cases (3 test cases) - **TO BE COMPLETED**
- [ ] Compile all team test cases into Chapter 7.1.3 - **TO BE COMPLETED**
- [ ] Update Section 7.2: Test Results Summary - **TO BE COMPLETED**

### Presentation:
- [x] Slides 7-8: UC-003 Functional Requirements - **READY**

---

## For Kamal:

### Final Document:
- [ ] UC-003 Test Cases (3 test cases) - **TO BE COMPLETED**
  - [ ] TC-003-01: Successful Password Reset (Sunny Day)
  - [ ] TC-003-02: Expired Token (Rainy Day)
  - [ ] TC-003-03: Invalid Email (Rainy Day)
- [ ] UC-004 Test Cases (10 test cases) - **TO BE COMPLETED**
  - [ ] TC-004-01: Successful Registration (Sunny Day)
  - [ ] TC-004-02: Email Already Exists (Rainy Day)
  - [ ] TC-004-03: Weak Password (Rainy Day)
  - [ ] TC-004-04: Password Mismatch (Rainy Day)
  - [ ] TC-004-05: Invalid Email Format (Rainy Day)
  - [ ] TC-004-06: Missing Required Fields (Rainy Day)
  - [ ] TC-004-07: Database Error (Rainy Day)
  - [ ] TC-004-08: Registration Timeout (Rainy Day)
  - [ ] TC-004-09: SQL Injection (Rainy Day)
  - [ ] TC-004-10: Registration with Optional Fields (Sunny Day)

### Presentation:
- [x] Slides 20-21, 23: UC-003 Test Cases - **READY**

---

# 📞 COORDINATION NOTES

## For Alexandra:
1. **Test Case Collection:** You need to collect test cases from:
   - Andre: UC-001, UC-005 (already in document)
   - Kamal: UC-003, UC-004 (to be provided)
   - Alfonso: UC-007 (to be provided)
   - Yourself: UC-002, UC-006 (to be completed)

2. **Chapter 7 Compilation:** 
   - Organize all test cases in Section 7.1.3
   - Update test results summary in Section 7.2
   - Ensure format consistency

3. **Format Consistency:**
   - Use the same format as `MenuMap_Test_Cases_Login_UC001.md`
   - Include database state tables for each test case
   - Follow CEN4010 requirements

## For Kamal:
1. **Test Case Format:**
   - Follow the format in `MenuMap_Test_Cases_Login_UC001.md`
   - Include database state tables
   - Be detailed with test steps

2. **Delivery:**
   - Provide test cases to Alexandra for Chapter 7 compilation
   - Or add directly to `Deliverable3_Final_Document_Team9.md` in Section 7.1.3

3. **Presentation Preparation:**
   - Review slides 20-21, 23 content
   - Practice explaining data models
   - Time yourself (3-4 minutes)

---

# 🎯 DEADLINES

**All test cases should be completed and added to the final document before submission.**

**Repository:** `AndreLewis1400/MenuMap`  
**Branch:** `main`  
**Folder:** `Deliverable3_Implementation/`

---

**Last Updated:** December 2024  
**Document Owner:** Team Lead (Andre Lewis)  
**For Questions:** Contact Team Lead

