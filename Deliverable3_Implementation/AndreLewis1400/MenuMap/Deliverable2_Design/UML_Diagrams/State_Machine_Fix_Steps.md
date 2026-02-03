# State Machine Diagram - Step-by-Step Fix Guide

## Quick Reference: What Your Diagram Should Look Like

Based on the example you showed, here's exactly what to fix:

---

## **STEP 1: Check Initial State**

**What to do:**
1. Open your state machine diagram in Papyrus
2. Look for a **black circle** labeled "Initial" or "Initial1"
3. It should have an arrow pointing to the "Ready" state

**If missing:**
- Add Initial State from palette
- Draw transition from Initial → Ready (no label needed)

---

## **STEP 2: Fix Transition Labels (CRITICAL)**
Í
**Format for ALL transitions:** `event[guard]/action`

### **Example from your attachment:**
```
login(userid, pwd)[valid(userid, pwd)]/loggedIn
```

### **How to fix in Papyrus:**
1. **Right-click on each transition** → Properties
2. **Name field:** Enter the event (e.g., `login(username, password)`)
3. **Guard field:** Enter guard condition (e.g., `[valid(username, password)]`)
4. **Effect field:** Enter action (e.g., `/loggedIn`)

### **Required Transitions to Fix:**

#### **1. Ready → LoggedIn (Successful Login)**
- **Label:** `login(username, password)[valid(username, password)]/loggedIn`
- **Event:** `login(username, password)`
- **Guard:** `[valid(username, password)]`
- **Action:** `/loggedIn`

#### **2. Ready → Ready (Failed Login - SELF-TRANSITION)**
- **Label:** `login(username, password)[!valid(username, password)]/print(errmsg)`
- **Event:** `login(username, password)`
- **Guard:** `[!valid(username, password)]`
- **Action:** `/print(errmsg)`
- **IMPORTANT:** This is a self-loop (arrow from Ready back to Ready)

#### **3. Ready → Registering**
- **Label:** `register()`
- **Event:** `register()`
- **Guard:** (none)
- **Action:** (none)

#### **4. Registering → Ready (Success)**
- **Label:** `registrationComplete()`
- **Event:** `registrationComplete()`
- **Guard:** (none)
- **Action:** (none)

#### **5. Registering → Registering (Failed - SELF-TRANSITION)**
- **Label:** `submitRegistration()[!validRegistrationData()]/print(validationErrors)`
- **Event:** `submitRegistration()`
- **Guard:** `[!validRegistrationData()]`
- **Action:** `/print(validationErrors)`
- **IMPORTANT:** This is a self-loop (arrow from Registering back to Registering)

#### **6. LoggedIn → Ready (Logout)**
- **Label:** `logout()`
- **Event:** `logout()`
- **Guard:** (none)
- **Action:** (none)

#### **7. LoggedIn → BrowseMenus**
- **Label:** `browseMenus()`
- **Event:** `browseMenus()`
- **Guard:** (none)
- **Action:** (none)

#### **8. BrowseMenus → LoggedIn**
- **Label:** `exitBrowse()`
- **Event:** `exitBrowse()`
- **Guard:** (none)
- **Action:** (none)

#### **9. LoggedIn → ManageFavorites**
- **Label:** `manageFavorites()`
- **Event:** `manageFavorites()`
- **Guard:** (none)
- **Action:** (none)

#### **10. ManageFavorites → LoggedIn**
- **Label:** `exitFavorites()`
- **Event:** `exitFavorites()`
- **Guard:** (none)
- **Action:** (none)

#### **11. LoggedIn → MenuManagement (Role-Based)**
- **Label:** `manageMenu()[role == RestaurantOwner]`
- **Event:** `manageMenu()`
- **Guard:** `[role == RestaurantOwner]`
- **Action:** (none)

#### **12. MenuManagement → LoggedIn**
- **Label:** `exitMenuManagement()`
- **Event:** `exitMenuManagement()`
- **Guard:** (none)
- **Action:** (none)

---

## **STEP 3: Add Self-Transitions (If Missing)**

**Self-transitions are critical for error handling!**

### **How to add self-transitions:**
1. Draw a transition from a state back to itself (loop)
2. The arrow should curve back to the same state
3. Add proper label with guard for failure case

### **Required Self-Transitions:**

1. **Ready → Ready** (Failed Login)
 - Label: `login(username, password)[!valid(username, password)]/print(errmsg)`

2. **Registering → Registering** (Failed Registration)
 - Label: `submitRegistration()[!validRegistrationData()]/print(validationErrors)`

---

## **STEP 4: Fix "null" Labels**

**Problem:** Transitions showing "null" instead of proper labels

**Fix:**
1. Right-click transition → Properties
2. **Name:** Enter event (e.g., `login(username, password)`)
3. **Guard:** Enter guard if conditional (e.g., `[valid(username, password)]`)
4. **Effect:** Enter action if needed (e.g., `/loggedIn`)

**Note:** The label will automatically combine: `event[guard]/action`

---

## **STEP 5: Verify States Exist**

**Required States:**
- [ ] **Initial** (black circle)
- [ ] **Ready** (rounded rectangle)
- [ ] **LoggedIn** (rounded rectangle)
- [ ] **Registering** (rounded rectangle)
- [ ] **BrowseMenus** (rounded rectangle)
- [ ] **ManageFavorites** (rounded rectangle)
- [ ] **MenuManagement** (rounded rectangle)

---

## **STEP 6: Verify Transition Format**

**Correct Format Examples:**
```
 login(username, password)[valid(username, password)]/loggedIn
 logout()
 register()
 manageMenu()[role == RestaurantOwner]
 login(username, password)[!valid(username, password)]/print(errmsg)
```

**Incorrect Format Examples:**
```
 login (missing parameters)
 [valid] (no event)
 loggedIn (should be /loggedIn as action)
 login[valid]/loggedIn (missing parentheses)
 login (username, password) (spaces around parentheses)
```

---

## **Common Papyrus Issues & Fixes**

### **Issue 1: Can't see transition labels**
- **Fix:** Zoom in or adjust label position
- Right-click transition → Properties → Appearance → Adjust label position

### **Issue 2: Guard syntax error (red X)**
- **Fix:** Ensure guard is exactly: `[valid(username, password)]`
- No extra quotes, no spaces inside brackets
- Use `==` for equality, `!=` for not equal

### **Issue 3: Self-transition looks wrong**
- **Fix:** Draw transition from state to itself
- The arrow should curve back to the same state
- Make sure it's a proper transition, not just a note

### **Issue 4: Action not showing with "/"**
- **Fix:** In Effect field, enter: `/loggedIn` (with slash)
- The "/" prefix indicates an action

---

## **Final Checklist**

Before exporting, verify:

- [ ] Initial state (black circle) exists and points to Ready
- [ ] All 6 states exist (Ready, LoggedIn, Registering, BrowseMenus, ManageFavorites, MenuManagement)
- [ ] All transitions have proper labels (no "null")
- [ ] Format is `event[guard]/action` (or `event` if no guard/action)
- [ ] Self-transitions exist for:
 - Ready → Ready (failed login)
 - Registering → Registering (failed registration)
- [ ] Role-based guard exists: `[role == RestaurantOwner]` on LoggedIn → MenuManagement
- [ ] Actions are prefixed with `/` (e.g., `/loggedIn`, `/print(errmsg)`)
- [ ] Guards are in square brackets (e.g., `[valid(username, password)]`)
- [ ] Events have parentheses for parameters (e.g., `login(username, password)`)

---

## **Visual Layout (Recommended)**

```
 [Registering] [BrowseMenus]
 ↓ ↓
 [Ready] ←→ [LoggedIn] → [ManageFavorites]
 ↑ ↓
 [MenuManagement]
```

**Initial state** should be at the top, pointing to **Ready**.

---

## **After Fixing**

1. **Save** your Papyrus diagram
2. **Export as PNG** (Right-click diagram → Export → Image)
3. **Replace** the file in: `Deliverable2_Design/UML_Diagrams/Diagrams_Only/State_Machine_StateMachine1_UserAuthentication_StateMachine.PNG`
4. **Commit and push** to GitHub

---

## **Quick Tips**

- **Format consistency:** All transitions should follow the same format pattern
- **Self-transitions:** Use for error handling (failed login, failed registration)
- **Guards:** Use for conditional transitions (valid credentials, role checks)
- **Actions:** Use when state change triggers side effects (session creation, error display)
- **No spaces:** Don't add spaces around brackets or slash: `event[guard]/action` (not `event [guard] / action`)

