
## Cyber Kill Chain

![](Attachments/Pasted%20image%2020260625063408.png)

Think of it as a domino effect: **Step 1 makes Step 2 possible, Step 2 leads to Step 3,** and so on.

### **Step 1: Reconnaissance (The Scouting)**

![](Attachments/Pasted%20image%2020260625064917.png)

- **What happens:** The attacker searches for a way in. They find an unpatched vulnerability or an employee's email address.
    
- 👇 _Because they found a specific target vulnerability..._
    

### **Step 2: Weaponization (The Making)**

![](Attachments/Pasted%20image%2020260625065029.png)

- **What happens:** The attacker builds a custom trap. They pair a piece of malware with an exploit that specifically fits the vulnerability found in Step 1.
    
- 👇 _Now that the trap is ready..._
    

### **Step 3: Delivery (The Shipping)**

![](Attachments/Pasted%20image%2020260625065221.png)


- **What happens:** The attacker sends the trap to the target. This is usually done via a phishing email, a bad link, or a malicious attachment.
    
- 👇 _Once the victim receives the trap and interacts with it..._
    

### **Step 4: Exploitation (The Triggering)**

![](Attachments/Pasted%20image%2020260625065437.png)

- **What happens:** The trap snaps shut. The malicious code executes by taking advantage of the system's weakness or user error.
    
- 👇 _Once the system is breached..._
    

### **Step 5: Installation (The Digging In)**

![](Attachments/04%20-%20Cyber%20Kill%20Chain.png)

- **What happens:** The attacker plants a permanent backdoor. They install software that ensures they don't lose access, even if the system reboots.
    
- 👇 _Now that they have a permanent foothold..._
    

### **Step 6: Command & Control (The Connecting)**

![](Attachments/Pasted%20image%2020260625065759.png)

- **What happens:** The planted backdoor opens a secret communication line. The infected system calls home to the attacker’s remote server, waiting for orders.
    
- 👇 _Now that the attacker has full remote control..._
    

### **Step 7: Actions on Objectives (The Stealing)**

- **What happens:** The attacker finally completes their mission. They steal the data, encrypt the files for ransom, or destroy the systems.
    

### 🧠 **The Quick Memory Build:**

1. **Scout** the target $\rightarrow$
    
2. **Make** the trap $\rightarrow$
    
3. **Ship** the trap $\rightarrow$
    
4. **Trigger** the trap $\rightarrow$
    
5. **Dig** a tunnel $\rightarrow$
    
6. **Connect** the radio $\rightarrow$
    
7. **Steal** the goods.
---


## Why SOC Analyst Need to learn Cyber Kill Chain ?

📌 **What it is:** The Cyber Kill Chain is a step-by-step framework that tracks the typical stages of a cyberattack, from the initial planning phase all the way to data theft. It helps defenders understand the exact sequence of actions an attacker must take to succeed.

🎯 **Why SOC Analysts use it:**

- It allows analysts to pinpoint exactly how far an attacker has penetrated the network during an active incident.
    
- It helps teams set up security controls at every stage to stop, slow down, or detect the attack before it reaches the final phase.
    
- It provides a standard, step-by-step language for analysts to map out alerts and explain attacks clearly to management.
    

🌍 **Real-World Example:** An attacker sends a phishing email with a malicious PDF link to a company accountant (Delivery). The accountant clicks it, and a hidden malware file downloads onto their laptop (Installation). A SOC analyst catches the alert at the installation stage and immediately isolates the laptop, breaking the kill chain before the attacker can steal any financial data.

⚡ **Key Takeaway:** By understanding every step of an attack, a SOC analyst can disrupt the chain at any point to completely defeat the threat.

---
