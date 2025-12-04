# MenuMap User's Guide
## Team 9 - CEN 4010 Software Engineering
## Fall 2024

---

## 📖 Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [User Roles](#user-roles)
4. [Features and Functionality](#features-and-functionality)
5. [Step-by-Step Guides](#step-by-step-guides)
6. [Troubleshooting](#troubleshooting)

---

## Introduction

### What is MenuMap?

MenuMap is a comprehensive restaurant menu management and browsing system that allows users to discover, view, and manage restaurant menus. The system supports multiple user roles including customers, restaurant owners, and administrators.

### System Overview

MenuMap provides the following key features:
- **Menu Browsing**: Search and view restaurant menus
- **Menu Management**: Restaurant owners can create and manage their menus
- **User Accounts**: Secure user registration and authentication
- **Favorites**: Save favorite restaurants and menu items
- **Menu Verification**: Administrators can verify menu accuracy

---

## Getting Started

### Creating an Account

1. Navigate to the MenuMap homepage
2. Click on "Register" or "Sign Up"
3. Fill in the registration form:
   - Email address
   - Password (must meet complexity requirements)
   - Confirm password
   - First name
   - Last name
4. Click "Create Account"
5. Check your email for verification link
6. Click the verification link to activate your account

### Logging In

1. Navigate to the MenuMap homepage
2. Click "Login"
3. Enter your email and password
4. Click "Sign In"
5. You will be redirected to your dashboard

### Password Requirements

Your password must:
- Be at least 8 characters long
- Contain at least one uppercase letter
- Contain at least one lowercase letter
- Contain at least one number
- Contain at least one special character (!@#$%^&*)

---

## User Roles

### Customer

**Capabilities:**
- Browse restaurant menus
- Search for restaurants
- View menu items with prices and descriptions
- Filter menu items by category
- Save favorite restaurants
- Manage user profile

**Limitations:**
- Cannot create or edit menus
- Cannot verify menu content

### Restaurant Owner

**Capabilities:**
- All customer capabilities, plus:
- Create and manage restaurant information
- Add, edit, and delete menu items
- Update menu prices and descriptions
- Manage restaurant status (active/inactive)

**Limitations:**
- Can only manage their own restaurant
- Cannot verify menus (admin function)

### Administrator

**Capabilities:**
- All customer capabilities, plus:
- Verify menu accuracy
- Review and approve menu changes
- Manage system settings
- View system reports

---

## Features and Functionality

### 1. Browse Restaurant Menus (UC-001)

**Purpose:** Search for and view restaurant menus

**Steps:**
1. From the homepage, use the search bar
2. Enter restaurant name (e.g., "Joe's Pizza")
3. Click "Search" or press Enter
4. Select a restaurant from the results
5. View the complete menu with items, descriptions, and prices

**Filtering Options:**
- Filter by category (Appetizers, Entrees, Desserts, etc.)
- Sort by price (low to high, high to low)
- Sort alphabetically

### 2. User Registration (UC-004)

**Purpose:** Create a new user account

**Steps:**
1. Click "Register" on the homepage
2. Fill in all required fields:
   - Email (must be valid email format)
   - Password (must meet requirements)
   - Confirm password (must match)
   - First name
   - Last name
3. Review and accept terms of service
4. Click "Create Account"
5. Check email for verification link
6. Click verification link to activate account

**Common Issues:**
- Email already exists: Use a different email or try logging in
- Weak password: Ensure password meets all requirements
- Email not received: Check spam folder, request new verification email

### 3. User Login (UC-005)

**Purpose:** Access your account

**Steps:**
1. Click "Login" on the homepage
2. Enter your email or user ID
3. Enter your password
4. Click "Sign In"

**Login Options:**
- Login with email address
- Login with user ID
- "Remember Me" option (saves login for 30 days)

**Troubleshooting:**
- Forgot password: Click "Forgot Password" to reset
- Account locked: Contact support after multiple failed attempts
- Email not verified: Check email for verification link

### 4. Secure Password Reset (UC-003)

**Purpose:** Reset forgotten password securely

**Steps:**
1. Click "Forgot Password" on login page
2. Enter your registered email address
3. Click "Send Reset Link"
4. Check your email for reset link
5. Click the reset link (valid for 24 hours)
6. Enter new password (must meet requirements)
7. Confirm new password
8. Click "Reset Password"
9. Login with new password

**Security Features:**
- Reset links expire after 24 hours
- Reset links can only be used once
- Secure token generation
- Email verification required

### 5. Restaurant Owner Menu Management (UC-007)

**Purpose:** Create and manage restaurant menus

**Steps to Add Menu Item:**
1. Login as restaurant owner
2. Navigate to "My Restaurant" or "Menu Management"
3. Click "Add Menu Item"
4. Fill in item details:
   - Item name
   - Description
   - Price
   - Category
   - Availability status
5. Click "Save"

**Steps to Edit Menu Item:**
1. Navigate to menu management
2. Find the item to edit
3. Click "Edit" button
4. Modify item details
5. Click "Save Changes"

**Steps to Delete Menu Item:**
1. Navigate to menu management
2. Find the item to delete
3. Click "Delete" button
4. Confirm deletion

### 6. Manage Favorites (UC-002)

**Purpose:** Save and manage favorite restaurants

**Steps to Add Favorite:**
1. Browse to a restaurant menu
2. Click the "Heart" or "Favorite" icon
3. Restaurant is saved to your favorites

**Steps to View Favorites:**
1. Click "My Favorites" in navigation menu
2. View list of saved restaurants
3. Click on any restaurant to view menu

**Steps to Remove Favorite:**
1. Go to "My Favorites"
2. Find restaurant to remove
3. Click "Remove" or unfavorite icon

---

## Step-by-Step Guides

### Complete Workflow: Finding and Viewing a Menu

1. **Access MenuMap**
   - Open web browser
   - Navigate to MenuMap URL
   - Homepage loads

2. **Search for Restaurant**
   - Enter restaurant name in search bar
   - Click "Search"
   - View search results

3. **Select Restaurant**
   - Click on desired restaurant
   - Restaurant page loads

4. **Browse Menu**
   - View all menu items
   - Use category filters if needed
   - Read item descriptions and prices

5. **Optional Actions**
   - Add restaurant to favorites
   - Share menu with others
   - View restaurant information

### Complete Workflow: Restaurant Owner Managing Menu

1. **Login as Owner**
   - Login with restaurant owner credentials
   - Navigate to dashboard

2. **Access Menu Management**
   - Click "Menu Management" or "My Restaurant"
   - View current menu items

3. **Add New Item**
   - Click "Add Menu Item"
   - Fill in item details
   - Save item

4. **Update Existing Item**
   - Find item to update
   - Click "Edit"
   - Modify details
   - Save changes

5. **Verify Changes**
   - View updated menu
   - Confirm changes are displayed correctly

---

## Troubleshooting

### Common Issues and Solutions

#### Issue: Cannot Login

**Possible Causes:**
- Incorrect email or password
- Account not verified
- Account locked

**Solutions:**
- Verify email and password are correct
- Check email for verification link
- Use "Forgot Password" to reset
- Contact support if account is locked

#### Issue: Menu Not Displaying

**Possible Causes:**
- Restaurant has no menu items
- Restaurant is inactive
- Database connection issue

**Solutions:**
- Check if restaurant has menu items
- Verify restaurant status
- Refresh page
- Contact support if issue persists

#### Issue: Cannot Add Menu Item

**Possible Causes:**
- Not logged in as restaurant owner
- Missing required fields
- Invalid data format

**Solutions:**
- Verify you are logged in as restaurant owner
- Check all required fields are filled
- Verify price is a valid number
- Check category is selected

#### Issue: Password Reset Link Not Working

**Possible Causes:**
- Link expired (24 hours)
- Link already used
- Invalid token

**Solutions:**
- Request new password reset
- Check email for most recent reset link
- Ensure link is clicked within 24 hours

#### Issue: Search Not Finding Restaurant

**Possible Causes:**
- Restaurant name misspelled
- Restaurant is inactive
- Restaurant not in database

**Solutions:**
- Try different search terms
- Check spelling
- Browse all restaurants
- Contact support if restaurant should exist

---

## Best Practices

### For Customers

- Keep your account information up to date
- Use strong, unique passwords
- Verify your email address
- Report any menu inaccuracies
- Use favorites to save frequently visited restaurants

### For Restaurant Owners

- Keep menu information current
- Use clear, descriptive item names
- Include accurate prices
- Update availability status regularly
- Respond to menu verification requests

### For Administrators

- Regularly verify menu accuracy
- Review reported issues promptly
- Maintain system security
- Monitor system performance

---

## Support and Contact

### Getting Help

- **Email Support:** [Support Email]
- **Documentation:** See Final Document for technical details
- **FAQ:** Check README.md for common questions

### Reporting Issues

When reporting issues, please include:
- Your user role (Customer/Owner/Admin)
- Steps to reproduce the issue
- Expected behavior
- Actual behavior
- Screenshots (if applicable)

---

## Appendix: Keyboard Shortcuts

- **Ctrl + F**: Search on page
- **Esc**: Close modal dialogs
- **Enter**: Submit forms
- **Tab**: Navigate between form fields

---

**User's Guide Version:** 1.0  
**Last Updated:** December 2024  
**Team 9 - CEN 4010 Software Engineering**

*For technical documentation, please refer to the Final Document.*

