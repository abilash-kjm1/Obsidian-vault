
![](Attachments/Pasted%20image%2020260627220528.png)



## 🛠️ The Ultimate SOC Tools & Technologies Cheat Sheet

### 1. Central Core & Automation

- **SIEM (Security Information & Event Management):** Aggregates and normalizes millions of raw text logs from across the entire enterprise into a single dashboard to correlate patterns and trigger real-time threat alerts.
    ![](Attachments/07%20-%20SOC%20Tools%20&%20Technology.png)
    
- **SOAR (Security Orchestration, Automation, and Response):** Executes pre-built automated **playbooks** to instantly handle repetitive security tasks—like blocking a malicious IP address or isolating an account—without human intervention.
    

### 2. Network Security Monitoring (NSM)

- **Firewalls:** Acts as the network's perimeter security gate, inspecting incoming and outgoing traffic to permit or block data based on defined security rules.
    
- **IDS (Intrusion Detection System):** Passively monitors network traffic packets to detect and log suspicious activity or known attack signatures, acting as an alarm system.
    
- **IPS (Intrusion Prevention System):** Sits directly in the traffic path to actively detect _and_ block malicious network packets in real time before they reach their target.
    
- **Packet Analyzers (e.g., Wireshark):** Allows analysts to intercept and perform deep-dive, microscopic inspections of raw data packets moving across the network wires.
    ![](Attachments/Pasted%20image%2020260627222315.png)


### 3. Host & Cloud Telemetry

- **EDR / XDR (Endpoint Detection & Response):** Monitors real-time behavioral activity directly on host devices (laptops, servers), tracking process execution trees and giving analysts the ability to remotely isolate a compromised machine.
    
- **System Logs (e.g., Windows Event Logs / Linux Syslog):** The operating system's raw, built-in digital diary that chronologically records every internal event, such as successful or failed user login attempts.
    
- **Cloud Service Logs (e.g., AWS CloudTrail / Azure Activity):** Specialized data streams that audit cloud infrastructure environments for identity access management modifications, unauthorized access, or configuration changes.
    
- **Threat Intelligence Feeds:** Global "Most Wanted" databases that continuously stream known Indicators of Compromise (IoCs)—like malicious file hashes and bad IP addresses—directly into SOC tools to flag active threats.
    ![](Attachments/Pasted%20image%2020260627222456.png)

![](Attachments/Pasted%20image%2020260627222631.png)


### 🧠 Quick Metacognitive Tip for Interviews

> When asked about the SOC stack in an interview, group your answer into **Visibility** (SIEM, Logs, Wireshark), **Detection/Control** (EDR, IDS/IPS, Firewalls), and **Response** (SOAR playbooks). It shows you understand how the technologies actually collaborate!
