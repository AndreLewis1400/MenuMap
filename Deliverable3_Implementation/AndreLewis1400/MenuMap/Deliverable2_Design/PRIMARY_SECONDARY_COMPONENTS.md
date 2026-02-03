# Primary and Secondary Components - MenuMap Deliverable 2

## PRIMARY COMPONENTS (Core Architecture)

### 1. Primary Architectural Pattern: 3-Tier Architecture
- **MM_Client** (Presentation Tier)
- **MM_Logic** (Business Logic Tier) 
- **MM_DataStore** (Data Tier)

**Diagram:** `Model_Static_Menu_map_3_tier.PNG`

### 2. Primary Use Cases (7 Total)
- UC-001: Browse Restaurant Menus
- UC-002: Manage Favorites
- UC-003: Secure Password Reset
- UC-004: User Login
- UC-005: User Registration
- UC-006: User Logout
- UC-007: Restaurant Owner Menu Management

### 3. Primary Actors
- Guest User
- Registered User
- Restaurant Owner
- System Administrator

---

## SECONDARY COMPONENTS (Supporting Patterns)

### 1. Secondary Architectural Pattern: MVC
**Implemented within MM_Client tier:**
- **Model:** Data handling
- **View:** UI components (Forms, Dashboard)
- **Controller:** User interaction handlers

**Diagram:** `Package_MM_Client_MM_Client_Class_Dia.PNG`

### 2. Secondary Design Patterns
**Implemented within MM_Logic tier:**
- **Observer Pattern:** Real-time updates
- **Factory Pattern:** Object creation
- **Strategy Pattern:** Interchangeable algorithms

**Diagram:** `Package_MM_Logic_MM_Logic_Class_Dia.PNG`

### 3. Secondary Data Patterns
**Implemented within MM_DataStore tier:**
- **Repository Pattern:** Data access
- **Cache Management:** Performance optimization

**Diagram:** `Package_MM_DataStore_MM_Data_Store_Dia.PNG`

---

## Key Point
**Primary = Essential foundation | Secondary = Supporting enhancements**
