# Deliverable 3 Presentation - Talking Points
## Team 9 - MenuMap System
## Andre Lewis (Team Lead)
## Presentation: Today at 4:15pm

---

## QUICK REFERENCE

**Total Time:** 30 minutes (20 min presenting + 10 min Q&A) 
**Alexandra's Slides:** Slides 1-7 (~4-5 minutes) 
**Your Slides:** Slides 9-25 (~15-16 minutes) 
**Your Role:** Main Presenter (Architecture, Design, Testing, Summary)

---

## YOUR SLIDE-BY-SLIDE TALKING POINTS

### **TRANSITION FROM ALEXANDRA** (~10 seconds)

**After Alexandra finishes Slide 7 (UC-003 Continued):**

**Your Opening Statement:**
"Thank you, Alexandra, for presenting our functional requirements. Now I'll take over to present our system architecture, design, and testing. Let me start with our software architecture."

---

### **SLIDE 9: Software Architecture Diagram** (~1.5 minutes)

**Point to Diagram:**
- "This is our Software Architecture Diagram showing the 3-Tier Architecture of MenuMap"

**Architectural Style:**
- "We chose a 3-Tier Architecture as our primary architectural style"

**Tier 1: Presentation Layer (MM_Client)**
- "The presentation layer handles user interactions
- Contains controllers: MenuController, UserController, RestaurantController
- Manages views and user interface components
- Handles HTTP requests and responses"

**Tier 2: Business Logic Layer (MM_Logic)**
- "The business logic layer implements our core functionality
- Contains services: MenuService, UserService, RestaurantService, VerificationService
- Implements business rules and validation
- Processes data before storage or retrieval"

**Tier 3: Data Layer (MM_DataStore)**
- "The data layer manages database operations
- Contains DAOs: MenuDAO, UserDAO, RestaurantDAO
- Contains data models: User, Restaurant, MenuItem, Session
- Handles all database operations"

**Architectural Patterns:**
- "We implemented multiple architectural patterns:
 - 3-Tier Architecture as our primary pattern
 - MVC Pattern within the Presentation Tier
 - Layered Architecture for separation of concerns"

**Transition:**
"Let me explain our data management approach."

---

### **SLIDE 10: Data Management - Part 1** (~1 minute)

**Database Type:**
- "We use a relational database - MySQL or PostgreSQL"

**Primary Entities:**
- "Our database has three primary entities:
 
 **Users:**
 - Stores user accounts and authentication information
 - Attributes include: userId, email, password (hashed), firstName, lastName, accountStatus, emailVerified
 
 **Restaurants:**
 - Stores restaurant information and details
 - Attributes include: restaurantId, name, address, phone, status, ownerUserId
 
 **MenuItems:**
 - Stores individual menu items with descriptions and prices
 - Attributes include: menuItemId, restaurantId, itemName, description, price, category, available"

**Relationships:**
- "We have three key relationships:
 - Users to Restaurants: One-to-Many (Owner relationship)
 - Restaurants to MenuItems: One-to-Many
 - Users to Sessions: One-to-Many"

**Transition:**
"Now let me explain how we access and secure this data."

---

### **SLIDE 11: Data Management - Part 2** (~1 minute)

**Data Access Objects (DAOs):**
- "We use DAOs to abstract database operations:
 
 **MenuDAO:**
 - Handles menu data operations
 - Methods: findMenuByRestaurantId(), saveMenu(), updateMenu()
 
 **UserDAO:**
 - Manages user data operations
 - Methods: findUserByEmail(), saveUser(), updateUser()
 
 **RestaurantDAO:**
 - Handles restaurant data operations
 - Methods: findRestaurantById(), saveRestaurant(), updateRestaurant()"

**Data Integrity:**
- "We ensure data integrity through:
 - Foreign key constraints for referential integrity
 - Transaction management for data consistency
 - Validation at service layer before persistence"

**Data Security:**
- "We implement multiple security measures:
 - Passwords stored as hashed values using BCrypt
 - Sensitive data encrypted in transit using HTTPS
 - Parameterized queries to prevent SQL injection"

**Transition:**
"Now let me discuss our security and privacy measures."

---

### **SLIDE 12: Security/Privacy - Part 1** (~1 minute)

**Authentication Mechanisms:**
- "We implement four authentication mechanisms:
 - Email/User ID and password authentication
 - Secure password hashing using BCrypt algorithm
 - Session management with secure tokens
 - Password reset with time-limited tokens"

**Access Control:**
- "We use Role-Based Access Control (RBAC):
 - Customer role: Can browse menus and manage favorites
 - Restaurant Owner role: Can manage own restaurant menus
 - Administrator role: Can verify menus and manage system
- Authorization checks occur at the service layer
- Unauthorized access attempts are logged"

**Session Management:**
- "We implement secure session management:
 - Secure session tokens
 - Session timeout after inactivity
 - Session invalidation on logout
 - Protection against session hijacking"

**Transition:**
"Let me continue with data encryption and privacy protection."

---

### **SLIDE 13: Security/Privacy - Part 2** (~1 minute)

**Data Encryption:**
- "We encrypt data in multiple ways:
 - Passwords: BCrypt hashing (one-way encryption)
 - Data in transit: HTTPS/TLS encryption
 - Sensitive data: Encrypted at rest in database
 - Reset tokens: Cryptographically secure random generation"

**Privacy Protection:**
- "We protect user privacy through:
 - User data access restricted to authorized users
 - No information leakage in error messages
 - Secure password reset process
 - Email verification required for account activation"

**Security Measures:**
- "We implement comprehensive security measures:
 - SQL injection prevention through parameterized queries
 - Input validation and sanitization
 - XSS (Cross-Site Scripting) prevention
 - CSRF (Cross-Site Request Forgery) protection
 - Account lockout after multiple failed login attempts"

**Transition:**
"Now let me show you our class diagrams, starting with the Presentation Layer."

---

### **SLIDE 14: Minimal Class Diagram - Part 1** (~45 seconds)

**Point to Diagram:**
- "This is our Presentation Layer Class Diagram showing Controllers and Views"

**Presentation Layer Classes:**
- "We have three main controllers:
 - **MenuController**: Handles menu browsing requests
 - **UserController**: Manages authentication and user management
 - **RestaurantController**: Handles restaurant operations"

**Design Patterns:**
- "We identified two design patterns in this layer:
 - **MVC Pattern**: Model-View-Controller separation
 - **Front Controller Pattern**: Centralized request handling"

**Transition:**
"Now let me show you the Business Logic Layer."

---

### **SLIDE 15: Minimal Class Diagram - Part 2** (~45 seconds)

**Point to Diagram:**
- "This is our Business Logic Layer Class Diagram showing Service classes"

**Business Logic Layer Classes:**
- "We have four main services:
 - **MenuService**: Menu business logic and validation
 - **UserService**: User authentication and management logic
 - **RestaurantService**: Restaurant management logic
 - **VerificationService**: Menu verification processes"

**Design Patterns:**
- "We identified two design patterns in this layer:
 - **Service Layer Pattern**: Encapsulates business logic
 - **Strategy Pattern**: Different validation strategies"

**Transition:**
"Now let me show you the Data Access Layer."

---

### **SLIDE 16: Minimal Class Diagram - Part 3** (~45 seconds)

**Point to Diagram:**
- "This is our Data Access Layer Class Diagram showing DAOs and Data Models"

**Data Access Layer Classes:**
- "We have three main DAOs:
 - **MenuDAO**: Database operations for menus
 - **UserDAO**: Database operations for users
 - **RestaurantDAO**: Database operations for restaurants"

**Data Models:**
- "Our data models include:
 - **User**: User entity with authentication data
 - **Restaurant**: Restaurant entity with business information
 - **MenuItem**: Menu item entity with product details"

**Design Patterns:**
- "We identified two design patterns in this layer:
 - **DAO Pattern**: Abstracts database access operations
 - **Repository Pattern**: Encapsulates data access logic"

**Transition:**
"Now let me show you how these layers interact in a sequence diagram."

---

### **SLIDE 17: Sequence Diagram** (~1 minute)

**Point to Diagram:**
- "This is our Sequence Diagram for UC-001: Browse Restaurant Menus"

**Interaction Flow (8 steps):**
1. "User requests menu view"
2. "MenuController receives request"
3. "MenuController calls MenuService"
4. "MenuService applies business rules"
5. "MenuService calls MenuDAO"
6. "MenuDAO queries Database"
7. "Data flows back through layers"
8. "User receives menu display"

**Lifelines:**
- "The diagram shows five lifelines:
 - User (Actor)
 - MenuController (Presentation Layer)
 - MenuService (Business Logic Layer)
 - MenuDAO (Data Access Layer)
 - Database (External System)"

**Key Point:**
- "This demonstrates how our 3-tier architecture separates concerns and allows data to flow cleanly through each layer."

**Transition:**
"Now let me present our test cases, starting with UC-001."

---

### **SLIDE 18: Test Cases - UC-001 Sunny Day** (~1 minute)

**Test Case Introduction:**
- "This is our Sunny Day test case for UC-001: Browse Restaurant Menus"

**Test Case ID:**
- "SystemTest-011-UC001"

**Purpose:**
- "This test verifies that a user can successfully browse and view a restaurant menu"

**Test Setup:**
- "Restaurant 'Joe's Pizza' exists with menu items in database"

**Data Model (Point to Table):**
- "Before the test, we have:
 - Restaurant ID 101: Joe's Pizza (Active)
 - Three menu items: Margherita Pizza ($12.99), Pepperoni Pizza ($14.99), Caesar Salad ($8.99)"

**Test Steps (4 steps):**
1. "User navigates to MenuMap application"
2. "User searches for 'Joe's Pizza'"
3. "User selects 'Joe's Pizza' from results"
4. "System displays menu with all items"

**Expected Output:**
- "Menu displays correctly with all items, prices, and descriptions"
- "All menu items visible"
- "Categories properly organized"

**Result:**
- " PASS - Test passed successfully"

**Transition:**
"Now let me show you a rainy day scenario."

---

### **SLIDE 19: Test Cases - UC-001 Rainy Day** (~1 minute)

**Test Case Introduction:**
- "This is our Rainy Day test case for UC-001"

**Test Case ID:**
- "SystemTest-013-UC001"

**Purpose:**
- "This test verifies system handles search for non-existent restaurant"

**Test Setup:**
- "Restaurant does not exist in database"

**Data Model (Point to Table):**
- "Before the test, we have two restaurants: Joe's Pizza and Burger Palace, both Active"

**Test Steps (3 steps):**
1. "User navigates to MenuMap application"
2. "User searches for 'NonExistent Restaurant'"
3. "System processes search request"

**Expected Output:**
- "Appropriate error message displayed: 'No restaurants found matching your search'"
- "User-friendly message with no technical details"
- "User can retry search"

**Data Model After Test:**
- "No changes to database"
- "No data corruption"

**Result:**
- " PASS - Test passed successfully"

**Transition:**
"Now I'll hand it over to Kamal to present the test cases for our security use case."

---

### **TRANSITION TO KAMAL** (~10 seconds)

**Your Statement:**
"Now I'll hand it over to Kamal to present the test cases for our security use case, UC-003."

**After Kamal finishes Slide 21:**
"Thank you, Kamal. Let me present one more test case for UC-001."

---

### **SLIDE 22: Test Cases - UC-001 Additional** (~45 seconds)

**Test Case Introduction:**
- "This is an additional test case for UC-001: Browse Restaurant Menus"

**Test Case ID:**
- "SystemTest-012-UC001"

**Purpose:**
- "This test verifies that user can filter menu items by category"

**Test Setup:**
- "Restaurant exists with menu items in multiple categories"

**Data Model (Point to Table):**
- "Before the test, we have four menu items:
 - Two entrees: Margherita Pizza, Pepperoni Pizza
 - Two appetizers: Caesar Salad, Garlic Bread"

**Test Steps (3 steps):**
1. "User views restaurant menu"
2. "User selects 'Appetizers' filter"
3. "System applies category filter"

**Expected Output:**
- "Only appetizer items displayed: Caesar Salad, Garlic Bread"
- "Entree items hidden"
- "Filter works correctly"

**Result:**
- " PASS - Test passed successfully"

**Transition:**
"Kamal will now present the additional test case for UC-003."

---

### **After Kamal finishes Slide 23:**

**Transition Statement:**
"Thank you, Kamal. Let me now summarize our key achievements."

---

### **SLIDE 24: Summary** (~1 minute)

**Key Achievements:**

**Complete Implementation:**
- "We've successfully implemented all use cases"
- "Our 3-tier architecture has been successfully deployed"
- "We created 33 comprehensive test cases with a 100% pass rate"

**Security Features:**
- "We implemented secure password reset (UC-003)"
- "Passwords are hashed and encrypted"
- "SQL injection prevention is in place"
- "Access control has been implemented"

**Quality Assurance:**
- "We conducted comprehensive testing covering both sunny day and rainy day scenarios"
- "Data models have been validated"
- "Error handling has been verified"

**System Status:**
- "Our system is ready for deployment"

**Transition:**
"Now we welcome your questions."

---

### **SLIDE 25: Q&A** (~10 minutes)

**Opening Statement:**
"We welcome your questions about:
- System architecture and design
- Implementation details
- Testing process and results
- Security measures
- Use case functionality
- Any other aspects of the project"

**During Q&A:**
- **Direct questions to appropriate team members:**
 - Architecture/Design questions → You (Andre)
 - Security questions → Alexandra
 - Test case questions → Kamal
 - General questions → Any team member

**Closing Statement:**
"Thank you for your attention. If you have any further questions, please feel free to contact us.
- Team Lead: Andre Lewis
- Team 9, CEN 4010
- Florida International University"

---

## PRESENTATION TIPS

### **Before You Start:**
1. **Take a deep breath** - You've got this!
2. **Check your slides** - Make sure slides 9-25 are loaded
3. **Have water nearby** - Stay hydrated
4. **Test your microphone** - Ensure you can be heard
5. **Listen to Alexandra** - Be ready for smooth transition

### **During Presentation:**
1. **Speak clearly** - Don't rush, enunciate
2. **Make eye contact** - Look at audience/camera
3. **Point to diagrams** - Use your cursor or pointer
4. **Pause for emphasis** - Let important points sink in
5. **Stay on time** - Keep track of your pace (~15-16 minutes)

### **Transitions:**
- **From Alexandra:** "Thank you, Alexandra, for presenting our functional requirements..."
- **To Kamal:** "Now I'll hand it over to Kamal to present the test cases for our security use case..."
- **From Kamal:** "Thank you, Kamal. Let me now summarize our key achievements..."

### **If You Get Stuck:**
- **Pause** - Take a breath, it's okay
- **Refer to slide** - The slide has the information
- **Ask team** - You can defer to Alexandra or Kamal if needed

---

## TIME MANAGEMENT

**Your Total Time: ~15-16 minutes**

**Breakdown:**
- Slide 9 (Architecture): ~1.5 minutes
- Slides 10-11 (Data Management): ~2 minutes
- Slides 12-13 (Security/Privacy): ~2 minutes
- Slides 14-16 (Class Diagrams): ~2.25 minutes
- Slide 17 (Sequence Diagram): ~1 minute
- Slides 18-19 (UC-001 Tests): ~2 minutes
- Slide 22 (UC-001 Additional): ~45 seconds
- Slide 24 (Summary): ~1 minute
- **Total: ~12.5 minutes** (with buffer for transitions and questions)

**Pacing:**
- **Fast sections:** Class diagrams, transitions
- **Normal pace:** Architecture, data management
- **Slower pace:** Complex explanations (architecture, sequence diagram, test cases)

---

## FINAL CHECKLIST

**Before Presentation:**
- [ ] Review all your slides (9-25) one more time
- [ ] Practice your transition from Alexandra
- [ ] Practice transitions to/from Kamal
- [ ] Know where all diagrams are located
- [ ] Have backup plan if technology fails
- [ ] Listen to Alexandra's presentation to be ready for transition
- [ ] Get good night's sleep
- [ ] Eat a good meal before
- [ ] Arrive early (if in-person)

**During Presentation:**
- [ ] Listen to Alexandra's presentation
- [ ] Smooth transition from Alexandra
- [ ] Speak clearly and confidently
- [ ] Point to diagrams when explaining
- [ ] Make eye contact with audience
- [ ] Stay within time limits (~15-16 minutes)
- [ ] Support your team members
- [ ] Stay calm if something goes wrong

**After Presentation:**
- [ ] Thank the audience
- [ ] Be ready for Q&A
- [ ] Support team members during Q&A
- [ ] Celebrate when done! 

---

## KEY MESSAGES TO EMPHASIZE

1. **Complete Implementation** - All use cases implemented and tested
2. **Strong Architecture** - Well-designed 3-tier architecture
3. **Security Focus** - Comprehensive security measures
4. **Quality Testing** - 33 test cases, 100% pass rate
5. **Team Collaboration** - Successful team effort

---

## CONFIDENCE BOOSTERS

- **You know this material** - You've been working on it all semester
- **You're the team lead** - You've coordinated everything
- **You've prepared** - You've reviewed all slides
- **Your team is ready** - Alexandra and Kamal are prepared
- **You've got this!** - Take a deep breath and go!

---

## YOUR SLIDES SUMMARY

**Slides You're Presenting:**
- Slide 9: Software Architecture Diagram
- Slide 10: Data Management - Part 1
- Slide 11: Data Management - Part 2
- Slide 12: Security/Privacy - Part 1
- Slide 13: Security/Privacy - Part 2
- Slide 14: Minimal Class Diagram - Part 1 (Presentation Layer)
- Slide 15: Minimal Class Diagram - Part 2 (Business Logic Layer)
- Slide 16: Minimal Class Diagram - Part 3 (Data Access Layer)
- Slide 17: Sequence Diagram
- Slide 18: Test Cases - UC-001 Sunny Day
- Slide 19: Test Cases - UC-001 Rainy Day
- Slide 22: Test Cases - UC-001 Additional
- Slide 24: Summary
- Slide 25: Q&A

**Total: 14 slides (~15-16 minutes)**

---

**GOOD LUCK! YOU'VE GOT THIS! **

**Presentation Time: 4:15pm Today**

**Break a leg! (But not literally )**
