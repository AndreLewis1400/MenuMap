# MenuMap Use Case Scenarios
## CEN4010 Software Engineering - Team 9

**Project:** MenuMap Application  
**Team:** Team 9  
**Project Lead:** Alfonso Oramas Jr.  
**Document Author:** Andre Lewis (UML Diagrams Coordinator)  
**Date:** [Current Date]  
**Version:** 1.0  

---

## 📋 Scenarios Overview

This document contains detailed scenarios for each of the three use cases in the MenuMap application. Each scenario demonstrates a specific user journey through the system.

---

## 🍽️ UC-001: Browse Restaurant Menus - Scenarios

### **Scenario 1: User Searches for Italian Restaurants**

**Actor:** Sarah (Food enthusiast)  
**Goal:** Find Italian restaurants near her location  
**Context:** Sarah is looking for a nice Italian restaurant for dinner tonight  

**Steps:**
1. Sarah opens the MenuMap application on her phone
2. She sees the main search interface with a search bar
3. Sarah types "Italian" in the search bar
4. System displays 15 Italian restaurants within 5 miles
5. Sarah sees "Mario's Italian Bistro" with 4.5 stars
6. She taps on the restaurant name
7. System displays Mario's complete menu with categories
8. Sarah browses the "Pasta" section
9. She sees "Spaghetti Carbonara - $18.99" with description
10. Sarah reads the ingredients and decides to visit the restaurant

**Expected Result:** Sarah successfully finds an Italian restaurant with a menu that meets her preferences

---

### **Scenario 2: User Browses Menu by Cuisine Type**

**Actor:** Mike (College student)  
**Goal:** Find affordable Mexican food  
**Context:** Mike is on a budget and wants Mexican food for lunch  

**Steps:**
1. Mike opens MenuMap on his laptop
2. He clicks on the "Cuisine" filter button
3. System shows cuisine categories (Italian, Mexican, Chinese, etc.)
4. Mike selects "Mexican" from the list
5. System displays 8 Mexican restaurants in the area
6. Mike sorts by "Price: Low to High"
7. He sees "Taco Bell" and "Local Taqueria" at the top
8. Mike clicks on "Local Taqueria"
9. System shows the menu with prices
10. Mike sees "Bean Burrito - $6.99" and decides to go there

**Expected Result:** Mike finds an affordable Mexican restaurant that fits his budget

---

### **Scenario 3: User Searches for Specific Menu Item**

**Actor:** Lisa (Vegetarian)  
**Goal:** Find restaurants that serve vegetarian burgers  
**Context:** Lisa is looking for a vegetarian burger for lunch  

**Steps:**
1. Lisa opens MenuMap
2. She types "vegetarian burger" in the search bar
3. System searches through all menu items
4. System displays 5 restaurants that serve vegetarian burgers
5. Lisa sees "Green Garden Cafe" with "Veggie Deluxe Burger - $12.99"
6. She taps on the restaurant
7. System shows the full menu with vegetarian options highlighted
8. Lisa reads the burger description: "Black bean patty with avocado and sprouts"
9. She checks the restaurant's location and hours
10. Lisa decides to visit Green Garden Cafe

**Expected Result:** Lisa finds a restaurant that serves the specific vegetarian burger she wants

---

## ⭐ UC-002: Manage Favorites - Scenarios

### **Scenario 1: User Adds Restaurant to Favorites**

**Actor:** David (Regular customer)  
**Goal:** Save his favorite pizza place for quick access  
**Context:** David frequently orders from the same pizza restaurant  

**Steps:**
1. David opens MenuMap and logs into his account
2. He searches for "Tony's Pizza" (his favorite place)
3. System displays Tony's Pizza with menu and details
4. David sees a "❤️ Add to Favorites" button
5. He taps the heart button
6. System shows "Added to Favorites!" confirmation message
7. David navigates to "My Favorites" section
8. He sees Tony's Pizza listed under "Restaurants"
9. David can now quickly access Tony's Pizza anytime
10. He taps on Tony's Pizza and sees the full menu instantly

**Expected Result:** David successfully saves Tony's Pizza to his favorites for quick access

---

### **Scenario 2: User Organizes Favorites into Categories**

**Actor:** Maria (Food blogger)  
**Goal:** Organize her favorite restaurants by meal type  
**Context:** Maria has many favorite restaurants and wants to organize them  

**Steps:**
1. Maria opens MenuMap and goes to "My Favorites"
2. She sees 20 restaurants in her favorites list
3. Maria clicks "Organize Favorites" button
4. System shows drag-and-drop interface
5. Maria creates a new category called "Breakfast Spots"
6. She drags "Sunrise Cafe" and "Morning Glory" into "Breakfast Spots"
7. Maria creates another category called "Date Night"
8. She drags "Fancy Bistro" and "Romantic Italian" into "Date Night"
9. System saves her organization
10. Maria now has organized favorites by meal type

**Expected Result:** Maria successfully organizes her favorites into meaningful categories

---

### **Scenario 3: User Adds Menu Item to Favorites**

**Actor:** Alex (Health-conscious eater)  
**Goal:** Save his favorite healthy meal for quick reordering  
**Context:** Alex wants to quickly find his favorite healthy dish  

**Steps:**
1. Alex opens MenuMap and searches for "Healthy Bites"
2. System displays the restaurant and menu
3. Alex finds "Quinoa Power Bowl - $14.99" in the menu
4. He taps on the menu item to see details
5. System shows full description: "Quinoa, kale, chickpeas, avocado, tahini dressing"
6. Alex sees a "⭐ Add to Favorites" button
7. He taps the star button
8. System asks "Which category?" and shows options
9. Alex selects "Healthy Meals" category
10. System confirms "Added to Healthy Meals favorites!"

**Expected Result:** Alex successfully saves his favorite healthy meal to a specific category

---

## 🔒 UC-003: Secure Password Reset - Scenarios

### **Scenario 1: User Forgets Password and Resets Successfully**

**Actor:** Jennifer (Regular user)  
**Goal:** Reset her forgotten password securely  
**Context:** Jennifer hasn't used MenuMap in months and forgot her password  

**Steps:**
1. Jennifer opens MenuMap and tries to log in
2. She enters her email but can't remember her password
3. Jennifer clicks "Forgot Password?" link
4. System displays password reset form
5. She enters her email address: jennifer@email.com
6. System validates the email format
7. System generates a secure reset token
8. Jennifer receives an email with reset link
9. She clicks the link in the email
10. System validates the token and shows new password form
11. Jennifer enters new password: "NewSecurePass123!"
12. System validates password strength
13. Jennifer confirms the new password
14. System encrypts and stores the new password
15. System sends confirmation email
16. Jennifer can now log in with her new password

**Expected Result:** Jennifer successfully resets her password and regains access to her account

---

### **Scenario 2: User Attempts Reset with Invalid Email**

**Actor:** Tom (New user)  
**Goal:** Reset password but enters wrong email  
**Context:** Tom thinks he used a different email address  

**Steps:**
1. Tom opens MenuMap and clicks "Forgot Password?"
2. System displays password reset form
3. Tom enters email: "tom@wrongemail.com"
4. System validates email format (valid format)
5. System checks if email exists in database
6. System displays generic message: "If this email exists, you'll receive a reset link"
7. System logs the failed attempt for security monitoring
8. Tom doesn't receive any email (security measure)
9. Tom realizes he used the wrong email
10. He tries again with his correct email address

**Expected Result:** System protects against email enumeration while providing appropriate feedback

---

### **Scenario 3: User Clicks Expired Reset Link**

**Actor:** Robert (Busy professional)  
**Goal:** Reset password but link has expired  
**Context:** Robert received reset email but didn't check it for 2 days  

**Steps:**
1. Robert receives password reset email
2. He doesn't check his email for 2 days
3. Robert finally clicks the reset link
4. System checks token expiration (24-hour limit)
5. System detects token is expired
6. System displays error: "Reset link has expired"
7. System prompts: "Please request a new password reset"
8. Robert clicks "Request New Reset"
9. System generates new reset token
10. Robert receives new email with fresh reset link
11. He clicks the new link within 24 hours
12. System allows password reset to proceed

**Expected Result:** System enforces security time limits while allowing users to request new resets

---

## 📊 **Scenario Summary**

| Use Case | Scenario | Actor | Key Learning |
|----------|----------|-------|--------------|
| UC-001 | Search Italian Restaurants | Sarah | Basic search functionality |
| UC-001 | Browse by Cuisine | Mike | Filtering and sorting |
| UC-001 | Search Specific Item | Lisa | Menu item search |
| UC-002 | Add Restaurant to Favorites | David | Basic favorites management |
| UC-002 | Organize Favorites | Maria | Category management |
| UC-002 | Add Menu Item to Favorites | Alex | Item-level favorites |
| UC-003 | Successful Password Reset | Jennifer | Normal reset flow |
| UC-003 | Invalid Email Attempt | Tom | Security protection |
| UC-003 | Expired Reset Link | Robert | Time limit enforcement |

---

*These scenarios demonstrate the complete user journeys for each use case, showing how different types of users interact with the MenuMap system in various situations.*
