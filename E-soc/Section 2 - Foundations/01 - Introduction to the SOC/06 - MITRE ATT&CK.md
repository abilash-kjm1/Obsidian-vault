
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
