# MenuMap Deliverable 3 - Test Cases
## CEN4010 Software Engineering - Team 9

**Project:** MenuMap Application  
**Deliverable:** 3 - Implementation  
**Group Lead:** Andre Lewis  
**Date:** [Current Date]  
**Version:** 1.0  

---

## 📋 Test Case Overview

This document contains comprehensive test cases for Deliverable 3 implementation, including both **Sunny Day** (happy path) and **Rainy Day** (error/edge case) scenarios.

### **Test Cases Covered:**
1. **UC-004: User Login** - Authentication and session management
2. **UC-001: Browse Restaurant Menus** - Menu discovery and browsing

---

## 🔐 UC-004: User Login - Test Cases

### **Test Case TC-LOGIN-001: Sunny Day - Successful Login with Valid Credentials**

**Test Case ID:** TC-LOGIN-001  
**Use Case:** UC-004: User Login  
**Test Type:** Sunny Day (Happy Path)  
**Priority:** High  
**Status:** ⏳ Pending

#### **Preconditions:**
- User account exists in the system
- User has registered with valid email and password
- User is not currently logged in
- Database is accessible and running
- Backend API is running and accessible

#### **Test Steps:**
1. Navigate to the login page
2. Enter valid email address: `testuser@example.com`
3. Enter valid password: `SecurePass123!`
4. Click the "Login" button
5. Wait for API response

#### **Expected Results:**
- Login form displays correctly
- Email field accepts input
- Password field accepts input (masked)
- Login button is enabled
- API request is sent to `/api/auth/login`
- Response status: `200 OK`
- Response contains JWT token in `Authorization` header
- User is redirected to dashboard/home page
- User session is created
- User authentication state is stored (localStorage/sessionStorage)
- Success message displayed: "Login successful" or similar
- User profile information is loaded

#### **Postconditions:**
- User is authenticated
- JWT token is stored
- User session is active
- User can access protected routes

#### **Test Data:**
- Email: `testuser@example.com`
- Password: `SecurePass123!`

---

### **Test Case TC-LOGIN-002: Rainy Day - Login with Invalid Email**

**Test Case ID:** TC-LOGIN-002  
**Use Case:** UC-004: User Login  
**Test Type:** Rainy Day (Error Case)  
**Priority:** High  
**Status:** ⏳ Pending

#### **Preconditions:**
- User is not logged in
- Backend API is running
- Database is accessible

#### **Test Steps:**
1. Navigate to the login page
2. Enter invalid email address: `invalid-email`
3. Enter password: `SecurePass123!`
4. Click the "Login" button

#### **Expected Results:**
- Email validation error displayed: "Please enter a valid email address"
- Login button may be disabled (if client-side validation)
- No API request is sent (if client-side validation)
- OR if API request is sent:
  - Response status: `400 Bad Request`
  - Error message: "Invalid email format"
- User remains on login page
- No session is created
- No JWT token is issued

#### **Postconditions:**
- User is not authenticated
- User remains on login page
- Error message is visible

#### **Test Data:**
- Email: `invalid-email`
- Password: `SecurePass123!`

---

### **Test Case TC-LOGIN-003: Rainy Day - Login with Incorrect Password**

**Test Case ID:** TC-LOGIN-003  
**Use Case:** UC-004: User Login  
**Test Type:** Rainy Day (Error Case)  
**Priority:** High  
**Status:** ⏳ Pending

#### **Preconditions:**
- User account exists: `testuser@example.com`
- User is not logged in
- Backend API is running
- Database is accessible

#### **Test Steps:**
1. Navigate to the login page
2. Enter valid email address: `testuser@example.com`
3. Enter incorrect password: `WrongPassword123!`
4. Click the "Login" button
5. Wait for API response

#### **Expected Results:**
- API request is sent to `/api/auth/login`
- Response status: `401 Unauthorized`
- Error message displayed: "Invalid email or password" (generic message for security)
- User remains on login page
- No JWT token is issued
- No session is created
- Login attempt is logged (for security monitoring)
- Password field is cleared (optional, for security)

#### **Postconditions:**
- User is not authenticated
- User remains on login page
- Error message is visible
- Failed login attempt is recorded

#### **Test Data:**
- Email: `testuser@example.com`
- Password: `WrongPassword123!`

---

### **Test Case TC-LOGIN-004: Rainy Day - Login with Non-Existent User**

**Test Case ID:** TC-LOGIN-004  
**Use Case:** UC-004: User Login  
**Test Type:** Rainy Day (Error Case)  
**Priority:** High  
**Status:** ⏳ Pending

#### **Preconditions:**
- User account does NOT exist in the system
- User is not logged in
- Backend API is running
- Database is accessible

#### **Test Steps:**
1. Navigate to the login page
2. Enter non-existent email: `nonexistent@example.com`
3. Enter password: `SomePassword123!`
4. Click the "Login" button
5. Wait for API response

#### **Expected Results:**
- API request is sent to `/api/auth/login`
- Response status: `401 Unauthorized`
- Error message displayed: "Invalid email or password" (generic message)
- User remains on login page
- No JWT token is issued
- No session is created
- Login attempt is logged
- No indication that user doesn't exist (security best practice)

#### **Postconditions:**
- User is not authenticated
- User remains on login page
- Error message is visible

#### **Test Data:**
- Email: `nonexistent@example.com`
- Password: `SomePassword123!`

---

### **Test Case TC-LOGIN-005: Rainy Day - Login with Empty Fields**

**Test Case ID:** TC-LOGIN-005  
**Use Case:** UC-004: User Login  
**Test Type:** Rainy Day (Error Case)  
**Priority:** Medium  
**Status:** ⏳ Pending

#### **Preconditions:**
- User is not logged in
- Login page is accessible

#### **Test Steps:**
1. Navigate to the login page
2. Leave email field empty
3. Leave password field empty
4. Click the "Login" button

#### **Expected Results:**
- Client-side validation prevents submission
- Email field shows error: "Email is required"
- Password field shows error: "Password is required"
- Login button may be disabled
- No API request is sent
- User remains on login page

#### **Postconditions:**
- User is not authenticated
- Validation errors are visible
- User remains on login page

---

### **Test Case TC-LOGIN-006: Rainy Day - Login with SQL Injection Attempt**

**Test Case ID:** TC-LOGIN-006  
**Use Case:** UC-004: User Login  
**Test Type:** Rainy Day (Security Test)  
**Priority:** High  
**Status:** ⏳ Pending

#### **Preconditions:**
- User is not logged in
- Backend API is running
- Security measures are in place

#### **Test Steps:**
1. Navigate to the login page
2. Enter SQL injection attempt in email: `admin' OR '1'='1`
3. Enter password: `anything`
4. Click the "Login" button

#### **Expected Results:**
- Input is sanitized/validated
- API request is sent with sanitized input
- Response status: `401 Unauthorized` or `400 Bad Request`
- No SQL injection occurs
- Database remains secure
- Security event is logged
- Error message displayed (generic)

#### **Postconditions:**
- User is not authenticated
- Security threat is blocked
- Attempt is logged for security monitoring

#### **Test Data:**
- Email: `admin' OR '1'='1`
- Password: `anything`

---

### **Test Case TC-LOGIN-007: Rainy Day - Multiple Failed Login Attempts (Rate Limiting)**

**Test Case ID:** TC-LOGIN-007  
**Use Case:** UC-004: User Login  
**Test Type:** Rainy Day (Security Test)  
**Priority:** High  
**Status:** ⏳ Pending

#### **Preconditions:**
- User is not logged in
- Backend API is running
- Rate limiting is configured (e.g., 5 attempts per 15 minutes)

#### **Test Steps:**
1. Navigate to the login page
2. Enter valid email: `testuser@example.com`
3. Enter incorrect password: `WrongPass1`
4. Click "Login" (Attempt 1)
5. Repeat steps 2-4 with different wrong passwords (Attempts 2-5)
6. On attempt 6, try to login again

#### **Expected Results:**
- Attempts 1-5: Each returns `401 Unauthorized`
- Attempt 6: Response status: `429 Too Many Requests`
- Error message: "Too many login attempts. Please try again in X minutes"
- Account may be temporarily locked
- Rate limiting is enforced
- Security event is logged
- User must wait before attempting again

#### **Postconditions:**
- User is not authenticated
- Account is rate-limited
- User must wait before retrying

---

## 🍽️ UC-001: Browse Restaurant Menus - Test Cases

### **Test Case TC-BROWSE-001: Sunny Day - Successful Menu Browse with Filters**

**Test Case ID:** TC-BROWSE-001  
**Use Case:** UC-001: Browse Restaurant Menus  
**Test Type:** Sunny Day (Happy Path)  
**Priority:** High  
**Status:** ⏳ Pending

#### **Preconditions:**
- User is logged in (optional, some features may require authentication)
- Database contains restaurant and menu data
- Backend API is running
- Frontend is accessible

#### **Test Steps:**
1. Navigate to the restaurant browse page
2. Enter search query: "Italian"
3. Select location filter: "Miami, FL"
4. Select cuisine type filter: "Italian"
5. Set price range: "$10-$30"
6. Click "Search" button
7. Wait for results to load

#### **Expected Results:**
- Search page loads correctly
- Search bar is visible and functional
- Filter options are available
- API request sent to `/api/restaurants?search=Italian&location=Miami&cuisine=Italian&priceMin=10&priceMax=30`
- Response status: `200 OK`
- Results are displayed in list/grid view
- Each result shows:
  - Restaurant name
  - Restaurant image/thumbnail
  - Cuisine type
  - Average price range
  - Rating (if available)
  - Location/address
- Results are relevant to search criteria
- Results load within 3 seconds (performance requirement)
- Pagination is available if results exceed page limit

#### **Postconditions:**
- Search results are displayed
- User can view restaurant details
- User can click on restaurants to view menus

#### **Test Data:**
- Search: "Italian"
- Location: "Miami, FL"
- Cuisine: "Italian"
- Price Range: $10-$30

---

### **Test Case TC-BROWSE-002: Sunny Day - View Restaurant Menu Details**

**Test Case ID:** TC-BROWSE-002  
**Use Case:** UC-001: Browse Restaurant Menus  
**Test Type:** Sunny Day (Happy Path)  
**Priority:** High  
**Status:** ⏳ Pending

#### **Preconditions:**
- User is on the restaurant browse page
- Restaurant with ID 123 exists in database
- Restaurant has menu items

#### **Test Steps:**
1. Click on a restaurant from the search results (Restaurant ID: 123)
2. Wait for restaurant detail page to load
3. View menu items displayed
4. Click on a menu item to view details

#### **Expected Results:**
- Restaurant detail page loads
- API request sent to `/api/restaurants/123`
- Response status: `200 OK`
- Restaurant information displayed:
  - Restaurant name
  - Address
  - Phone number
  - Hours of operation
  - Rating
  - Images
- Menu items are displayed:
  - Menu item name
  - Description
  - Price
  - Category (Appetizer, Main Course, Dessert, etc.)
  - Image (if available)
- Menu items are organized by category
- Clicking menu item shows detailed modal/page:
  - Full description
  - Nutritional information (if available)
  - Allergen information (if available)
  - Price
  - Image
- Page loads within 3 seconds

#### **Postconditions:**
- Restaurant details are displayed
- Menu items are visible
- User can interact with menu items

#### **Test Data:**
- Restaurant ID: 123

---

### **Test Case TC-BROWSE-003: Rainy Day - Search with No Results**

**Test Case ID:** TC-BROWSE-003  
**Use Case:** UC-001: Browse Restaurant Menus  
**Test Type:** Rainy Day (Error Case)  
**Priority:** Medium  
**Status:** ⏳ Pending

#### **Preconditions:**
- User is on the browse page
- Database contains restaurant data
- Backend API is running

#### **Test Steps:**
1. Enter search query: "NonExistentRestaurantXYZ123"
2. Click "Search" button
3. Wait for results

#### **Expected Results:**
- API request sent to `/api/restaurants?search=NonExistentRestaurantXYZ123`
- Response status: `200 OK`
- Response contains empty results array: `[]`
- Empty state message displayed: "No restaurants found matching your search"
- Suggestions displayed (optional):
  - "Try different keywords"
  - "Clear filters"
  - "Browse all restaurants"
- No error message (empty results is valid)
- User can modify search and try again

#### **Postconditions:**
- Empty state is displayed
- User can modify search criteria
- No errors occurred

#### **Test Data:**
- Search: "NonExistentRestaurantXYZ123"

---

### **Test Case TC-BROWSE-004: Rainy Day - Invalid Search Parameters**

**Test Case ID:** TC-BROWSE-004  
**Use Case:** UC-001: Browse Restaurant Menus  
**Test Type:** Rainy Day (Error Case)  
**Priority:** Medium  
**Status:** ⏳ Pending

#### **Preconditions:**
- User is on the browse page
- Backend API is running

#### **Test Steps:**
1. Enter invalid price range: Min = $50, Max = $10 (min > max)
2. Click "Search" button

#### **Expected Results:**
- Client-side validation prevents invalid submission
- Error message: "Minimum price cannot be greater than maximum price"
- OR if sent to API:
  - Response status: `400 Bad Request`
  - Error message: "Invalid price range parameters"
- No API request sent (if client-side validation)
- User can correct the input

#### **Postconditions:**
- Validation error is displayed
- User can correct input
- No invalid request sent to server

---

### **Test Case TC-BROWSE-005: Rainy Day - API Timeout/Server Error**

**Test Case ID:** TC-BROWSE-005  
**Use Case:** UC-001: Browse Restaurant Menus  
**Test Type:** Rainy Day (Error Case)  
**Priority:** High  
**Status:** ⏳ Pending

#### **Preconditions:**
- User is on the browse page
- Backend API is down or unreachable

#### **Test Steps:**
1. Enter search query: "Italian"
2. Click "Search" button
3. Wait for timeout or error

#### **Expected Results:**
- API request times out or returns error
- Response status: `500 Internal Server Error` or `503 Service Unavailable` or timeout
- Error message displayed: "Unable to load restaurants. Please try again later."
- Retry button is available (optional)
- User-friendly error message (no technical details exposed)
- Error is logged on backend
- User can try again later

#### **Postconditions:**
- Error message is displayed
- User is informed of the issue
- System remains stable

---

### **Test Case TC-BROWSE-006: Rainy Day - View Menu for Restaurant with No Menu Items**

**Test Case ID:** TC-BROWSE-006  
**Use Case:** UC-001: Browse Restaurant Menus  
**Test Type:** Rainy Day (Edge Case)  
**Priority:** Low  
**Status:** ⏳ Pending

#### **Preconditions:**
- Restaurant exists in database (ID: 456)
- Restaurant has no menu items
- User navigates to restaurant detail page

#### **Test Steps:**
1. Navigate to restaurant detail page (ID: 456)
2. View menu section

#### **Expected Results:**
- Restaurant detail page loads
- API request sent to `/api/restaurants/456/menu`
- Response status: `200 OK`
- Response contains empty menu array: `[]`
- Empty state message: "No menu items available for this restaurant"
- Restaurant information is still displayed
- User can still view restaurant details

#### **Postconditions:**
- Restaurant details are displayed
- Empty menu state is shown
- User experience is not broken

#### **Test Data:**
- Restaurant ID: 456 (with no menu items)

---

### **Test Case TC-BROWSE-007: Sunny Day - Browse with Special Characters in Search**

**Test Case ID:** TC-BROWSE-007  
**Use Case:** UC-001: Browse Restaurant Menus  
**Test Type:** Sunny Day (Edge Case)  
**Priority:** Medium  
**Status:** ⏳ Pending

#### **Preconditions:**
- User is on the browse page
- Database contains restaurants with special characters in names

#### **Test Steps:**
1. Enter search query: "Café & Restaurant"
2. Click "Search" button

#### **Expected Results:**
- Special characters are properly encoded in API request
- API request sent to `/api/restaurants?search=Café%20%26%20Restaurant`
- Response status: `200 OK`
- Results include restaurants matching the search
- Special characters are displayed correctly
- No encoding errors occur
- Search works correctly with special characters

#### **Postconditions:**
- Search results are displayed correctly
- Special characters are handled properly

#### **Test Data:**
- Search: "Café & Restaurant"

---

## 📊 Test Case Summary

| Test Case ID | Use Case | Type | Priority | Status |
|--------------|----------|------|----------|--------|
| TC-LOGIN-001 | UC-004: User Login | Sunny Day | High | ⏳ Pending |
| TC-LOGIN-002 | UC-004: User Login | Rainy Day | High | ⏳ Pending |
| TC-LOGIN-003 | UC-004: User Login | Rainy Day | High | ⏳ Pending |
| TC-LOGIN-004 | UC-004: User Login | Rainy Day | High | ⏳ Pending |
| TC-LOGIN-005 | UC-004: User Login | Rainy Day | Medium | ⏳ Pending |
| TC-LOGIN-006 | UC-004: User Login | Rainy Day (Security) | High | ⏳ Pending |
| TC-LOGIN-007 | UC-004: User Login | Rainy Day (Security) | High | ⏳ Pending |
| TC-BROWSE-001 | UC-001: Browse Menus | Sunny Day | High | ⏳ Pending |
| TC-BROWSE-002 | UC-001: Browse Menus | Sunny Day | High | ⏳ Pending |
| TC-BROWSE-003 | UC-001: Browse Menus | Rainy Day | Medium | ⏳ Pending |
| TC-BROWSE-004 | UC-001: Browse Menus | Rainy Day | Medium | ⏳ Pending |
| TC-BROWSE-005 | UC-001: Browse Menus | Rainy Day | High | ⏳ Pending |
| TC-BROWSE-006 | UC-001: Browse Menus | Rainy Day | Low | ⏳ Pending |
| TC-BROWSE-007 | UC-001: Browse Menus | Sunny Day | Medium | ⏳ Pending |

**Total Test Cases:** 14  
**Sunny Day:** 4  
**Rainy Day:** 10

---

## ✅ Test Execution Checklist

### **Before Testing:**
- [ ] Test environment is set up
- [ ] Database is populated with test data
- [ ] Backend API is running
- [ ] Frontend application is running
- [ ] Test accounts are created
- [ ] Test data is prepared

### **During Testing:**
- [ ] Execute each test case step by step
- [ ] Record actual results
- [ ] Take screenshots for evidence
- [ ] Log any defects found
- [ ] Note any deviations from expected results

### **After Testing:**
- [ ] Update test case status (Pass/Fail/Blocked)
- [ ] Document defects in issue tracker
- [ ] Create test execution report
- [ ] Share results with team

---

## 📝 Notes

- **Test Data:** Ensure test data is consistent and available before executing tests
- **Environment:** Tests should be run in a dedicated test environment
- **Documentation:** All test results should be documented for Deliverable 3 Chapter 8
- **Defects:** Any defects found should be logged and tracked

---

*This test case document supports Deliverable 3 Chapter 8: Testing & Quality Assurance*

