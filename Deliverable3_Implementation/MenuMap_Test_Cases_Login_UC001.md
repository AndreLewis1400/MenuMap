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

## 🌞 **UC-005: User Login - SUNNY DAY SCENARIOS**

### **TC-005-01: Successful Login (Sunny Day)**

**Test Case ID:** SystemTest-001-UC005 (sunny day scenario)

**Purpose:** Verify that user "johndoe" can successfully log into the MenuMap system with correct credentials.

#### **Table TC-005-01: Users Table (Before Test Execution)**

| User ID | Password (Hashed) | Email | First Name | Last Name | Account Status | Email Verified |
|---------|-------------------|-------|------------|-----------|----------------|----------------|
| johndoe | $2a$10$hashed123 | johndoe@example.com | John | Doe | Active | Yes |

**Test Setup:**
1. User "johndoe" exists in database (see Table TC-005-01)
2. User "johndoe" account is active
3. User "johndoe" email is verified
4. MenuMap login page is accessible
5. Database is accessible and responsive

**Test Input:**
1. User "johndoe" navigates to MenuMap login page
2. User "johndoe" enters the following data:
   a. Email/User ID: `johndoe@example.com`
   b. Password: `SecurePass123!`
3. User "johndoe" clicks "Login" button

**Expected Output:**
1. System validates credentials successfully
2. System creates user session for user "johndoe"
3. User "johndoe" is redirected to MenuMap homepage/dashboard
4. Welcome message displays: "Welcome, John Doe"
5. User "johndoe" is authenticated and can access protected features
6. No error messages displayed

---

### **TC-005-02: Successful Login with User ID**

**Test Case ID:** SystemTest-002-UC005 (sunny day scenario)

**Purpose:** Verify that user "johndoe" can log in using their User ID instead of email.

#### **Table TC-005-02: Users Table (Before Test Execution)**

| User ID | Password (Hashed) | Email | First Name | Last Name | Account Status | Email Verified |
|---------|-------------------|-------|------------|-----------|----------------|----------------|
| johndoe | $2a$10$hashed123 | johndoe@example.com | John | Doe | Active | Yes |

**Test Setup:**
1. User "johndoe" exists in database (see Table TC-005-02)
2. User "johndoe" account is active and verified
3. MenuMap login page is accessible

**Test Input:**
1. User "johndoe" navigates to MenuMap login page
2. User "johndoe" enters the following data:
   a. Email/User ID: `johndoe`
   b. Password: `SecurePass123!`
3. User "johndoe" clicks "Login" button

**Expected Output:**
1. System accepts User ID as valid identifier
2. System validates credentials successfully
3. User "johndoe" is redirected to homepage
4. Welcome message displays: "Welcome, John Doe"
5. No error messages displayed

---

## 🌧️ **UC-005: User Login - RAINY DAY SCENARIOS**

### **TC-005-03: Invalid Password**

**Test Case ID:** SystemTest-003-UC005 (rainy day scenario)

**Purpose:** Verify that system rejects login attempt for user "johndoe" with incorrect password.

#### **Table TC-005-03: Users Table (Before Test Execution)**

| User ID | Password (Hashed) | Email | First Name | Last Name | Account Status | Email Verified |
|---------|-------------------|-------|------------|-----------|----------------|----------------|
| johndoe | $2a$10$hashed123 | johndoe@example.com | John | Doe | Active | Yes |

**Test Setup:**
1. User "johndoe" exists in database (see Table TC-005-03)
2. User "johndoe" account is active and verified
3. MenuMap login page is accessible

**Test Input:**
1. User "johndoe" navigates to MenuMap login page
2. User "johndoe" enters the following data:
   a. Email/User ID: `johndoe@example.com`
   b. Password: `WrongPassword123`
3. User "johndoe" clicks "Login" button

**Expected Output:**
1. System validates credentials
2. System detects password mismatch for user "johndoe"
3. Error message displays: "Invalid email or password. Please try again."
4. User "johndoe" remains on login page
5. Password field is cleared (for security)
6. User "johndoe" can retry login
7. No session is created for user "johndoe"

---

### **TC-005-04: User Not Found (Invalid Email)**

**Test Case ID:** SystemTest-004-UC005 (rainy day scenario)

**Purpose:** Verify that system handles login attempt with non-existent email/user ID.

#### **Table TC-005-04: Users Table (Before Test Execution)**

| User ID | Password (Hashed) | Email | First Name | Last Name | Account Status | Email Verified |
|---------|-------------------|-------|------------|-----------|----------------|----------------|
| (No users exist) | | | | | | |

**Test Setup:**
1. Email "nonexistent@example.com" does NOT exist in database (see Table TC-005-04)
2. MenuMap login page is accessible

**Test Input:**
1. Test user navigates to MenuMap login page
2. Test user enters the following data:
   a. Email/User ID: `nonexistent@example.com`
   b. Password: `AnyPassword123`
3. Test user clicks "Login" button

**Expected Output:**
1. System searches for user in database
2. System finds no matching user
3. Error message displays: "Invalid email or password. Please try again."
   (Note: Generic message for security - doesn't reveal if email exists)
4. Test user remains on login page
5. No session is created

---

### **TC-005-05: Empty Required Fields**

**Test Case ID:** SystemTest-005-UC005 (rainy day scenario)

**Purpose:** Verify that system validates required fields before processing login.

#### **Table TC-005-05: Users Table (Before Test Execution)**

| User ID | Password (Hashed) | Email | First Name | Last Name | Account Status | Email Verified |
|---------|-------------------|-------|------------|-----------|----------------|----------------|
| (Not applicable - no database query) | | | | | | |

**Test Setup:**
1. MenuMap login page is accessible

**Test Input:**
1. Test user navigates to MenuMap login page
2. Test user leaves email field empty: `""`
3. Test user enters password: `SecurePass123!`
4. Test user clicks "Login" button

**Expected Output:**
1. System validates input before processing
2. Error message displays: "Required field missing input value" or "Please enter your email"
3. Email field is highlighted or marked with error
4. Test user remains on login page
5. No login attempt is processed
6. No database query is executed

**Additional Test:** Repeat with empty password field, empty both fields

---

### **TC-005-06: Account Locked**

**Test Case ID:** SystemTest-006-UC005 (rainy day scenario)

**Purpose:** Verify that system prevents login for locked account "lockeduser".

#### **Table TC-005-06: Users Table (Before Test Execution)**

| User ID | Password (Hashed) | Email | First Name | Last Name | Account Status | Email Verified |
|---------|-------------------|-------|------------|-----------|----------------|----------------|
| lockeduser | $2a$10$hashed789 | locked@example.com | Locked | User | Locked | Yes |

**Test Setup:**
1. User "lockeduser" exists in database (see Table TC-005-06)
2. User "lockeduser" account status is "Locked"
3. MenuMap login page is accessible

**Test Input:**
1. User "lockeduser" navigates to MenuMap login page
2. User "lockeduser" enters the following data:
   a. Email/User ID: `locked@example.com`
   b. Password: `CorrectPassword123`
3. User "lockeduser" clicks "Login" button

**Expected Output:**
1. System validates credentials (may be correct)
2. System checks account status for user "lockeduser"
3. System detects account "lockeduser" is locked
4. Error message displays: "Your account has been locked. Please contact support."
5. User "lockeduser" remains on login page
6. No session is created for user "lockeduser"
7. User "lockeduser" cannot proceed with login

---

### **TC-005-07: Email Not Verified**

**Test Case ID:** SystemTest-007-UC005 (rainy day scenario)

**Purpose:** Verify that system handles login attempt for unverified email account "unverified".

#### **Table TC-005-07: Users Table (Before Test Execution)**

| User ID | Password (Hashed) | Email | First Name | Last Name | Account Status | Email Verified |
|---------|-------------------|-------|------------|-----------|----------------|----------------|
| unverified | $2a$10$hashed000 | unverified@example.com | Unverified | User | Active | No |

**Test Setup:**
1. User "unverified" exists in database (see Table TC-005-07)
2. User "unverified" account is active but email is NOT verified
3. MenuMap login page is accessible

**Test Input:**
1. User "unverified" navigates to MenuMap login page
2. User "unverified" enters the following data:
   a. Email/User ID: `unverified@example.com`
   b. Password: `CorrectPassword123`
3. User "unverified" clicks "Login" button

**Expected Output:**
1. System validates credentials successfully for user "unverified"
2. System checks email verification status for user "unverified"
3. System detects email is not verified for user "unverified"
4. Warning message displays: "Please verify your email address before logging in. Check your inbox for verification link."
5. Option to resend verification email is provided
6. User "unverified" may be redirected to verification page or remain on login
7. Limited session may be created for user "unverified" (depends on system design)

---

### **TC-005-08: SQL Injection Attempt**

**Test Case ID:** SystemTest-008-UC005 (rainy day scenario)

**Purpose:** Verify that system prevents SQL injection attacks in login fields.

#### **Table TC-005-08: Users Table (Before Test Execution)**

| User ID | Password (Hashed) | Email | First Name | Last Name | Account Status | Email Verified |
|---------|-------------------|-------|------------|-----------|----------------|----------------|
| (Not applicable - security test) | | | | | | |

**Test Setup:**
1. MenuMap login page is accessible
2. Database is accessible

**Test Input:**
1. Attacker navigates to MenuMap login page
2. Attacker enters the following data:
   a. Email/User ID: `admin' OR '1'='1`
   b. Password: `anything' OR '1'='1`
3. Attacker clicks "Login" button

**Expected Output:**
1. System sanitizes/escapes input
2. SQL injection is prevented
3. System treats as invalid input
4. Error message displays: "Invalid email or password. Please try again."
5. No SQL commands are executed
6. Database security is maintained
7. No unauthorized access granted

---

### **TC-005-09: Database Connection Error**

**Test Case ID:** SystemTest-009-UC005 (rainy day scenario)

**Purpose:** Verify that system handles database unavailability during login for user "johndoe".

#### **Table TC-005-09: Users Table (Before Test Execution)**

| User ID | Password (Hashed) | Email | First Name | Last Name | Account Status | Email Verified |
|---------|-------------------|-------|------------|-----------|----------------|----------------|
| johndoe | $2a$10$hashed123 | johndoe@example.com | John | Doe | Active | Yes |

**Test Setup:**
1. User "johndoe" exists in database (see Table TC-005-09)
2. Database server is down or unreachable
3. MenuMap login page is accessible

**Test Input:**
1. User "johndoe" navigates to MenuMap login page
2. User "johndoe" enters the following data:
   a. Email/User ID: `johndoe@example.com`
   b. Password: `SecurePass123!`
3. User "johndoe" clicks "Login" button

**Expected Output:**
1. System attempts database connection
2. Database connection fails
3. User-friendly error message displays: "We're experiencing technical difficulties. Please try again in a few moments."
4. Error is logged for administrators
5. User "johndoe" remains on login page
6. No session is created for user "johndoe"
7. System remains stable

---

### **TC-005-10: Multiple Failed Login Attempts (Account Lockout)**

**Test Case ID:** SystemTest-010-UC005 (rainy day scenario)

**Purpose:** Verify that system locks account "johndoe" after multiple failed login attempts.

#### **Table TC-005-10: Users Table (Before Test Execution)**

| User ID | Password (Hashed) | Email | First Name | Last Name | Account Status | Email Verified |
|---------|-------------------|-------|------------|-----------|----------------|----------------|
| johndoe | $2a$10$hashed123 | johndoe@example.com | John | Doe | Active | Yes |

**Test Setup:**
1. User "johndoe" exists in database (see Table TC-005-10)
2. User "johndoe" account is currently active
3. MenuMap login page is accessible
4. System has lockout policy: 5 failed attempts = account locked

**Test Input:**
1. User "johndoe" navigates to MenuMap login page
2. User "johndoe" attempts login 5 times with incorrect password:
   - Attempt 1: Email: `johndoe@example.com`, Password: `Wrong1`
   - Attempt 2: Email: `johndoe@example.com`, Password: `Wrong2`
   - Attempt 3: Email: `johndoe@example.com`, Password: `Wrong3`
   - Attempt 4: Email: `johndoe@example.com`, Password: `Wrong4`
   - Attempt 5: Email: `johndoe@example.com`, Password: `Wrong5`
3. User "johndoe" clicks "Login" button for each attempt

**Expected Output:**
- Attempts 1-4: Error message: "Invalid email or password. X attempts remaining."
- Attempt 5: Error message: "Your account has been locked due to multiple failed login attempts. Please contact support."
- User "johndoe" account status in database changes to "Locked"
- No session is created for user "johndoe"
- User "johndoe" cannot proceed with login

---

## 🍽️ **UC-001: Browse Restaurant Menus**

## 🌞 **UC-001: Browse Restaurant Menus - SUNNY DAY SCENARIOS**

### **TC-001-01: Successful Menu Browse (Sunny Day)**

**Test Case ID:** SystemTest-011-UC001 (sunny day scenario)

**Purpose:** Verify that a user can successfully browse and view a restaurant menu with all items displayed correctly.

#### **Table TC-001-01: Restaurants Table (Before Test Execution)**

| Restaurant ID | Restaurant Name | Address | Phone | Status | Owner User ID |
|---------------|-----------------|---------|-------|--------|---------------|
| 101 | Joe's Pizza | 123 Main St, Miami, FL | 305-555-0101 | Active | johndoe |

#### **Table TC-001-01: Menu Items Table (Before Test Execution)**

| Menu Item ID | Restaurant ID | Item Name | Description | Price | Category | Available |
|--------------|---------------|-----------|-------------|-------|----------|-----------|
| 1001 | 101 | Margherita Pizza | Classic tomato and mozzarella | $12.99 | Entree | Yes |
| 1002 | 101 | Pepperoni Pizza | Pepperoni and cheese | $14.99 | Entree | Yes |
| 1003 | 101 | Caesar Salad | Fresh romaine with Caesar dressing | $8.99 | Appetizer | Yes |

**Test Setup:**
1. User "janedoe" is on MenuMap homepage (may be logged in or not, depending on system design)
2. Restaurant "Joe's Pizza" (ID: 101) exists in database (see Table TC-001-01: Restaurants)
3. Restaurant "Joe's Pizza" has menu items in database (see Table TC-001-01: Menu Items)
4. Database is accessible and responsive

**Test Input:**
1. User "janedoe" navigates to MenuMap application
2. User "janedoe" enters restaurant name in search field: `Joe's Pizza`
3. User "janedoe" clicks "Search" button
4. System displays search results
5. User "janedoe" selects "Joe's Pizza" from results
6. User "janedoe" clicks "View Menu" button

**Expected Output:**
1. Search returns matching restaurant: "Joe's Pizza"
2. Restaurant "Joe's Pizza" details are displayed correctly
3. Menu for restaurant "Joe's Pizza" loads successfully from database
4. Menu for restaurant "Joe's Pizza" displays all items for restaurant ID 101:
   - Margherita Pizza - $12.99 (Entree)
   - Pepperoni Pizza - $14.99 (Entree)
   - Caesar Salad - $8.99 (Appetizer)
5. Items are organized by category (if applicable)
6. Prices are formatted correctly
7. No error messages displayed
8. Response time is acceptable (< 2 seconds)

---

### **TC-001-02: Browse Menu with Filters**

**Test Case ID:** SystemTest-012-UC001 (sunny day scenario)

**Purpose:** Verify that user can filter menu items by category successfully.

#### **Table TC-001-02: Restaurants Table (Before Test Execution)**

| Restaurant ID | Restaurant Name | Address | Phone | Status | Owner User ID |
|---------------|-----------------|---------|-------|--------|---------------|
| 101 | Joe's Pizza | 123 Main St, Miami, FL | 305-555-0101 | Active | johndoe |

#### **Table TC-001-02: Menu Items Table (Before Test Execution)**

| Menu Item ID | Restaurant ID | Item Name | Description | Price | Category | Available |
|--------------|---------------|-----------|-------------|-------|----------|-----------|
| 1001 | 101 | Margherita Pizza | Classic tomato and mozzarella | $12.99 | Entree | Yes |
| 1002 | 101 | Pepperoni Pizza | Pepperoni and cheese | $14.99 | Entree | Yes |
| 1003 | 101 | Caesar Salad | Fresh romaine with Caesar dressing | $8.99 | Appetizer | Yes |

**Test Setup:**
1. User "janedoe" is viewing "Joe's Pizza" menu (see TC-001-01 setup)
2. Restaurant "Joe's Pizza" menu has items in multiple categories (see Table TC-001-02: Menu Items)

**Test Input:**
1. User "janedoe" is viewing "Joe's Pizza" menu
2. User "janedoe" clicks on "Appetizers" filter button
3. System filters menu items
4. User "janedoe" clicks on "Entrees" filter button
5. System updates displayed items
6. User "janedoe" clears filter
7. System displays all items

**Expected Output:**
1. When "Appetizers" selected: Only Caesar Salad is displayed for restaurant "Joe's Pizza"
2. When "Entrees" selected: Only Margherita Pizza and Pepperoni Pizza are displayed for restaurant "Joe's Pizza"
3. When filter cleared: All 3 items are displayed for restaurant "Joe's Pizza"
4. Menu for restaurant "Joe's Pizza" updates dynamically without page reload (if applicable)
5. No items are lost or duplicated
6. Filter state is maintained correctly

---

## 🌧️ **UC-001: Browse Restaurant Menus - RAINY DAY SCENARIOS**

### **TC-001-03: Restaurant Not Found**

**Test Case ID:** SystemTest-013-UC001 (rainy day scenario)

**Purpose:** Verify that system handles search for non-existent restaurant gracefully.

#### **Table TC-001-03: Restaurants Table (Before Test Execution)**

| Restaurant ID | Restaurant Name | Address | Phone | Status | Owner User ID |
|---------------|-----------------|---------|-------|--------|---------------|
| (No restaurants exist) | | | | | |

**Test Setup:**
1. User "janedoe" is on MenuMap homepage
2. Restaurant "NonExistent" (ID: 999) does NOT exist in database (see Table TC-001-03)
3. Database is accessible

**Test Input:**
1. User "janedoe" navigates to MenuMap application
2. User "janedoe" enters restaurant name in search field: `NonExistent Restaurant`
3. User "janedoe" clicks "Search" button
4. System searches database

**Expected Output:**
1. System queries database for matching restaurants
2. System finds no matching results for "NonExistent Restaurant"
3. Message displays: "No restaurants found matching your search. Please try a different search term."
4. Search results page shows empty state with helpful message
5. User "janedoe" can try a new search
6. No error stack trace or technical details shown to user "janedoe"
7. System remains stable and responsive

---

### **TC-001-04: Menu Not Available (Empty Menu)**

**Test Case ID:** SystemTest-014-UC001 (rainy day scenario)

**Purpose:** Verify that system handles restaurant with no menu items gracefully.

#### **Table TC-001-04: Restaurants Table (Before Test Execution)**

| Restaurant ID | Restaurant Name | Address | Phone | Status | Owner User ID |
|---------------|-----------------|---------|-------|--------|---------------|
| 102 | Burger Palace | 456 Oak Ave, Miami, FL | 305-555-0102 | Active | janedoe |

#### **Table TC-001-04: Menu Items Table (Before Test Execution)**

| Menu Item ID | Restaurant ID | Item Name | Description | Price | Category | Available |
|--------------|---------------|-----------|-------------|-------|----------|-----------|
| (No menu items exist for restaurant 102) | | | | | | |

**Test Setup:**
1. Restaurant "Burger Palace" (ID: 102) exists in database (see Table TC-001-04: Restaurants)
2. Restaurant "Burger Palace" has NO menu items in database (see Table TC-001-04: Menu Items)
3. User "janedoe" is on MenuMap application

**Test Input:**
1. User "janedoe" searches for restaurant: `Burger Palace`
2. User "janedoe" finds restaurant "Burger Palace" in search results
3. User "janedoe" clicks "View Menu" button
4. System attempts to retrieve menu for restaurant "Burger Palace"

**Expected Output:**
1. System finds restaurant "Burger Palace" successfully
2. System queries for menu items for restaurant "Burger Palace"
3. System finds no menu items for restaurant "Burger Palace" (ID: 102)
4. Message displays: "This restaurant has not added menu items yet. Please check back later."
5. Restaurant "Burger Palace" information is displayed (name, address, etc.)
6. Menu section for restaurant "Burger Palace" shows empty state message
7. No error messages or crashes
8. User "janedoe" can navigate back or contact restaurant "Burger Palace"

---

### **TC-001-05: Database Connection Error**

**Test Case ID:** SystemTest-015-UC001 (rainy day scenario)

**Purpose:** Verify that system handles database unavailability when browsing menus.

#### **Table TC-001-05: Restaurants Table (Before Test Execution)**

| Restaurant ID | Restaurant Name | Address | Phone | Status | Owner User ID |
|---------------|-----------------|---------|-------|--------|---------------|
| 101 | Joe's Pizza | 123 Main St, Miami, FL | 305-555-0101 | Active | johndoe |

#### **Table TC-001-05: Menu Items Table (Before Test Execution)**

| Menu Item ID | Restaurant ID | Item Name | Description | Price | Category | Available |
|--------------|---------------|-----------|-------------|-------|----------|-----------|
| 1001 | 101 | Margherita Pizza | Classic tomato and mozzarella | $12.99 | Entree | Yes |
| 1002 | 101 | Pepperoni Pizza | Pepperoni and cheese | $14.99 | Entree | Yes |
| 1003 | 101 | Caesar Salad | Fresh romaine with Caesar dressing | $8.99 | Appetizer | Yes |

**Test Setup:**
1. User "janedoe" is on MenuMap application
2. Database server is down or unreachable
3. Restaurant "Joe's Pizza" exists in database (see Table TC-001-05: Restaurants)

**Test Input:**
1. User "janedoe" searches for restaurant: `Joe's Pizza`
2. User "janedoe" selects restaurant "Joe's Pizza" from results
3. User "janedoe" clicks "View Menu" button
4. System attempts database connection

**Expected Output:**
1. System attempts to connect to database
2. Database connection fails
3. User-friendly error message displays: "We're having trouble loading the menu. Please try again in a moment."
4. Error is logged for administrators with technical details
5. User "janedoe" can retry the operation for restaurant "Joe's Pizza"
6. System does not crash or show technical error details
7. User "janedoe" can navigate to other parts of application

---

### **TC-001-06: Invalid Search Input (SQL Injection)**

**Test Case ID:** SystemTest-016-UC001 (rainy day scenario)

**Purpose:** Verify that system prevents SQL injection attacks in search field.

#### **Table TC-001-06: Restaurants Table (Before Test Execution)**

| Restaurant ID | Restaurant Name | Address | Phone | Status | Owner User ID |
|---------------|-----------------|---------|-------|--------|---------------|
| (Not applicable - security test) | | | | | |

**Test Setup:**
1. User "janedoe" is on MenuMap homepage
2. Database is accessible

**Test Input:**
1. User "janedoe" navigates to MenuMap application
2. User "janedoe" enters malicious input in search field: `'; DROP TABLE restaurants; --`
3. User "janedoe" clicks "Search" button
4. System processes input

**Expected Output:**
1. Input is sanitized/validated
2. SQL injection is prevented
3. System treats as invalid or empty search
4. Message displays: "Please enter a valid search term" or "No restaurants found"
5. No SQL commands are executed
6. Database tables remain intact
7. No security vulnerabilities exploited

---

### **TC-001-07: Timeout During Menu Load**

**Test Case ID:** SystemTest-017-UC001 (rainy day scenario)

**Purpose:** Verify that system handles timeout when menu loading takes too long.

#### **Table TC-001-07: Restaurants Table (Before Test Execution)**

| Restaurant ID | Restaurant Name | Address | Phone | Status | Owner User ID |
|---------------|-----------------|---------|-------|--------|---------------|
| 101 | Joe's Pizza | 123 Main St, Miami, FL | 305-555-0101 | Active | johndoe |

#### **Table TC-001-07: Menu Items Table (Before Test Execution)**

| Menu Item ID | Restaurant ID | Item Name | Description | Price | Category | Available |
|--------------|---------------|-----------|-------------|-------|----------|-----------|
| 1001 | 101 | Margherita Pizza | Classic tomato and mozzarella | $12.99 | Entree | Yes |
| 1002 | 101 | Pepperoni Pizza | Pepperoni and cheese | $14.99 | Entree | Yes |
| 1003 | 101 | Caesar Salad | Fresh romaine with Caesar dressing | $8.99 | Appetizer | Yes |

**Test Setup:**
1. Restaurant "Joe's Pizza" exists in database (see Table TC-001-07: Restaurants)
2. Database is slow or under heavy load
3. Network connection is slow
4. System timeout threshold: 30 seconds

**Test Input:**
1. User "janedoe" searches for restaurant: `Joe's Pizza`
2. User "janedoe" selects restaurant "Joe's Pizza"
3. User "janedoe" clicks "View Menu" button
4. System attempts to load menu for restaurant "Joe's Pizza"
5. Request exceeds timeout threshold

**Expected Output:**
1. System attempts to load menu for restaurant "Joe's Pizza"
2. Request exceeds 30-second timeout
3. Timeout message displays: "The request took too long. Please try again."
4. User "janedoe" can retry the operation for restaurant "Joe's Pizza"
5. System cancels the request
6. No partial data is displayed
7. System remains responsive

---

### **TC-001-08: Restaurant Inactive/Closed**

**Test Case ID:** SystemTest-018-UC001 (rainy day scenario)

**Purpose:** Verify that system handles viewing menu for inactive/closed restaurant.

#### **Table TC-001-08: Restaurants Table (Before Test Execution)**

| Restaurant ID | Restaurant Name | Address | Phone | Status | Owner User ID |
|---------------|-----------------|---------|-------|--------|---------------|
| 103 | Closed Restaurant | 789 Pine Rd, Miami, FL | 305-555-0103 | Inactive | lockeduser |

#### **Table TC-001-08: Menu Items Table (Before Test Execution)**

| Menu Item ID | Restaurant ID | Item Name | Description | Price | Category | Available |
|--------------|---------------|-----------|-------------|-------|----------|-----------|
| 1006 | 103 | Old Menu Item | Item from closed restaurant | $5.99 | Entree | No |

**Test Setup:**
1. Restaurant "Closed Restaurant" (ID: 103) exists in database (see Table TC-001-08: Restaurants)
2. Restaurant "Closed Restaurant" status is "Inactive"
3. Restaurant "Closed Restaurant" may have menu items (see Table TC-001-08: Menu Items)

**Test Input:**
1. User "janedoe" searches for restaurant: `Closed Restaurant`
2. User "janedoe" finds restaurant "Closed Restaurant" in results (if inactive restaurants are shown)
3. User "janedoe" clicks "View Menu" button
4. System processes request for restaurant "Closed Restaurant"

**Expected Output:**
1. System checks restaurant "Closed Restaurant" status
2. System detects restaurant "Closed Restaurant" is inactive
3. Message displays: "This restaurant is currently closed or inactive. Menu is not available."
4. Restaurant "Closed Restaurant" information may be shown with inactive status
5. Menu for restaurant "Closed Restaurant" is not displayed (or shown as unavailable)
6. User "janedoe" can search for other restaurants
7. No error messages or crashes

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
- **Each test case includes its own database state table(s)**

---

## ✅ **Test Execution Checklist**

### **Before Testing:**
- [ ] Test environment is set up
- [ ] Database is accessible
- [ ] Test data is prepared (see individual test case tables)
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
2. **Database Tables:** Each test case includes its own database state table(s) before the Test Setup section
3. **Documentation:** Include this test case document in your Final Document
4. **Implementation Evidence:** Reference code snippets that handle each scenario
5. **No Papyrus Required:** Test cases are written documentation, not diagrams

---

**This document provides comprehensive test coverage for UC-005 (Login) and UC-001 (Browse Restaurant Menus) with both successful and error scenarios, following CEN4010 Software Engineering standards.**

