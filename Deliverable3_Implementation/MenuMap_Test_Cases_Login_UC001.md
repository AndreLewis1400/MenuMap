# MenuMap Test Cases - Deliverable 3
## UC-005: User Login & UC-001: Browse Restaurant Menus

---

## 📋 **Test Case Format**

Based on CEN4010 requirements, each test case includes:
- **Test Case ID**: Unique identifier (e.g., SystemTest-001-UC005)
- **Purpose**: What the test case validates
- **Test Setup**: Preconditions including database state
- **Test Input**: Step-by-step actions
- **Expected Output**: Expected results

---

## 🔐 **UC-005: User Login**

### **Database State Tables**

#### **Table 1: Users Table (Before Test Execution)**

| User ID | Password (Hashed) | Email | First Name | Last Name | Account Status | Email Verified |
|---------|-------------------|-------|------------|-----------|----------------|----------------|
| johndoe | $2a$10$hashed123 | johndoe@example.com | John | Doe | Active | Yes |
| janedoe | $2a$10$hashed456 | janedoe@example.com | Jane | Doe | Active | Yes |
| lockeduser | $2a$10$hashed789 | locked@example.com | Locked | User | Locked | Yes |
| unverified | $2a$10$hashed000 | unverified@example.com | Unverified | User | Active | No |

---

## 🌞 **UC-005: User Login - SUNNY DAY SCENARIOS**

### **TC-005-01: Successful Login (Sunny Day)**

**Test Case ID:** SystemTest-001-UC005 (sunny day scenario)

**Purpose:** Verify that a valid user can successfully log into the MenuMap system with correct credentials.

**Test Setup:**
1. User "johndoe" exists in database (see Table 1)
2. User account is active
3. User email is verified
4. MenuMap login page is accessible
5. Database is accessible and responsive

**Test Input:**
1. User navigates to MenuMap login page
2. User enters the following data:
   a. Email/User ID: `johndoe@example.com`
   b. Password: `SecurePass123!`
3. User clicks "Login" button

**Expected Output:**
1. System validates credentials successfully
2. System creates user session
3. User is redirected to MenuMap homepage/dashboard
4. Welcome message displays: "Welcome, John Doe"
5. User is authenticated and can access protected features
6. No error messages displayed

**Postconditions:**
- User session is created in database
- User is logged in and authenticated
- User can navigate to other pages

---

### **TC-005-02: Successful Login with User ID**

**Test Case ID:** SystemTest-002-UC005 (sunny day scenario)

**Purpose:** Verify that a user can log in using their User ID instead of email.

**Test Setup:**
1. User "johndoe" exists in database (see Table 1)
2. User account is active and verified
3. MenuMap login page is accessible

**Test Input:**
1. User navigates to MenuMap login page
2. User enters the following data:
   a. Email/User ID: `johndoe`
   b. Password: `SecurePass123!`
3. User clicks "Login" button

**Expected Output:**
1. System accepts User ID as valid identifier
2. System validates credentials successfully
3. User is redirected to homepage
4. Welcome message displays: "Welcome, John Doe"
5. No error messages displayed

**Postconditions:**
- User is successfully logged in
- Session is created

---

## 🌧️ **UC-005: User Login - RAINY DAY SCENARIOS**

### **TC-005-03: Invalid Password**

**Test Case ID:** SystemTest-003-UC005 (rainy day scenario)

**Purpose:** Verify that system rejects login attempt with incorrect password.

**Test Setup:**
1. User "johndoe" exists in database (see Table 1)
2. User account is active and verified
3. MenuMap login page is accessible

**Test Input:**
1. User navigates to MenuMap login page
2. User enters the following data:
   a. Email/User ID: `johndoe@example.com`
   b. Password: `WrongPassword123`
3. User clicks "Login" button

**Expected Output:**
1. System validates credentials
2. System detects password mismatch
3. Error message displays: "Invalid email or password. Please try again."
4. User remains on login page
5. Password field is cleared (for security)
6. User can retry login
7. No session is created

**Postconditions:**
- User is NOT logged in
- No session created
- User can attempt login again

---

### **TC-005-04: User Not Found (Invalid Email)**

**Test Case ID:** SystemTest-004-UC005 (rainy day scenario)

**Purpose:** Verify that system handles login attempt with non-existent email/user ID.

**Test Setup:**
1. Email "nonexistent@example.com" does NOT exist in database
2. MenuMap login page is accessible

**Test Input:**
1. User navigates to MenuMap login page
2. User enters the following data:
   a. Email/User ID: `nonexistent@example.com`
   b. Password: `AnyPassword123`
3. User clicks "Login" button

**Expected Output:**
1. System searches for user in database
2. System finds no matching user
3. Error message displays: "Invalid email or password. Please try again."
   (Note: Generic message for security - doesn't reveal if email exists)
4. User remains on login page
5. No session is created

**Postconditions:**
- No user session created
- User can retry with correct credentials

---

### **TC-005-05: Empty Required Fields**

**Test Case ID:** SystemTest-005-UC005 (rainy day scenario)

**Purpose:** Verify that system validates required fields before processing login.

**Test Setup:**
1. MenuMap login page is accessible

**Test Input:**
1. User navigates to MenuMap login page
2. User leaves email field empty: `""`
3. User enters password: `SecurePass123!`
4. User clicks "Login" button

**Expected Output:**
1. System validates input before processing
2. Error message displays: "Required field missing input value" or "Please enter your email"
3. Email field is highlighted or marked with error
4. User remains on login page
5. No login attempt is processed
6. No database query is executed

**Postconditions:**
- No login attempt processed
- User can fill in required fields and retry

**Additional Test:** Repeat with empty password field, empty both fields

---

### **TC-005-06: Account Locked**

**Test Case ID:** SystemTest-006-UC005 (rainy day scenario)

**Purpose:** Verify that system prevents login for locked accounts.

**Test Setup:**
1. User "lockeduser" exists in database (see Table 1)
2. User account status is "Locked"
3. MenuMap login page is accessible

**Test Input:**
1. User navigates to MenuMap login page
2. User enters the following data:
   a. Email/User ID: `locked@example.com`
   b. Password: `CorrectPassword123`
3. User clicks "Login" button

**Expected Output:**
1. System validates credentials (may be correct)
2. System checks account status
3. System detects account is locked
4. Error message displays: "Your account has been locked. Please contact support."
5. User remains on login page
6. No session is created
7. User cannot proceed with login

**Postconditions:**
- No session created
- Account remains locked
- User must contact support

---

### **TC-005-07: Email Not Verified**

**Test Case ID:** SystemTest-007-UC005 (rainy day scenario)

**Purpose:** Verify that system handles login attempt for unverified email accounts.

**Test Setup:**
1. User "unverified" exists in database (see Table 1)
2. User account is active but email is NOT verified
3. MenuMap login page is accessible

**Test Input:**
1. User navigates to MenuMap login page
2. User enters the following data:
   a. Email/User ID: `unverified@example.com`
   b. Password: `CorrectPassword123`
3. User clicks "Login" button

**Expected Output:**
1. System validates credentials successfully
2. System checks email verification status
3. System detects email is not verified
4. Warning message displays: "Please verify your email address before logging in. Check your inbox for verification link."
5. Option to resend verification email is provided
6. User may be redirected to verification page or remain on login
7. Limited session may be created (depends on system design)

**Postconditions:**
- User may have limited access or no access
- Verification reminder is shown

---

### **TC-005-08: SQL Injection Attempt**

**Test Case ID:** SystemTest-008-UC005 (rainy day scenario)

**Purpose:** Verify that system prevents SQL injection attacks in login fields.

**Test Setup:**
1. MenuMap login page is accessible
2. Database is accessible

**Test Input:**
1. User navigates to MenuMap login page
2. User enters the following data:
   a. Email/User ID: `admin' OR '1'='1`
   b. Password: `anything' OR '1'='1`
3. User clicks "Login" button

**Expected Output:**
1. System sanitizes/escapes input
2. SQL injection is prevented
3. System treats as invalid input
4. Error message displays: "Invalid email or password. Please try again."
5. No SQL commands are executed
6. Database security is maintained
7. No unauthorized access granted

**Postconditions:**
- No security breach
- System remains secure
- Invalid login attempt logged (if logging enabled)

---

### **TC-005-09: Database Connection Error**

**Test Case ID:** SystemTest-009-UC005 (rainy day scenario)

**Purpose:** Verify that system handles database unavailability during login.

**Test Setup:**
1. User "johndoe" exists in database
2. Database server is down or unreachable
3. MenuMap login page is accessible

**Test Input:**
1. User navigates to MenuMap login page
2. User enters the following data:
   a. Email/User ID: `johndoe@example.com`
   b. Password: `SecurePass123!`
3. User clicks "Login" button

**Expected Output:**
1. System attempts database connection
2. Database connection fails
3. User-friendly error message displays: "We're experiencing technical difficulties. Please try again in a few moments."
4. Error is logged for administrators
5. User remains on login page
6. No session is created
7. System remains stable

**Postconditions:**
- No session created
- Error is logged
- User can retry when database is available

---

### **TC-005-10: Multiple Failed Login Attempts (Account Lockout)**

**Test Case ID:** SystemTest-010-UC005 (rainy day scenario)

**Purpose:** Verify that system locks account after multiple failed login attempts.

**Test Setup:**
1. User "johndoe" exists in database (see Table 1)
2. Account is currently active
3. MenuMap login page is accessible
4. System has lockout policy: 5 failed attempts = account locked

**Test Input:**
1. User navigates to MenuMap login page
2. User attempts login 5 times with incorrect password:
   - Attempt 1: Email: `johndoe@example.com`, Password: `Wrong1`
   - Attempt 2: Email: `johndoe@example.com`, Password: `Wrong2`
   - Attempt 3: Email: `johndoe@example.com`, Password: `Wrong3`
   - Attempt 4: Email: `johndoe@example.com`, Password: `Wrong4`
   - Attempt 5: Email: `johndoe@example.com`, Password: `Wrong5`
3. User clicks "Login" button for each attempt

**Expected Output:**
- Attempts 1-4: Error message: "Invalid email or password. X attempts remaining."
- Attempt 5: Error message: "Your account has been locked due to multiple failed login attempts. Please contact support."
- Account status in database changes to "Locked"
- No session is created
- User cannot proceed with login

**Postconditions:**
- Account is locked in database
- User must contact support to unlock
- Failed attempts are logged

---

## 🍽️ **UC-001: Browse Restaurant Menus**

### **Database State Tables**

#### **Table 2: Restaurants Table (Before Test Execution)**

| Restaurant ID | Restaurant Name | Address | Phone | Status | Owner User ID |
|---------------|-----------------|---------|-------|--------|---------------|
| 101 | Joe's Pizza | 123 Main St, Miami, FL | 305-555-0101 | Active | johndoe |
| 102 | Burger Palace | 456 Oak Ave, Miami, FL | 305-555-0102 | Active | janedoe |
| 103 | Closed Restaurant | 789 Pine Rd, Miami, FL | 305-555-0103 | Inactive | lockeduser |
| 999 | NonExistent | N/A | N/A | N/A | N/A |

#### **Table 3: Menu Items Table (Before Test Execution)**

| Menu Item ID | Restaurant ID | Item Name | Description | Price | Category | Available |
|--------------|---------------|-----------|-------------|-------|----------|-----------|
| 1001 | 101 | Margherita Pizza | Classic tomato and mozzarella | $12.99 | Entree | Yes |
| 1002 | 101 | Pepperoni Pizza | Pepperoni and cheese | $14.99 | Entree | Yes |
| 1003 | 101 | Caesar Salad | Fresh romaine with Caesar dressing | $8.99 | Appetizer | Yes |
| 1004 | 102 | Classic Burger | Beef patty with lettuce and tomato | $9.99 | Entree | Yes |
| 1005 | 102 | French Fries | Crispy golden fries | $3.99 | Side | Yes |
| 1006 | 103 | Old Menu Item | Item from closed restaurant | $5.99 | Entree | No |

---

## 🌞 **UC-001: Browse Restaurant Menus - SUNNY DAY SCENARIOS**

### **TC-001-01: Successful Menu Browse (Sunny Day)**

**Test Case ID:** SystemTest-011-UC001 (sunny day scenario)

**Purpose:** Verify that a user can successfully browse and view a restaurant menu with all items displayed correctly.

**Test Setup:**
1. User is on MenuMap homepage (may be logged in or not, depending on system design)
2. Restaurant "Joe's Pizza" (ID: 101) exists in database (see Table 2)
3. Restaurant has menu items in database (see Table 3: items 1001, 1002, 1003)
4. Database is accessible and responsive

**Test Input:**
1. User navigates to MenuMap application
2. User enters restaurant name in search field: `Joe's Pizza`
3. User clicks "Search" button
4. System displays search results
5. User selects "Joe's Pizza" from results
6. User clicks "View Menu" button

**Expected Output:**
1. Search returns matching restaurant: "Joe's Pizza"
2. Restaurant details are displayed correctly
3. Menu loads successfully from database
4. Menu displays all items for restaurant ID 101:
   - Margherita Pizza - $12.99 (Entree)
   - Pepperoni Pizza - $14.99 (Entree)
   - Caesar Salad - $8.99 (Appetizer)
5. Items are organized by category (if applicable)
6. Prices are formatted correctly
7. No error messages displayed
8. Response time is acceptable (< 2 seconds)

**Postconditions:**
- Menu is displayed to user
- User can continue browsing or navigate away
- No data is modified in database

---

### **TC-001-02: Browse Menu with Filters**

**Test Case ID:** SystemTest-012-UC001 (sunny day scenario)

**Purpose:** Verify that user can filter menu items by category successfully.

**Test Setup:**
1. User is viewing "Joe's Pizza" menu (see TC-001-01 setup)
2. Menu has items in multiple categories (see Table 3)

**Test Input:**
1. User is viewing "Joe's Pizza" menu
2. User clicks on "Appetizers" filter button
3. System filters menu items
4. User clicks on "Entrees" filter button
5. System updates displayed items
6. User clears filter
7. System displays all items

**Expected Output:**
1. When "Appetizers" selected: Only Caesar Salad is displayed
2. When "Entrees" selected: Only Margherita Pizza and Pepperoni Pizza are displayed
3. When filter cleared: All 3 items are displayed
4. Menu updates dynamically without page reload (if applicable)
5. No items are lost or duplicated
6. Filter state is maintained correctly

**Postconditions:**
- Menu display reflects selected filter
- User can continue filtering or viewing full menu

---

## 🌧️ **UC-001: Browse Restaurant Menus - RAINY DAY SCENARIOS**

### **TC-001-03: Restaurant Not Found**

**Test Case ID:** SystemTest-013-UC001 (rainy day scenario)

**Purpose:** Verify that system handles search for non-existent restaurant gracefully.

**Test Setup:**
1. User is on MenuMap homepage
2. Restaurant "NonExistent" (ID: 999) does NOT exist in database
3. Database is accessible

**Test Input:**
1. User navigates to MenuMap application
2. User enters restaurant name in search field: `NonExistent Restaurant`
3. User clicks "Search" button
4. System searches database

**Expected Output:**
1. System queries database for matching restaurants
2. System finds no matching results
3. Message displays: "No restaurants found matching your search. Please try a different search term."
4. Search results page shows empty state with helpful message
5. User can try a new search
6. No error stack trace or technical details shown to user
7. System remains stable and responsive

**Postconditions:**
- User is on search results page
- User can perform new search
- No data corruption or system errors

---

### **TC-001-04: Menu Not Available (Empty Menu)**

**Test Case ID:** SystemTest-014-UC001 (rainy day scenario)

**Purpose:** Verify that system handles restaurant with no menu items gracefully.

**Test Setup:**
1. Restaurant "Burger Palace" (ID: 102) exists in database (see Table 2)
2. Restaurant has NO menu items in database (remove items 1004, 1005 for this test)
3. User is on MenuMap application

**Test Input:**
1. User searches for restaurant: `Burger Palace`
2. User finds restaurant in search results
3. User clicks "View Menu" button
4. System attempts to retrieve menu

**Expected Output:**
1. System finds restaurant successfully
2. System queries for menu items
3. System finds no menu items for restaurant ID 102
4. Message displays: "This restaurant has not added menu items yet. Please check back later."
5. Restaurant information is displayed (name, address, etc.)
6. Menu section shows empty state message
7. No error messages or crashes
8. User can navigate back or contact restaurant

**Postconditions:**
- User sees empty menu state
- System handles gracefully without errors
- Restaurant information is still accessible

---

### **TC-001-05: Database Connection Error**

**Test Case ID:** SystemTest-015-UC001 (rainy day scenario)

**Purpose:** Verify that system handles database unavailability when browsing menus.

**Test Setup:**
1. User is on MenuMap application
2. Database server is down or unreachable
3. Restaurant "Joe's Pizza" exists in database

**Test Input:**
1. User searches for restaurant: `Joe's Pizza`
2. User selects restaurant from results
3. User clicks "View Menu" button
4. System attempts database connection

**Expected Output:**
1. System attempts to connect to database
2. Database connection fails
3. User-friendly error message displays: "We're having trouble loading the menu. Please try again in a moment."
4. Error is logged for administrators with technical details
5. User can retry the operation
6. System does not crash or show technical error details
7. User can navigate to other parts of application

**Postconditions:**
- Error is handled gracefully
- System remains functional for other operations
- User can attempt operation again later

---

### **TC-001-06: Invalid Search Input (SQL Injection)**

**Test Case ID:** SystemTest-016-UC001 (rainy day scenario)

**Purpose:** Verify that system prevents SQL injection attacks in search field.

**Test Setup:**
1. User is on MenuMap homepage
2. Database is accessible

**Test Input:**
1. User navigates to MenuMap application
2. User enters malicious input in search field: `'; DROP TABLE restaurants; --`
3. User clicks "Search" button
4. System processes input

**Expected Output:**
1. Input is sanitized/validated
2. SQL injection is prevented
3. System treats as invalid or empty search
4. Message displays: "Please enter a valid search term" or "No restaurants found"
5. No SQL commands are executed
6. Database tables remain intact
7. No security vulnerabilities exploited

**Postconditions:**
- Database security maintained
- No data loss
- System remains secure

---

### **TC-001-07: Timeout During Menu Load**

**Test Case ID:** SystemTest-017-UC001 (rainy day scenario)

**Purpose:** Verify that system handles timeout when menu loading takes too long.

**Test Setup:**
1. Restaurant "Joe's Pizza" exists in database
2. Database is slow or under heavy load
3. Network connection is slow
4. System timeout threshold: 30 seconds

**Test Input:**
1. User searches for restaurant: `Joe's Pizza`
2. User selects restaurant
3. User clicks "View Menu" button
4. System attempts to load menu
5. Request exceeds timeout threshold

**Expected Output:**
1. System attempts to load menu
2. Request exceeds 30-second timeout
3. Timeout message displays: "The request took too long. Please try again."
4. User can retry the operation
5. System cancels the request
6. No partial data is displayed
7. System remains responsive

**Postconditions:**
- User can retry or navigate away
- System handles timeout gracefully
- No partial state corruption

---

### **TC-001-08: Restaurant Inactive/Closed**

**Test Case ID:** SystemTest-018-UC001 (rainy day scenario)

**Purpose:** Verify that system handles viewing menu for inactive/closed restaurant.

**Test Setup:**
1. Restaurant "Closed Restaurant" (ID: 103) exists in database (see Table 2)
2. Restaurant status is "Inactive"
3. Restaurant may or may not have menu items

**Test Input:**
1. User searches for restaurant: `Closed Restaurant`
2. User finds restaurant in results (if inactive restaurants are shown)
3. User clicks "View Menu" button
4. System processes request

**Expected Output:**
1. System checks restaurant status
2. System detects restaurant is inactive
3. Message displays: "This restaurant is currently closed or inactive. Menu is not available."
4. Restaurant information may be shown with inactive status
5. Menu is not displayed (or shown as unavailable)
6. User can search for other restaurants
7. No error messages or crashes

**Postconditions:**
- User sees inactive restaurant message
- System handles gracefully
- User can continue browsing

---

## 📊 **Test Case Summary**

### **UC-005: User Login**
- **Sunny Day:** 2 test cases (TC-005-01, TC-005-02)
- **Rainy Day:** 8 test cases (TC-005-03 through TC-005-10)
- **Total:** 10 test cases

### **UC-001: Browse Restaurant Menus**
- **Sunny Day:** 2 test cases (TC-001-01, TC-001-02)
- **Rainy Day:** 6 test cases (TC-001-03 through TC-001-08)
- **Total:** 8 test cases

### **Overall Summary**
- **Total Test Cases:** 18
- **Sunny Day:** 4 test cases
- **Rainy Day:** 14 test cases
- **All test cases include database state tables**

---

## ✅ **Test Execution Checklist**

### **Before Testing:**
- [ ] Test environment is set up
- [ ] Database is accessible
- [ ] Test data is prepared (see Tables 1, 2, 3)
- [ ] Test accounts are created
- [ ] Test restaurants and menu items are created

### **During Testing:**
- [ ] Execute each test case step-by-step
- [ ] Document actual results vs expected results
- [ ] Take screenshots of errors (if applicable)
- [ ] Note any deviations from expected behavior
- [ ] Verify database state before and after tests

### **After Testing:**
- [ ] Review all test results
- [ ] Document any bugs found
- [ ] Update test cases if needed
- [ ] Prepare test report for Deliverable 3

---

## 📝 **Notes for Deliverable 3 Submission**

1. **Format:** These test cases follow the CEN4010 format shown in lecture examples
2. **Database Tables:** Include database state tables before each test case section
3. **Documentation:** Include this test case document in your Final Document
4. **Implementation Evidence:** Reference code snippets that handle each scenario
5. **No Papyrus Required:** Test cases are written documentation, not diagrams

---

**This document provides comprehensive test coverage for UC-005 (Login) and UC-001 (Browse Restaurant Menus) with both successful and error scenarios, following CEN4010 Software Engineering standards.**

