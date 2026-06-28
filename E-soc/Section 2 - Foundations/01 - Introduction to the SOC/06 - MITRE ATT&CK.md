
# 📝 My Cheat Sheet: MITRE ATT&CK for a SOC L1

## 🎯 What is it?

It is a giant encyclopedia of **every trick hackers use**. You use it every day to figure out what a weird alert means and what the hacker is going to do next.

## 🧩 The 2 Words You MUST Know

1. **TACTIC (The "Why"):** What is the hacker's goal right now?
    
    - _Examples:_ Breaking in, stealing passwords, hiding from the antivirus, or deleting backups.
    
2. **TECHNIQUE (The "How"):** How did they achieve that goal?
    
    - _Examples:_ Sending a fake email, using a PowerShell script, or making a fake admin account.


## 🏃‍♂️ My Daily 3-Step Workflow

### Step 1: Translate the Alert 🌐

- **The Problem:** The SIEM gives you a weird alert like _"LSASS Memory Dump."_ You have no idea what that means.

- **The Fix:** Go to the MITRE website and search it. It will tell you: _"This means the hacker is trying to steal passwords from the computer's memory (Technique T1003)."_ Now you know what you are dealing with.


### Step 2: Predict the Future (Look Left & Right) 🔮

Hackers don't just do one thing. They follow a path.

- **Look Left (How did they get here?):** If you catch them running a virus, think: _"How did this file get on the PC?"_ Look at the "Initial Access" column on MITRE to remind yourself to check email logs or web history.

- **Look Right (What are they doing next?):** If they are on the computer, look at the next columns on MITRE (like "Persistence"). Ask yourself: _"Did they leave a back door open so they can log back in tomorrow?"_ Go check the logs for that!


### Step 3: Sound Like a Pro when Escalating 🚀

Don't write sloppy notes when passing a ticket to Tier 2. Use MITRE names to sound like an expert.

- **Bad Note:** _"The user did something weird with a command prompt."_

- **Pro Note:** _"Confirmed Technique T1059 (Command and Scripting Interpreter). Escalating for further review."_


## 🧠 The 3 Frameworks (The Quick Reminder)

- **Cyber Kill Chain:** _The Timeline._ Tells you **how close the hacker is to winning** so you know the priority.

- **MITRE ATT&CK:** _The Clues._ Tells you **exactly what they did** and what logs to check next.

- **NIST CSF:** _The Rules._ The company's guide on **how to build** the security team and policies.

![697](Attachments/Pasted%20image%2020260627202908.png)

# 🛡️ THE PROFESSIONAL SOC ANALYST CHEAT SHEET: MITRE ATT&CK

## ⚡ Core Concepts

- **MITRE ATT&CK Matrix:** A globally standardized encyclopedia mapping real-world adversary behavior.
    
- **The Blueprint ID (e.g., `T1059.001`):** A universal barcode. Every SIEM, EDR, and security team globally uses these identical IDs to eliminate language barriers.
    

```
TACTIC (The Goal) ──> TECHNIQUE (The Action) ──> SUB-TECHNIQUE (The Specific Tool)
[Execution]            [Command Interpreter]      [.001: PowerShell]
```

## 📊 Anatomy of a Technique Page

|**Component**|**Professional Definition**|**Quick Translation**|**Practical SOC Use Case**|
|---|---|---|---|
|**Tactic**|Adversarial tactical objective.|**The "Why"**|Determines triage priority and phase of breach.|
|**Technique**|The method executed to achieve an objective.|**The "How"**|Identifies the general nature of the malicious alert.|
|**Sub-Technique**|Granular sub-category of a technique.|**The Exact Tool**|Directs you to the exact software/language used.|
|**Procedure**|Historical, real-world implementation by threat actors.|**The History**|Provides context on known threat group behaviors (TTPs).|
|**Mitigation**|Hardening steps to prevent the technique from succeeding.|**The Shield**|Used to verify if defensive configurations failed.|
|**Detection**|Specific data sources and telemetry required to observe behavior.|**The Clues**|**Your Holy Grail:** Names the exact log IDs needed to query.|

## 💻 Shift Execution Workflow (3-Step Blueprint)

### 1. Alert Enrichment (Triage)

- **Action:** SIEM triggers an abstract alert (`lsass.exe memory read`).
    
- **Execution:** Query `lsass` on the ATT&CK framework. Map it to **T1003 (Credential Dumping)**.
    
- **Outcome:** You instantly identify the intent: _The adversary is attempting to harvest plain-text passwords from memory._
    

### 2. Analytical Pivoting (Scoping)

- **Action:** You confirm a malicious script ran via PowerShell (**T1059.001**).
    
- **Execution:** Navigate to the **Detection** section of the T1059.001 page. It dictates analyzing process creation logs.
    
- **Outcome:** You target your SIEM query to **Windows Event ID 4688** or **Sysmon Event ID 1** to extract the raw command line string executed by the attacker.
    

### 3. Professional Escalation (Handoff)

- **Action:** Documenting findings to escalate to Tier 2/Incident Response.
    
- **Execution:** Replace descriptive prose with framework terminology.
    
- **Outcome:**
    
    - ❌ _Incorrect:_ "The user ran a bad script and it looks like a hacker tried to steal passwords."
        
    - ✅ _Professional:_ "Alert validated. Observed execution of **T1059.001 (PowerShell)** leading to **T1003.001 (LSASS Memory)** on Host-01. Escalating for immediate containment."
        

## 🧠 Framework Matrix Correlation

- **NIST CSF:** _Strategic Governance._ Controls **how to build** and evaluate the security architecture.
    
- **Cyber Kill Chain:** _Chronological Timeline._ Tracks **how close** the adversary is to their final objective. Dictates **Severity/Priority**.
    
- **MITRE ATT&CK:** _Technical Telemetry._ Explains **exactly what** actions occurred and **which logs** hold the evidence. Dictates **Analysis/Hunting**.