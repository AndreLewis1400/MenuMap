# UC-005: Menu Verification System - Sequence Diagram
## MenuMap Application - Team 9

**Use Case:** UC-005: Menu Verification System  
**Complexity:** High  
**Priority:** Content quality assurance  

---

## 🎯 **Lifelines (Participants)**

```
Restaurant Owner | Administrator | WebInterface | MenuController | VerificationSystem | Database | Report
```

---

## 📋 **Message Flow (Step by Step)**

### **Phase 1: Menu Submission**
```
1. Restaurant Owner -> WebInterface: submit menu for verification
2. WebInterface -> MenuController: submitMenuForVerification(menuData)
3. MenuController -> VerificationSystem: verifyMenu(menuData)
4. VerificationSystem -> VerificationSystem: validateMenuItems()
5. VerificationSystem -> VerificationSystem: checkPricingConsistency()
6. VerificationSystem -> VerificationSystem: detectDuplicates()

7. VerificationSystem -> Database: saveVerificationReport(menuID, report)
8. Database -> VerificationSystem: return reportID
9. VerificationSystem -> MenuController: return verificationResult
10. MenuController -> WebInterface: return verificationStatus
11. WebInterface -> Restaurant Owner: display verification results
```

### **Phase 2: Administrator Review**
```
12. Administrator -> WebInterface: review verification reports
13. WebInterface -> MenuController: getVerificationReports()
14. MenuController -> Database: getReports(status)
15. Database -> MenuController: return reportsList
16. MenuController -> WebInterface: return reports
17. WebInterface -> Administrator: display reports

18. Administrator -> WebInterface: approve/reject menu
19. WebInterface -> MenuController: updateMenuStatus(menuID, status)
20. MenuController -> Database: updateMenuStatus(menuID, status)
21. Database -> MenuController: return success
22. MenuController -> WebInterface: return confirmation
23. WebInterface -> Administrator: display "Status updated"
```

---

## 🔄 **Alternative Flows (Alt Frames)**

### **Alt Frame 1: Menu Validation Failed**
```
alt Menu Validation Failed
    VerificationSystem -> MenuController: return validationFailed
    MenuController -> WebInterface: return validationErrors
    WebInterface -> Restaurant Owner: display "Menu validation failed"
```

### **Alt Frame 2: No Reports Found**
```
alt No Reports Found
    Database -> MenuController: return emptyList
    MenuController -> WebInterface: return noReports
    WebInterface -> Administrator: display "No reports found"
```

### **Alt Frame 3: Status Update Failed**
```
alt Status Update Failed
    Database -> MenuController: return updateError
    MenuController -> WebInterface: return updateFailed
    WebInterface -> Administrator: display "Status update failed"
```

---

## 🎨 **Visual Layout in Papyrus**

### **Lifeline Order (Left to Right):**
```
Restaurant Owner | Administrator | WebInterface | MenuController | VerificationSystem | Database | Report
```

### **Message Types:**
- **Solid Arrow**: Synchronous calls
- **Dashed Arrow**: Return messages
- **Self Arrow**: Internal method calls (steps 4-6)

### **Activation Boxes:**
- **WebInterface**: Steps 1-2, 11-13, 17-19, 23
- **MenuController**: Steps 2-3, 9-10, 13-16, 19-22
- **VerificationSystem**: Steps 3-9
- **Database**: Steps 7-8, 14-15, 20-21

---

## ✅ **Validation Checklist**

- [ ] All 7 lifelines created
- [ ] 23 main flow messages added
- [ ] 3 alternative flows (alt frames) included
- [ ] Self messages for internal calls
- [ ] Activation boxes showing method execution
- [ ] Return messages as dashed arrows
- [ ] Professional formatting applied
- [ ] No syntax errors in validation

---

*This sequence diagram provides detailed interaction flow for UC-005: Menu Verification System use case.*
