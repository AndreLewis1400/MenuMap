# State Machine Diagram: User Authentication

## Overview
This state machine diagram models the user authentication and session management flow for the MenuMap application, following UML state machine notation similar to the example provided.

---

## **States (Rounded Rectangles)**

### **1. Ready (Initial Interactive State)**
- **Location:** Central left position
- **Description:** User is not logged in, ready to interact with the system
- **Entry Actions:** None
- **Exit Actions:** None

### **2. LoggedIn (Authenticated State)**
- **Location:** Central position, right of Ready
- **Description:** User has successfully authenticated and has an active session
- **Entry Actions:** Session token created, user role loaded
- **Exit Actions:** Session token invalidated

### **3. Registering (Registration State)**
- **Location:** Top left position
- **Description:** User is in the process of creating a new account
- **Entry Actions:** Registration form displayed
- **Exit Actions:** Registration data cleared

### **4. BrowseMenus (Browsing State)**
- **Location:** Top right position
- **Description:** User is browsing restaurant menus
- **Entry Actions:** Menu data loaded
- **Exit Actions:** None

### **5. ManageFavorites (Favorites Management State)**
- **Location:** Bottom right position
- **Description:** User is managing their favorite restaurants
- **Entry Actions:** Favorites list loaded
- **Exit Actions:** Changes saved

### **6. MenuManagement (Restaurant Owner State)**
- **Location:** Bottom left position
- **Description:** Restaurant owner is managing their menu
- **Entry Actions:** Menu editor loaded
- **Exit Actions:** Changes saved
- **Guard:** `[role == RestaurantOwner]`

---

## **Transitions (with Proper Format: event[guard]/action)**

### **Initial State → Ready**
- **From:** Initial (black circle labeled "Initial")
- **To:** Ready
- **Label:** (no label - automatic transition)

### **Ready → LoggedIn (Successful Login)**
- **From:** Ready
- **To:** LoggedIn
- **Label:** `login(username, password)[valid(username, password)]/loggedIn`
 - **Event:** `login(username, password)`
 - **Guard:** `[valid(username, password)]` (credentials are valid)
 - **Action:** `/loggedIn` (session established)

### **Ready → Ready (Failed Login - Self-Transition)**
- **From:** Ready
- **To:** Ready (self-loop)
- **Label:** `login(username, password)[!valid(username, password)]/print(errmsg)`
 - **Event:** `login(username, password)`
 - **Guard:** `[!valid(username, password)]` (credentials are invalid)
 - **Action:** `/print(errmsg)` (display error message)

### **Ready → Registering (Start Registration)**
- **From:** Ready
- **To:** Registering
- **Label:** `register()`
 - **Event:** `register()`

### **Registering → Ready (Registration Complete)**
- **From:** Registering
- **To:** Ready
- **Label:** `registrationComplete()`
 - **Event:** `registrationComplete()`
 - **Action:** (user can now log in)

### **Registering → Registering (Registration Failed - Self-Transition)**
- **From:** Registering
- **To:** Registering (self-loop)
- **Label:** `submitRegistration()[!validRegistrationData()]/print(validationErrors)`
 - **Event:** `submitRegistration()`
 - **Guard:** `[!validRegistrationData()]` (data validation failed)
 - **Action:** `/print(validationErrors)` (display validation errors)

### **LoggedIn → Ready (Logout)**
- **From:** LoggedIn
- **To:** Ready
- **Label:** `logout()`
 - **Event:** `logout()`
 - **Action:** Session invalidated

### **LoggedIn → BrowseMenus**
- **From:** LoggedIn
- **To:** BrowseMenus
- **Label:** `browseMenus()`
 - **Event:** `browseMenus()`
 - **Guard:** (no guard - all authenticated users can browse)

### **BrowseMenus → LoggedIn (Exit Browsing)**
- **From:** BrowseMenus
- **To:** LoggedIn
- **Label:** `exitBrowse()`
 - **Event:** `exitBrowse()`

### **LoggedIn → ManageFavorites**
- **From:** LoggedIn
- **To:** ManageFavorites
- **Label:** `manageFavorites()`
 - **Event:** `manageFavorites()`
 - **Guard:** (no guard - all authenticated users can manage favorites)

### **ManageFavorites → LoggedIn (Exit Favorites)**
- **From:** ManageFavorites
- **To:** LoggedIn
- **Label:** `exitFavorites()`
 - **Event:** `exitFavorites()`

### **LoggedIn → MenuManagement**
- **From:** LoggedIn
- **To:** MenuManagement
- **Label:** `manageMenu()[role == RestaurantOwner]`
 - **Event:** `manageMenu()`
 - **Guard:** `[role == RestaurantOwner]` (only Restaurant Owners can access)

### **MenuManagement → LoggedIn (Exit Menu Management)**
- **From:** MenuManagement
- **To:** LoggedIn
- **Label:** `exitMenuManagement()`
 - **Event:** `exitMenuManagement()`

---

## **Diagram Structure (Based on Example)**

### **Initial State**
- Black circle labeled "Initial" or "Initial1"
- Located at the top or left
- Single arrow pointing to "Ready"

### **State Layout**
```
 [Registering] [BrowseMenus]
 ↓ ↓
 [Ready] ←→ [LoggedIn] → [ManageFavorites]
 ↑ ↓
 [MenuManagement]
```

### **Transition Format Rules**
1. **Event:** Function call format (e.g., `login(username, password)`)
2. **Guard:** Boolean expression in square brackets (e.g., `[valid(username, password)]`)
3. **Action:** Slash-prefixed action (e.g., `/loggedIn`, `/print(errmsg)`)
4. **Format:** `event[guard]/action`
 - If no guard: `event/action`
 - If no action: `event[guard]`
 - If neither: just `event`

### **Self-Transitions**
- Used for error handling (failed login, failed registration)
- Arrow loops back to the same state
- Must include guard condition for failure case

---

## **Checklist for Papyrus Implementation**

- [ ] Initial state (black circle) labeled "Initial"
- [ ] All states are rounded rectangles
- [ ] State names are clear and descriptive
- [ ] Transitions have proper format: `event[guard]/action`
- [ ] Self-transitions exist for error cases (Ready → Ready, Registering → Registering)
- [ ] Role-based guards are used where appropriate (`[role == RestaurantOwner]`)
- [ ] Actions are prefixed with `/` (e.g., `/loggedIn`, `/print(errmsg)`)
- [ ] Guards are boolean expressions in square brackets
- [ ] Events are function calls with parameters where needed
- [ ] Diagram layout is clear and readable
- [ ] No "null" labels on any transitions

---

## **Common Issues to Fix**

### **Issue 1: Missing Event Labels**
- **Problem:** Transition shows "null" or no label
- **Fix:** Right-click transition → Properties → Name → Enter event name (e.g., `login(username, password)`)

### **Issue 2: Missing Guards**
- **Problem:** No guard condition on conditional transitions
- **Fix:** Right-click transition → Properties → Guard → Enter guard (e.g., `[valid(username, password)]`)

### **Issue 3: Missing Actions**
- **Problem:** No action specified on transitions that should have actions
- **Fix:** Right-click transition → Properties → Effect → Enter action (e.g., `/loggedIn`)

### **Issue 4: Self-Transitions Not Showing**
- **Problem:** Failed login should loop back to Ready
- **Fix:** Draw transition from Ready to Ready (self-loop), add guard `[!valid(username, password)]`

### **Issue 5: Incorrect Transition Format**
- **Problem:** Format doesn't match `event[guard]/action`
- **Fix:** Ensure format is exactly: `event[guard]/action` (no spaces around brackets/slash)

---

## **Example Transition Labels**

```
 CORRECT:
login(username, password)[valid(username, password)]/loggedIn
logout()
register()
manageMenu()[role == RestaurantOwner]
login(username, password)[!valid(username, password)]/print(errmsg)

 INCORRECT:
login (no parameters)
[valid] (no event)
loggedIn (no event, should be /loggedIn as action)
login[valid]/loggedIn (missing parentheses for event parameters)
```

---

## **Visual Layout Recommendations**

1. **Initial State:** Top center or top left
2. **Ready:** Central left (main entry point)
3. **LoggedIn:** Central right (main authenticated state)
4. **Registering:** Top left (related to Ready)
5. **BrowseMenus:** Top right (common action)
6. **ManageFavorites:** Bottom right (common action)
7. **MenuManagement:** Bottom left (restricted action)

---

## **Notes**

- This state machine follows the same pattern as the example:
 - Initial → Ready → LoggedIn flow
 - Self-transitions for error handling
 - Role-based guards for restricted actions
 - Clear event/guard/action format on all transitions
- All transitions must have proper labels (no "null" labels)
- Guards are optional but should be used for conditional transitions
- Actions are optional but should be used when state changes trigger side effects

