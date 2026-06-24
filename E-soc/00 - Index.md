# eSoc Study Tracker

**Goal:** SOC Analyst Level 1  
**Started:** 23 - June - 2026 
**Status:** 🔴 In Progress

---

## Section 1 - Welcome
- [ ] SOC Analyst Level 1 Overview

---

## Section 2 - Foundations of SOC Operations
- [ ] 01 - Introduction to the SOC *(3h 35m)*
- [ ] 02 - Core Skills for SOC Analysts *(13h 40m)*
- [ ] 03 - SOC Tools & Technology *(11h 32m)*

---

## Section 3 - SOC Analyst Operations
- [ ] 01 - SOC Logging & Analysis *(8h 38m)*
- [ ] 02 - Incident Detection & Response *(6h 1m)*
- [ ] 03 - SOC Ticketing & Reporting *(6h 8m)*
- [ ] 04 - Intelligence in Threat Hunting *(5h 5m)*
- [ ] 05 - Malware Analysis *(12h 6m)*
- [ ] 06 - Phishing Mail Analysis *(4h 54m)*
- [ ] 07 - AI in the SOC *(5h 18m)*

---

## Section 4 - Goodbye
- [ ] SOC Analyst Level 1 Summary

---

## 📊 Auto Progress Tracker

```dataview
TABLE
  length(filter(rows.task, (t) => t.completed)) as "✅ Done",
  length(filter(rows.task, (t) => !t.completed)) as "⏳ Remaining",
  length(rows.task) as "📚 Total"
FROM "E-soc"
FLATTEN file.tasks as task
WHERE task.text != ""
GROUP BY file.folder
```

---
