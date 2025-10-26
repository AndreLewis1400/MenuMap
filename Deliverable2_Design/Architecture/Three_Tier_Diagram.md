# MenuMap 3-Tier Architecture Diagram
## CEN4010 Software Engineering - Team 9

**Author:** Andre Lewis (Software Architecture & Design Lead)  
**Date:** October 19, 2025  
**Version:** 1.0

---

## 🏗️ 3-Tier Architecture Visual Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                           TIER 1: PRESENTATION TIER                            │
│                              (Client Tier)                                     │
├─────────────────────────────────────────────────────────────────────────────────┤
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐              │
│  │   Web Interface │  │ Mobile Interface│  │  API Interface  │              │
│  │   (React/HTML)  │  │ (React Native)  │  │ (REST/GraphQL)  │              │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘              │
│           │                     │                     │                        │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐              │
│  │   LoginForm     │  │   MobileApp     │  │  RESTEndpoints  │              │
│  │   Dashboard     │  │ ResponsiveDesign│  │ GraphQLQueries  │              │
│  │   MenuBrowser   │  │ TouchOptimization│  │ WebSocketConn   │              │
│  │   UserProfile   │  │ OfflineSupport  │  │ AuthEndpoints   │              │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘              │
└─────────────────────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                          TIER 2: BUSINESS LOGIC TIER                           │
│                            (Application Tier)                                  │
├─────────────────────────────────────────────────────────────────────────────────┤
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐              │
│  │ Use Case        │  │ Business        │  │ Security        │              │
│  │ Controllers     │  │ Services        │  │ Services        │              │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘              │
│           │                     │                     │                        │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐              │
│  │MenuBrowsingCtrl │  │ MenuService     │  │ Authentication  │              │
│  │FavoritesCtrl    │  │ UserService     │  │ Authorization   │              │
│  │AuthController   │  │ NotificationSvc │  │ SpamProtection  │              │
│  │UserRegistration │  │ SecurityService │  │ AccessControl   │              │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘              │
│           │                     │                     │                        │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐              │
│  │ Business Rules  │  │ Workflow        │  │ Data           │              │
│  │ Engine          │  │ Management      │  │ Validation     │              │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘              │
└─────────────────────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                             TIER 3: DATA TIER                                  │
│                              (Data Tier)                                       │
├─────────────────────────────────────────────────────────────────────────────────┤
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐              │
│  │   Database      │  │ Cache Layer  │  │   File Storage  │              │
│  │  (PostgreSQL)   │  │    (Redis)     │  │    (AWS S3)    │              │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘              │
│           │                     │                     │                        │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐              │
│  │ Data Access     │  │ Data Mapping    │  │ Transaction     │              │
│  │ Layer           │  │ & Persistence   │  │ Management      │              │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘              │
│           │                     │                     │                        │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐              │
│  │ UserRepository  │  │ MenuRepository  │  │ RestaurantRepo  │              │
│  │ FavoriteRepo    │  │ VerificationRepo│  │ SecurityRepo    │              │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘              │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 🔄 Data Flow Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              USER INTERACTION                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                           PRESENTATION TIER                                    │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐              │
│  │   Web Browser   │  │  Mobile App     │  │   API Client    │              │
│  │                 │  │                 │  │                 │              │
│  │ • User Input    │  │ • Touch Input   │  │ • HTTP Request  │              │
│  │ • Form Data     │  │ • Gestures      │  │ • JSON Data     │              │
│  │ • Validation    │  │ • Validation    │  │ • Authentication│              │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘              │
└─────────────────────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                          BUSINESS LOGIC TIER                                   │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐              │
│  │   Controllers   │  │    Services     │  │   Security      │              │
│  │                 │  │                 │  │                 │              │
│  │ • Process       │  │ • Business      │  │ • Authenticate  │              │
│  │   Requests      │  │   Rules          │  │ • Authorize     │              │
│  │ • Validate      │  │ • Workflow      │  │ • Audit         │              │
│  │   Data          │  │   Management     │  │ • Monitor       │              │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘              │
└─────────────────────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                             DATA TIER                                          │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐              │
│  │   Database      │  │     Cache       │  │  File Storage   │              │
│  │                 │  │                 │  │                 │              │
│  │ • CRUD Ops      │  │ • Fast Access   │  │ • Static Files  │              │
│  │ • Transactions  │  │ • Session Data  │  │ • Images        │              │
│  │ • Queries       │  │ • Temp Data     │  │ • Documents     │              │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘              │
└─────────────────────────────────────────────────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              RESPONSE FLOW                                     │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐              │
│  │   Data          │  │   Business      │  │   Presentation  │              │
│  │   Response      │  │   Processing    │  │   Response      │              │
│  │                 │  │                 │  │                 │              │
│  │ • Query Results  │  │ • Business      │  │ • HTML/JSON     │              │
│  │ • Data Objects  │  │   Logic          │  │ • UI Updates    │              │
│  │ • Status Info   │  │ • Validation     │  │ • Notifications │              │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘              │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## 🎯 Use Case Flow Through 3-Tier Architecture

### **UC-001: Browse Restaurant Menus**

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Web Browser   │───▶│ MenuBrowser     │───▶│ MenuController  │
│   (User clicks  │    │ Component       │    │                 │
│    "Browse")    │    │                 │    │ • Process       │
└─────────────────┘    └─────────────────┘    │   Request       │
                                │              │ • Validate      │
                                ▼              │   Input         │
┌─────────────────┐    ┌─────────────────┐    └─────────────────┘
│   MenuService   │◀───│ MenuController  │              │
│                 │    │                 │              ▼
│ • Search Logic  │    │ • Business      │    ┌─────────────────┐
│ • Filter Logic  │    │   Rules          │    │ MenuRepository   │
│ • Ranking Logic │    │ • Validation     │    │                 │
└─────────────────┘    └─────────────────┘    │ • Query Database│
                                │              │ • Return Data   │
                                ▼              └─────────────────┘
┌─────────────────┐    ┌─────────────────┐              │
│   Database      │◀───│ MenuRepository  │              ▼
│                 │    │                 │    ┌─────────────────┐
│ • Restaurants   │    │ • Data Mapping   │    │   Response      │
│ • Menus        │    │ • Query Builder  │    │                 │
│ • Menu Items   │    │ • Result Mapping │    │ • Menu Data     │
└─────────────────┘    └─────────────────┘    │ • Restaurant    │
                                │              │   Info          │
                                ▼              │ • Status        │
┌─────────────────┐    ┌─────────────────┐    └─────────────────┘
│   MenuBrowser   │◀───│ MenuService     │              │
│   Component     │    │                 │              ▼
│                 │    │ • Format Data   │    ┌─────────────────┐
│ • Display Menus │    │ • Apply Business│    │   Web Browser   │
│ • Show Results  │    │   Rules          │    │                 │
│ • Handle Events │    │ • Return Results│    │ • Display Menus │
└─────────────────┘    └─────────────────┘    │ • User Interface│
                                │              │ • Interactions  │
                                ▼              └─────────────────┘
┌─────────────────┐    ┌─────────────────┐
│   User Sees     │◀───│ MenuBrowser     │
│   Menu Results  │    │ Component       │
│                 │    │                 │
│ • Restaurant    │    │ • Rendered UI   │
│   List          │    │ • User Events   │
│ • Menu Items    │    │ • Interactions  │
│ • Search Results│    │                 │
└─────────────────┘    └─────────────────┘
```

---

## 🔒 Security Flow Through 3-Tier Architecture

### **Authentication & Authorization**

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Login Form    │───▶│ Authentication  │───▶│ SecurityService │
│   (User enters  │    │ Controller      │    │                 │
│    credentials) │    │                 │    │ • Validate      │
└─────────────────┘    └─────────────────┘    │   Credentials   │
                                │              │ • Generate      │
                                ▼              │   Token         │
┌─────────────────┐    ┌─────────────────┐    └─────────────────┘
│ UserRepository  │◀───│ SecurityService │              │
│                 │    │                 │              │
│ • Check User    │    │ • Hash Password │              ▼
│ • Verify Creds  │    │ • Compare Hash  │    ┌─────────────────┐
│ • Get User Data │    │ • Create Token  │    │   Database      │
└─────────────────┘    └─────────────────┘    │                 │
                                │              │ • User Table    │
                                ▼              │ • Session Table │
┌─────────────────┐    ┌─────────────────┐    │ • Security Logs │
│   Response      │◀───│ Authentication  │    └─────────────────┘
│                 │    │ Controller      │              │
│ • Success/Error │    │                 │              ▼
│ • Token/Session │    │ • Return Token  │    ┌─────────────────┐
│ • User Info     │    │ • Set Session   │    │   Response      │
└─────────────────┘    └─────────────────┘    │                 │
                                │              │ • Authentication│
                                ▼              │   Status        │
┌─────────────────┐    ┌─────────────────┐    │ • Session Token │
│   Web Browser   │◀───│ Login Form      │    │ • User Data     │
│                 │    │                 │    └─────────────────┘
│ • Store Token   │    │ • Handle        │              │
│ • Redirect User │    │   Response      │              ▼
│ • Update UI     │    │ • Show Success  │    ┌─────────────────┐
└─────────────────┘    └─────────────────┘    │   Web Browser   │
                                │              │                 │
                                ▼              │ • User Logged   │
┌─────────────────┐    ┌─────────────────┐    │   In            │
│   User Logged   │◀───│ Web Browser     │    │ • Dashboard     │
│   In Successfully│    │                 │    │   Available     │
│                 │    │ • Token Stored  │    │ • Menu Access   │
│ • Access Granted│    │ • Session Set   │    │                 │
│ • Dashboard     │    │ • UI Updated    │    └─────────────────┘
│   Available     │    │                 │
└─────────────────┘    └─────────────────┘
```

---

## 📊 Performance Metrics by Tier

### **Tier 1: Presentation Tier**
- **Response Time**: < 200ms for UI updates
- **Load Time**: < 3 seconds for initial page load
- **Caching**: Browser caching and CDN
- **Optimization**: Minification and compression

### **Tier 2: Business Logic Tier**
- **Processing Time**: < 500ms for business operations
- **Throughput**: 1000+ requests per second
- **Caching**: Application-level caching
- **Load Balancing**: Multiple application servers

### **Tier 3: Data Tier**
- **Query Time**: < 100ms for database queries
- **Connection Pool**: 100+ concurrent connections
- **Caching**: Redis caching for frequently accessed data
- **Backup**: Automated daily backups

---

## 🚀 Deployment Architecture

### **Tier Deployment Strategy**

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                           PRODUCTION ENVIRONMENT                                │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                 │
│  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐              │
│  │   Load Balancer │    │   Load Balancer │    │   Load Balancer │              │
│  │   (NGINX)       │    │   (NGINX)       │    │   (NGINX)       │              │
│  └─────────────────┘    └─────────────────┘    └─────────────────┘              │
│           │                       │                       │                      │
│  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐              │
│  │ Web Server 1    │    │ Web Server 2    │    │ Web Server 3    │              │
│  │ (Presentation)  │    │ (Presentation)  │    │ (Presentation)  │              │
│  └─────────────────┘    └─────────────────┘    └─────────────────┘              │
│           │                       │                       │                      │
│  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐              │
│  │ App Server 1      │    │ App Server 2      │    │ App Server 3      │              │
│  │ (Business Logic) │    │ (Business Logic) │    │ (Business Logic) │              │
│  └─────────────────┘    └─────────────────┘    └─────────────────┘              │
│           │                       │                       │                      │
│  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐              │
│  │ Database        │    │ Cache Server     │    │ File Storage    │              │
│  │ (PostgreSQL)    │    │ (Redis)          │    │ (AWS S3)        │              │
│  └─────────────────┘    └─────────────────┘    └─────────────────┘              │
│                                                                                 │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

*This 3-tier architecture diagram provides a comprehensive visual representation of MenuMap's software architecture, showing the clear separation of concerns and data flow between tiers.*
