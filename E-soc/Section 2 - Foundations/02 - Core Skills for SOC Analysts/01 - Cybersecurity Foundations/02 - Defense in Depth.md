![](Attachments/02%20-%20Defense%20in%20Depth.png)

**Defense in Depth (Layered Security)**

Defense in depth, also known as layered security, is the practice of implementing several layers of protection to secure an organization's assets. The core philosophy is that security should not rely on a single action or mechanism; if one layer fails, additional layers still provide protection.

**Key elements include:**

- **Diversity in security measures:** Vendor diversity, technology diversity, and control diversity.
- **Examples:** Host-based and network-based firewalls, system hardening, multi-layer malware protection, and secure network configuration (e.g., changing the default SSID).

Ultimately, defense in depth creates a resilient security posture where attackers must overcome multiple, diverse obstacles to reach their target.





Here's a **clean, exam-friendly visual note** that matches the concept in your image while keeping the textbook language.

---

# 🛡️ Defense in Depth – Core Layers!

[![](Attachments/02%20-%20Defense%20in%20Depth-1.png)


> **Defense in Depth (Layered Security)** is the practice of implementing several layers of protection so that if one layer fails, additional layers remain in place to provide protection.


|**Core Layer**|**Purpose / Security Measures**|
|---|---|
|**1. Physical**|Protects physical assets and facilities using **locks, fences, CCTV, security guards, lighting, and secure server rooms**.|
|**2. Perimeter**|Protects the organization's boundary using **network firewalls, gateways, proxy servers, IDS/IPS, and email security**.|
|**3. Network**|Protects internal network communication through **network segmentation, secure protocols, firewalls, and network monitoring**.|
|**4. Endpoint**|Protects workstations, laptops, servers, and mobile devices using **host-based firewalls, antivirus, anti-malware, system hardening, and patch management**.|
|**5. Application**|Protects software applications through **secure configuration, authentication, authorization, vulnerability management, and regular updates**.|
|**6. Data**|Protects sensitive information using **encryption, access control, backups, and data loss prevention (DLP)**.|
|**7. Identity**|Ensures only authorized users can access resources using **strong passwords, multi-factor authentication (MFA), identity management, and least privilege**.|
|**8. Monitoring & Response**|Continuously detects and responds to threats using **logging, SIEM, IDS/IPS, security monitoring, and incident response**.|

![](Attachments/02%20-%20Defense%20in%20Depth-2.png)

## Examples

![](Attachments/02%20-%20Defense%20in%20Depth-3.png)
Phishing Email
      │
      ▼
Email Gateway ❌ (Missed the email)
      │
      ▼
User ❌ (Clicked the malicious link)
      │
      ▼
Endpoint Security ✅ (Detects suspicious activity)
      │
      ▼
Identity System ✅ (Detects abnormal login / MFA)
      │
      ▼
SIEM & SOC ✅ (Investigates and responds)


| **Layer**                              | **What Happens in the Phishing Attack**                                                                                        | **Defense in Depth Concept**                                                                      |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------- |
| **Email Gateway**                      | The phishing email is **not detected** and reaches the user's inbox.                                                           | The **first layer fails**, but the attack is not yet successful.                                  |
| **User (Human Layer)**                 | The user clicks the malicious link.                                                                                            | Another layer fails because of **human error**. Defense in depth assumes users can make mistakes. |
| **Endpoint Security**                  | Antivirus/EDR detects suspicious activity and raises an alert.                                                                 | A **third layer** detects the attack after execution begins.                                      |
| **Identity System**                    | The attacker attempts to log in, but abnormal login behavior is detected and **MFA** or other identity controls are triggered. | The **Identity layer** prevents or limits unauthorized access.                                    |
| **SIEM & SOC (Monitoring & Response)** | Alerts from different systems are correlated, and the Security Operations Center investigates and responds.                    | The **Monitoring & Response layer** contains the attack and reduces its impact.                   |