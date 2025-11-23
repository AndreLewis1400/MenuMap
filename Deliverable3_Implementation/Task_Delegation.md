# MenuMap Deliverable 3 - Implementation Task Delegation
## CEN4010 Software Engineering - Team 9

**Project:** MenuMap Application  
**Deliverable:** 3 - Implementation  
**Group Lead:** Andre Lewis  
**Date:** [Current Date]  
**Version:** 1.0  

---

## 🎯 Deliverable 3 Overview

This document outlines the implementation tasks for MenuMap Deliverable 3. All team members have been assigned specific responsibilities based on their roles, skills, and the 7 use cases that need to be implemented.

---

## 👥 Team Members & Primary Responsibilities

| Team Member | Role | Primary Focus Area |
|------------|------|-------------------|
| **Alexandra Cozar** | Team Leader | Project coordination, integration, testing oversight |
| **Kamal Ayoub** | Minute Taker | Documentation, progress tracking, meeting coordination |
| **Alfonso Oramas** | Modeler | Database implementation, data layer, models |
| **Andre Lewis** | Software Architecture & Design Lead | Backend logic, architecture implementation, code review |

---

## 📋 Implementation Tasks by Use Case

### **UC-001: Browse Restaurant Menus**

#### **Task Breakdown:**
1. **Frontend Components** (Kamal Ayoub - if implementing)
   - Search bar component
   - Restaurant list/grid view component
   - Menu item detail modal/component
   - Filter components (location, cuisine, price range)
   - **Deliverable:** React components with TypeScript
   - **Deadline:** Week 1-2

2. **Backend API Endpoints** (Andre Lewis)
   - `GET /api/restaurants` - List restaurants with filters
   - `GET /api/restaurants/:id` - Get restaurant details
   - `GET /api/restaurants/:id/menu` - Get menu items
   - `GET /api/menu-items/search` - Search menu items
   - **Deliverable:** RESTful API endpoints with Spring Boot
   - **Deadline:** Week 1-2

3. **Database Schema & Queries** (Alfonso Oramas)
   - Restaurant table schema
   - MenuItem table schema
   - CuisineType table schema
   - Location/Address table schema
   - Optimized search queries with indexes
   - **Deliverable:** Database schema SQL + migration scripts
   - **Deadline:** Week 1

4. **Integration & Testing** (Alexandra Cozar)
   - Integration testing for full flow
   - End-to-end testing
   - Performance testing
   - **Deliverable:** Test suite and test results
   - **Deadline:** Week 3

---

### **UC-002: Manage Favorites**

#### **Task Breakdown:**
1. **Frontend Components** (Kamal Ayoub - if implementing)
   - Favorites list component
   - Add/remove favorite button component
   - Favorites organization/category component
   - **Deliverable:** React components with state management
   - **Deadline:** Week 2-3

2. **Backend API Endpoints** (Andre Lewis)
   - `POST /api/favorites` - Add favorite
   - `DELETE /api/favorites/:id` - Remove favorite
   - `GET /api/favorites` - Get user's favorites
   - `PUT /api/favorites/:id/category` - Organize favorite
   - **Deliverable:** RESTful API with authentication
   - **Deadline:** Week 2-3

3. **Database Schema** (Alfonso Oramas)
   - UserFavorite junction table
   - FavoriteCategory table
   - Relationships and foreign keys
   - **Deliverable:** Database schema and relationships
   - **Deadline:** Week 2

4. **Documentation** (Kamal Ayoub)
   - API documentation
   - User guide for favorites feature
   - **Deliverable:** Markdown documentation
   - **Deadline:** Week 3

---

### **UC-003: Secure Password Reset**

#### **Task Breakdown:**
1. **Backend Security Implementation** (Andre Lewis)
   - Password reset token generation
   - Email service integration
   - Token validation and expiration
   - Secure password hashing (BCrypt)
   - Rate limiting for password reset requests
   - **Deliverable:** Secure password reset service
   - **Deadline:** Week 2-3

2. **Frontend Components** (Kamal Ayoub - if implementing)
   - Password reset request form
   - Password reset confirmation form
   - Email verification UI
   - Security indicators and feedback
   - **Deliverable:** Secure UI components
   - **Deadline:** Week 2-3

3. **Database Schema** (Alfonso Oramas)
   - PasswordResetToken table
   - Token expiration tracking
   - Audit log table for security events
   - **Deliverable:** Security-related database schema
   - **Deadline:** Week 2

4. **Security Testing** (Alexandra Cozar)
   - Security vulnerability testing
   - Token expiration testing
   - Rate limiting testing
   - **Deliverable:** Security test report
   - **Deadline:** Week 3-4

---

### **UC-004: User Login**

#### **Task Breakdown:**
1. **Backend Authentication** (Andre Lewis)
   - JWT token generation
   - User authentication service
   - Session management
   - Login attempt tracking
   - **Deliverable:** Authentication service with JWT
   - **Deadline:** Week 1-2

2. **Frontend Components** (Kamal Ayoub - if implementing)
   - Login form component
   - Form validation
   - Error handling UI
   - Session state management
   - **Deliverable:** Login UI components
   - **Deadline:** Week 1-2

3. **Database Schema** (Alfonso Oramas)
   - User table with authentication fields
   - Session table (if needed)
   - LoginAttempt table for security
   - **Deliverable:** User authentication schema
   - **Deadline:** Week 1

4. **Integration Testing** (Alexandra Cozar)
   - Login flow testing
   - Authentication testing
   - Session management testing
   - **Deliverable:** Authentication test suite
   - **Deadline:** Week 2-3

---

### **UC-005: User Registration**

#### **Task Breakdown:**
1. **Backend Registration Service** (Andre Lewis)
   - User registration endpoint
   - Input validation
   - Email verification
   - Duplicate user checking
   - **Deliverable:** Registration API with validation
   - **Deadline:** Week 1-2

2. **Frontend Components** (Kamal Ayoub - if implementing)
   - Registration form component
   - Multi-step registration (if needed)
   - Form validation UI
   - Success/error feedback
   - **Deliverable:** Registration UI
   - **Deadline:** Week 1-2

3. **Database Schema** (Alfonso Oramas)
   - User table schema
   - EmailVerification table
   - UserProfile table
   - **Deliverable:** Registration database schema
   - **Deadline:** Week 1

4. **Documentation** (Kamal Ayoub)
   - Registration process documentation
   - API endpoint documentation
   - **Deliverable:** Registration documentation
   - **Deadline:** Week 2

---

### **UC-006: User Logout**

#### **Task Breakdown:**
1. **Backend Logout Service** (Andre Lewis)**
   - Logout endpoint
   - Token invalidation
   - Session cleanup
   - **Deliverable:** Logout API endpoint
   - **Deadline:** Week 2

2. **Frontend Components** (Kamal Ayoub - if implementing)
   - Logout button/component
   - Session cleanup on frontend
   - Redirect after logout
   - **Deliverable:** Logout UI component
   - **Deadline:** Week 2

3. **Integration** (Alexandra Cozar)
   - Logout flow testing
   - Session cleanup verification
   - **Deliverable:** Logout test cases
   - **Deadline:** Week 2-3

---

### **UC-007: Restaurant Owner Menu Management**

#### **Task Breakdown:**
1. **Backend Menu Management API** (Andre Lewis)
   - `POST /api/restaurants/:id/menu-items` - Add menu item
   - `PUT /api/menu-items/:id` - Update menu item
   - `DELETE /api/menu-items/:id` - Delete menu item
   - Role-based authorization (RestaurantOwner)
   - **Deliverable:** Menu management API with authorization
   - **Deadline:** Week 3-4

2. **Frontend Admin Components** (Kamal Ayoub - if implementing)
   - Menu item form (add/edit)
   - Menu item list with actions
   - Restaurant owner dashboard
   - Role-based UI rendering
   - **Deliverable:** Admin UI components
   - **Deadline:** Week 3-4

3. **Database Schema** (Alfonso Oramas)
   - RestaurantOwner table
   - Restaurant ownership relationships
   - Menu item versioning (if needed)
   - **Deliverable:** Owner management schema
   - **Deadline:** Week 3

4. **Authorization Testing** (Alexandra Cozar)
   - Role-based access control testing
   - Authorization boundary testing
   - **Deliverable:** Authorization test suite
   - **Deadline:** Week 4

---

## 🏗️ Architecture Implementation Tasks

### **3-Tier Architecture Setup**

#### **Tier 1: MM_Client (Presentation Layer)**
**Assigned to:** Kamal Ayoub (if implementing)
- React application setup
- Component library structure
- Routing setup
- State management (Redux/Context)
- **Deadline:** Week 1**

#### **Tier 2: MM_Logic (Business Logic Layer)**
**Assigned to:** Andre Lewis
- Spring Boot application setup
- Service layer implementation
- Controller layer
- Business logic implementation
- **Deadline:** Week 1**

#### **Tier 3: MM_DataStore (Data Layer)**
**Assigned to:** Alfonso Oramas
- PostgreSQL database setup
- Database connection configuration
- Repository layer setup
- Data access layer
- **Deadline:** Week 1**

---

## 🎨 Design Pattern Implementation

### **Observer Pattern**
**Assigned to:** Andre Lewis
- Implement observer pattern for real-time updates
- Menu update notifications
- Favorite change notifications
- **Deliverable:** Observer pattern implementation
- **Deadline:** Week 3**

### **Factory Pattern**
**Assigned to:** Andre Lewis
- Factory for creating different user types
- Factory for creating menu items
- **Deliverable:** Factory pattern implementation
- **Deadline:** Week 3**

### **Strategy Pattern**
**Assigned to:** Andre Lewis
- Search strategy (by location, cuisine, name)
- Payment strategy (if applicable)
- **Deliverable:** Strategy pattern implementation
- **Deadline:** Week 3**

---

## 📝 Documentation Tasks

### **Assigned to:** Kamal Ayoub

1. **API Documentation**
   - Swagger/OpenAPI documentation
   - Endpoint descriptions
   - Request/response examples
   - **Deadline:** Week 4**

2. **Implementation Documentation**
   - Code comments and JSDoc
   - Architecture decisions
   - Setup instructions
   - **Deadline:** Week 4**

3. **Meeting Minutes**
   - Weekly team meeting minutes
   - Decision log
   - Progress tracking
   - **Deadline:** Ongoing**

4. **User Documentation**
   - User guide for each feature
   - Installation guide
   - **Deadline:** Week 4**

---

## 🧪 Testing Tasks

### **Assigned to:** Alexandra Cozar (with support from all team members)

1. **Unit Testing**
   - Backend service unit tests (Andre Lewis)
   - Frontend component unit tests (Kamal Ayoub - if implementing)
   - Database query tests (Alfonso Oramas)
   - **Target:** 80% code coverage
   - **Deadline:** Week 4**

2. **Integration Testing**
   - API integration tests
   - Frontend-backend integration
   - Database integration tests
   - **Deadline:** Week 4**

3. **End-to-End Testing**
   - Complete user flows
   - All 7 use cases
   - **Deadline:** Week 4**

4. **Security Testing**
   - Authentication testing
   - Authorization testing
   - Input validation testing
   - **Deadline:** Week 4**

---

## 🔄 Integration & Deployment

### **Assigned to:** Alexandra Cozar (Team Leader)

1. **Code Integration**
   - Git branch management
   - Merge coordination
   - Conflict resolution
   - **Deadline:** Ongoing**

2. **Build & Deployment**
   - CI/CD pipeline setup
   - Environment configuration
   - Deployment scripts
   - **Deadline:** Week 4**

3. **Final Integration Testing**
   - Full system testing
   - Performance testing
   - User acceptance testing
   - **Deadline:** Week 4**

---

## 📅 Timeline & Milestones

### **Week 1: Foundation Setup**
- ✅ Database schema design and setup (Alfonso)
- ✅ Backend project setup (Andre)
- ✅ Frontend project setup (Evelio)
- ✅ Basic authentication (Andre)
- ✅ User registration (Andre + Evelio)
- ✅ User login (Andre + Evelio)

### **Week 2: Core Features**
- ✅ Browse Restaurant Menus (All)
- ✅ User logout (Andre + Evelio)
- ✅ Password reset backend (Andre)
- ✅ Password reset frontend (Evelio)

### **Week 3: Advanced Features**
- ✅ Manage Favorites (All)
- ✅ Design pattern implementation (Andre)
- ✅ Menu Management backend (Andre)
- ✅ Menu Management frontend (Evelio)

### **Week 4: Testing & Documentation**
- ✅ All testing (Alexandra + Team)
- ✅ Documentation completion (Kamal)
- ✅ Final integration (Alexandra)
- ✅ Deployment preparation (Alexandra)

---

## 📊 Task Summary by Team Member

### **Andre Lewis (Software Architecture & Design Lead)**
- Backend API development (all use cases)
- Business logic implementation
- Design pattern implementation
- Authentication & security
- Code review and architecture decisions
- **Estimated Hours:** 40-50 hours

### **Kamal Ayoub (Documentation & UI - if implementing)**
- All frontend components
- UI/UX implementation
- State management
- Form validation
- User interface design
- **Estimated Hours:** 35-45 hours

### **Alfonso Oramas (Modeler/Database)**
- Database schema design
- Database migrations
- Data access layer
- Query optimization
- Database testing
- **Estimated Hours:** 25-35 hours

### **Alexandra Cozar (Team Leader)**
- Project coordination
- Integration management
- Testing oversight
- Deployment coordination
- Team communication
- **Estimated Hours:** 30-40 hours

### **Kamal Ayoub (Minute Taker/Documentation)**
- Meeting minutes
- API documentation
- User documentation
- Progress tracking
- Implementation documentation
- **Estimated Hours:** 20-30 hours

---

## ✅ Deliverables Checklist

### **Code Deliverables**
- [ ] Backend API (Spring Boot) - All 7 use cases
- [ ] Frontend Application (React) - All 7 use cases
- [ ] Database Schema & Migrations
- [ ] Design Pattern Implementations (Observer, Factory, Strategy)
- [ ] Unit Tests (80% coverage)
- [ ] Integration Tests
- [ ] End-to-End Tests

### **Documentation Deliverables**
- [ ] API Documentation (Swagger/OpenAPI)
- [ ] Implementation Documentation
- [ ] User Guide
- [ ] Setup/Installation Guide
- [ ] Meeting Minutes (Weekly)
- [ ] Progress Reports

### **Deployment Deliverables**
- [ ] Working application (local or cloud)
- [ ] Deployment instructions
- [ ] Environment configuration
- [ ] CI/CD pipeline (if applicable)

---

## 🚨 Risk Management

### **Potential Risks & Mitigation**

1. **Risk:** Team member availability
   - **Mitigation:** Regular check-ins, clear deadlines, backup assignments

2. **Risk:** Integration issues
   - **Mitigation:** Early integration, frequent merges, clear API contracts

3. **Risk:** Scope creep
   - **Mitigation:** Strict adherence to use cases, regular scope review

4. **Risk:** Technical challenges
   - **Mitigation:** Early prototyping, team collaboration, design review

---

## 📞 Communication Plan

### **Weekly Team Meetings**
- **When:** [Schedule to be determined]
- **Facilitator:** Alexandra Cozar
- **Minute Taker:** Kamal Ayoub
- **Agenda:** Progress updates, blockers, next steps

### **Communication Channels**
- **Primary:** [To be determined - Slack/Discord/Teams]
- **Code Repository:** GitHub (AndreLewis1400/MenuMap)
- **Documentation:** Shared drive or GitHub wiki

---

## 🎯 Success Criteria

### **Technical Success**
- ✅ All 7 use cases implemented and working
- ✅ 80%+ code coverage with tests
- ✅ All design patterns implemented
- ✅ Security requirements met
- ✅ Performance requirements met (3-second page loads)

### **Team Success**
- ✅ All team members contributing
- ✅ Clear communication
- ✅ On-time delivery
- ✅ Quality code and documentation

---

## 📝 Notes

- **Flexibility:** Tasks may be adjusted based on team member availability and progress
- **Collaboration:** Team members should help each other when needed
- **Quality:** Code quality and testing are priorities
- **Documentation:** Keep documentation updated as you work

---

*This delegation document should be reviewed and updated weekly based on progress and team feedback.*

