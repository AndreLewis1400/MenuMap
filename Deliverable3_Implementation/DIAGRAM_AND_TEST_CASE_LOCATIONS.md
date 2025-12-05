# Diagram and Test Case Insertion Guide
## For Andre Lewis (Group Lead) - Deliverable 3 Final Document

---

## 📍 WHERE TO ADD DIAGRAMS

### **Chapter 5: Software Architecture**

#### **Figure 5.1: Presentation Layer Class Diagram**
**Location:** After line ~260 (in Section 5.2.1)
**Current Text:**
```
**Figure 5.1: Presentation Layer Class Diagram**

[Insert diagram: `Package_MM_Client_MM_Client_Class_Dia.PNG`]
```

**Action:** Replace `[Insert diagram: ...]` with the actual image
**Diagram File:** `Deliverable2_Design/UML_Diagrams/Diagrams_Only/Package_MM_Clent_MM_Client_Class_Dia.PNG`
**Note:** File name has typo "Clent" instead of "Client" - use the actual file name

---

#### **Figure 5.2: Business Logic Layer Class Diagram**
**Location:** After line ~237 (in Section 5.2.2)
**Current Text:**
```
**Figure 5.2: Business Logic Layer Class Diagram**

[Insert diagram: `Package_MM_Logic_MM_Logic_Class_Dia.PNG`]
```

**Action:** Replace `[Insert diagram: ...]` with the actual image
**Diagram File:** `Deliverable2_Design/UML_Diagrams/Diagrams_Only/Package_MM_Logic_MM_Logic_Class_Dia.PNG`

---

#### **Figure 5.3: Data Access Layer Class Diagram**
**Location:** After line ~254 (in Section 5.2.3)
**Current Text:**
```
**Figure 5.3: Data Access Layer Class Diagram**

[Insert diagram: `Package_MM_DataStore_MM_Data_Store_Dia.PNG`]
```

**Action:** Replace `[Insert diagram: ...]` with the actual image
**Diagram File:** `Deliverable2_Design/UML_Diagrams/Diagrams_Only/Package_MM_DataStore_MM_Data_Store_Dia.PNG`

---

#### **Figure 5.4: 3-Tier Architecture Diagram**
**Location:** After line ~260 (in Section 5.2.3, after Figure 5.3)
**Current Text:**
```
**Figure 5.4: 3-Tier Architecture Diagram**

[Insert diagram: `Model_Static_Menu_Map_3_Tier.PNG` or `Model_Static_Model_Static_Menu_Map_3_Tier.PNG`]
```

**Action:** Replace `[Insert diagram: ...]` with the actual image
**Diagram File:** `Deliverable2_Design/UML_Diagrams/Diagrams_Only/Model_Static_Model_Static_Menu_Map_3_Tier.PNG`

---

### **Chapter 6: Detailed Design**

#### **Sequence Diagram for UC-001: Browse Restaurant Menus**
**Location:** Section 6.4 (Sequence Diagrams)
**Current Text:**
```
## 6.4 Sequence Diagrams

The system uses sequence diagrams to illustrate interactions between components. Key interactions include:

1. **Menu Browsing Flow**: User → MenuController → MenuService → MenuRepository → Database
2. **User Login Flow**: User → UserController → UserService → UserRepository → Database
3. **User Registration Flow**: User → UserController → UserService → UserRepository → Database
```

**Action:** Add sequence diagram reference and image for UC-001
**Diagram File:** `Deliverable2_Design/UML_Diagrams/Diagrams_Only/UC-001-Browse_Restaurant_Menus_Sequence.PNG`
**OR:** `Deliverable2_Design/UML_Diagrams/Diagrams_Only/Interaction_Interaction4_UC-001-Browse_Restaurant_Menus_Sequence.PNG`

**Suggested Addition:**
```
**Figure 6.1: UC-001 Sequence Diagram**

[Insert diagram: `UC-001-Browse_Restaurant_Menus_Sequence.PNG`]

**Caption:** Sequence Diagram for UC-001: Browse Restaurant Menus showing interaction between User, MenuController, MenuService, MenuRepository, and Database.
```

---

#### **Sequence Diagram for UC-005: User Login**
**Location:** Section 6.4 (Sequence Diagrams), after UC-001
**Diagram File:** `Deliverable2_Design/UML_Diagrams/Diagrams_Only/UC-005-User_Login.PNG`
**OR:** `Deliverable2_Design/UML_Diagrams/Diagrams_Only/Interaction_Interaction1_UC-005-User_Login.PNG`

**Suggested Addition:**
```
**Figure 6.2: UC-005 Sequence Diagram**

[Insert diagram: `UC-005-User_Login.PNG`]

**Caption:** Sequence Diagram for UC-005: User Login showing authentication flow through all three tiers.
```

---

## 📋 WHERE YOUR TEST CASES ARE

### **Chapter 7: Testing Process**

#### **Section 7.1.3: Test Cases**

**Your Test Cases Are Already in the Document:**

1. **UC-001: Browse Restaurant Menus** (8 test cases)
   - **Location:** Lines ~434-498
   - **Test Cases:**
     - TC-001-01: Successful Menu Browse (Sunny Day)
     - TC-001-02: Browse Menu with Filters (Sunny Day)
     - TC-001-03: Restaurant Not Found (Rainy Day)
     - TC-001-04: Menu Not Available (Rainy Day)
     - TC-001-05: Database Connection Error (Rainy Day)
     - TC-001-06: Invalid Search Input (Rainy Day)
     - TC-001-07: Timeout During Menu Load (Rainy Day)
     - TC-001-08: Restaurant Inactive/Closed (Rainy Day)

2. **UC-005: User Login** (10 test cases)
   - **Location:** Lines ~500-580
   - **Test Cases:**
     - TC-005-01: Successful Login (Sunny Day)
     - TC-005-02: Successful Login with User ID (Sunny Day)
     - TC-005-03: Invalid Password (Rainy Day)
     - TC-005-04: User Not Found (Rainy Day)
     - TC-005-05: Empty Required Fields (Rainy Day)
     - TC-005-06: Account Locked (Rainy Day)
     - TC-005-07: Email Not Verified (Rainy Day)
     - TC-005-08: SQL Injection Attempt (Rainy Day)
     - TC-005-09: Database Connection Error (Rainy Day)
     - TC-005-10: Multiple Failed Login Attempts (Rainy Day)

**Status:** ✅ All 18 test cases are already in the document and complete!

---

## 📝 HOW TO INSERT DIAGRAMS

### **Option 1: In Markdown (for GitHub)**
Replace the placeholder with:
```markdown
![Figure 5.1: Presentation Layer Class Diagram](Deliverable2_Design/UML_Diagrams/Diagrams_Only/Package_MM_Clent_MM_Client_Class_Dia.PNG)
```

### **Option 2: In Word Document (for final submission)**
1. Place cursor where `[Insert diagram: ...]` appears
2. Go to Insert → Pictures → This Device
3. Navigate to: `C:\Users\alewi\OneDrive\Desktop\MenuMap\Deliverable2_Design\UML_Diagrams\Diagrams_Only\`
4. Select the appropriate PNG file
5. Insert the image
6. Delete the placeholder text `[Insert diagram: ...]`
7. Ensure image is properly captioned below

---

## 📂 DIAGRAM FILE LOCATIONS

All diagrams are located in:
**Base Path:** `C:\Users\alewi\OneDrive\Desktop\MenuMap\Deliverable2_Design\UML_Diagrams\Diagrams_Only\`

### **Your Required Diagrams:**

1. **Package_MM_Clent_MM_Client_Class_Dia.PNG** (Note: typo "Clent")
   - For: Figure 5.1 - Presentation Layer

2. **Package_MM_Logic_MM_Logic_Class_Dia.PNG**
   - For: Figure 5.2 - Business Logic Layer

3. **Package_MM_DataStore_MM_Data_Store_Dia.PNG**
   - For: Figure 5.3 - Data Access Layer

4. **Model_Static_Model_Static_Menu_Map_3_Tier.PNG**
   - For: Figure 5.4 - 3-Tier Architecture

5. **UC-001-Browse_Restaurant_Menus_Sequence.PNG**
   - For: Figure 6.1 - UC-001 Sequence Diagram

6. **UC-005-User_Login.PNG**
   - For: Figure 6.2 - UC-005 Sequence Diagram

---

## ✅ CHECKLIST

### **Diagrams to Add:**
- [ ] Figure 5.1: Presentation Layer Class Diagram
- [ ] Figure 5.2: Business Logic Layer Class Diagram
- [ ] Figure 5.3: Data Access Layer Class Diagram
- [ ] Figure 5.4: 3-Tier Architecture Diagram
- [ ] Figure 6.1: UC-001 Sequence Diagram (if adding)
- [ ] Figure 6.2: UC-005 Sequence Diagram (if adding)

### **Test Cases:**
- [x] UC-001: All 8 test cases (already in document)
- [x] UC-005: All 10 test cases (already in document)
- [x] Database State Tables (already in document)
- [x] Test Results Summary (already in document)

---

## 🎯 SUMMARY

**Your Test Cases:** ✅ Already complete in Chapter 7, Section 7.1.3
- UC-001: 8 test cases (lines ~434-498)
- UC-005: 10 test cases (lines ~500-580)

**Your Diagrams:** Need to be inserted in:
- Chapter 5: 4 diagrams (Figures 5.1, 5.2, 5.3, 5.4)
- Chapter 6: 2 sequence diagrams (optional, for UC-001 and UC-005)

**All diagram files are ready in:** `Deliverable2_Design/UML_Diagrams/Diagrams_Only/`

---

**Last Updated:** December 2024

