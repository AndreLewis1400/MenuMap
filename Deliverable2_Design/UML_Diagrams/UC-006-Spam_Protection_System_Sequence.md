# UC-006: Spam Protection System - Sequence Diagram
## MenuMap Application - Team 9

**Use Case:** UC-006: Spam Protection System  
**Complexity:** High  
**Priority:** Security and content quality  

---

## 🎯 **Lifelines (Participants)**

```
User | Administrator | WebInterface | SpamProtection | Database | Alert
```

---

## 📋 **Message Flow (Step by Step)**

### **Phase 1: Content Submission and Analysis**
```
1. User -> WebInterface: submit content (review, menu item)
2. WebInterface -> SpamProtection: analyzeContent(content)
3. SpamProtection -> SpamProtection: checkSpamPatterns()
4. SpamProtection -> SpamProtection: validateContentQuality()
5. SpamProtection -> SpamProtection: checkRateLimits(userID)
6. SpamProtection -> WebInterface: return analysisResult
```

### **Phase 2: Alternative Flows Based on Analysis**
```
alt Content is Clean
    WebInterface -> Database: saveContent(content)
    Database -> WebInterface: return success
    WebInterface -> User: display "Content published"

else Content is Spam
    WebInterface -> Alert: createAlert(content, userID)
    Alert -> WebInterface: return alertID
    WebInterface -> User: display "Content blocked"
    WebInterface -> Administrator: notify administrator
end
```

### **Phase 3: Administrator Review and Action**
```
7. Administrator -> WebInterface: review spam alerts
8. WebInterface -> SpamProtection: getSpamAlerts()
9. SpamProtection -> Database: getAlerts(status)
10. Database -> SpamProtection: return alertsList
11. SpamProtection -> WebInterface: return alerts
12. WebInterface -> Administrator: display alerts

13. Administrator -> WebInterface: take action (block user, approve content)
14. WebInterface -> SpamProtection: processAlert(alertID, action)
15. SpamProtection -> Alert: updateAlertStatus(alertID, action)
16. Alert -> SpamProtection: return success
17. SpamProtection -> WebInterface: return confirmation
18. WebInterface -> Administrator: display "Action completed"
```

---

## 🔄 **Alternative Flows (Alt Frames)**

### **Alt Frame 1: Rate Limit Exceeded**
```
alt Rate Limit Exceeded
    SpamProtection -> WebInterface: return rateLimitExceeded
    WebInterface -> User: display "Rate limit exceeded"
```

### **Alt Frame 2: No Alerts Found**
```
alt No Alerts Found
    Database -> SpamProtection: return emptyList
    SpamProtection -> WebInterface: return noAlerts
    WebInterface -> Administrator: display "No alerts found"
```

### **Alt Frame 3: Action Processing Failed**
```
alt Action Processing Failed
    Alert -> SpamProtection: return processingError
    SpamProtection -> WebInterface: return actionFailed
    WebInterface -> Administrator: display "Action failed"
```

---

## 🎨 **Visual Layout in Papyrus**

### **Lifeline Order (Left to Right):**
```
User | Administrator | WebInterface | SpamProtection | Database | Alert
```

### **Message Types:**
- **Solid Arrow**: Synchronous calls
- **Dashed Arrow**: Return messages
- **Self Arrow**: Internal method calls (steps 3-5)

### **Activation Boxes:**
- **WebInterface**: Steps 1-2, 6, 7-8, 12-14, 18
- **SpamProtection**: Steps 2-5, 8-11, 14-17
- **Database**: Steps 7-8, 9-10
- **Alert**: Steps 7-8, 15-16

---

## ✅ **Validation Checklist**

- [ ] All 6 lifelines created
- [ ] 18 main flow messages added
- [ ] 3 alternative flows (alt frames) included
- [ ] Self messages for internal calls
- [ ] Activation boxes showing method execution
- [ ] Return messages as dashed arrows
- [ ] Professional formatting applied
- [ ] No syntax errors in validation

---

*This sequence diagram provides detailed interaction flow for UC-006: Spam Protection System use case.*
