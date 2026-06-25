# 🛡️ eSoc Study Tracker

**Goal:** SOC Analyst Level 1
**Started:** 23 - June - 2026
**Status:** 🔴 In Progress

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

## 🟦 Section 1 — Welcome

> - [x] [SOC Analyst Level 1 Overview](SOC%20Analyst%20Level%201%20Overview.md)
 

---

## 🟦 Section 2 — Foundations of SOC Operations

> ### 📂 01 — Introduction to the SOC
> #### 🔹 Security Operations Centers
> - [x] [01 - What is a SOC](01%20-%20What%20is%20a%20SOC.md) *(14m)*
> - [x] [02 - SOC Roles & Responsibilities](02%20-%20SOC%20Roles%20&%20Responsibilities.md) *(16m)*
> - [ ] [03 - SOC Operations](03%20-%20SOC%20Operations.md) *(15m)*
>
> #### 🔹 Guides & Frameworks
> - [ ] [04 - Cyber Kill Chain](04%20-%20Cyber%20Kill%20Chain.md) *(13m)*
> - [ ] [05 - NIST Cybersecurity Framework](05%20-%20NIST%20Cybersecurity%20Framework.md) *(8m)*
> - [ ] [06 - MITRE ATT&CK](06%20-%20MITRE%20ATT&CK.md) *(6m)*
>
> #### 🔹 Working in a SOC
> - [ ] [07 - SOC Tools & Technology](07%20-%20SOC%20Tools%20&%20Technology.md) *(19m)*
> - [ ] [08 - Introduction to DFIR](08%20-%20Introduction%20to%20DFIR.md) *(11m)*
> - [ ] [09 - SOC Maturity Levels](09%20-%20SOC%20Maturity%20Levels.md) *(9m)*

> ### 📂 02 — Core Skills for SOC Analysts
> #### 🔹 Cybersecurity Foundations
> - [ ] [01 - What is Information Security](01%20-%20What%20is%20Information%20Security.md) *(9m)*
> - [ ] [02 - Defense in Depth](02%20-%20Defense%20in%20Depth.md) *(17m)*
> - [ ] [03 - Common Threats & Attacks](03%20-%20Common%20Threats%20&%20Attacks.md) *(16m)*
> - [ ] [04 - Risk Concepts](04%20-%20Risk%20Concepts.md) *(6m)*
> - [ ] [05 - Security Controls](05%20-%20Security%20Controls.md) *(14m)*
>
> #### 🔹 Networking Fundamentals
> - [ ] [01 - Network Models (OSI & TCP-IP)](01%20-%20Network%20Models%20(OSI%20&%20TCP-IP).md) *(17m)*
> - [ ] [02 - Fundamentals of IP Addressing](02%20-%20Fundamentals%20of%20IP%20Addressing.md) *(15m)*
> - [ ] [03 - IPv4 Addressing](03%20-%20IPv4%20Addressing.md) *(23m)*
> - [ ] [04 - IPv6 Addressing](04%20-%20IPv6%20Addressing.md) *(18m)*
> - [ ] [05 - Common Protocols & Port Numbers](05%20-%20Common%20Protocols%20&%20Port%20Numbers.md) *(14m)*
> - [ ] [06 - Network Devices & Their Security Roles](06%20-%20Network%20Devices%20&%20Their%20Security%20Roles.md) *(19m)*
>
> #### 🔹 Windows Fundamentals
> - [ ] [01 - Windows Architecture & Components](01%20-%20Windows%20Architecture%20&%20Components.md) *(18m)*
> - [ ] [02 - Key System Locations & Files](02%20-%20Key%20System%20Locations%20&%20Files.md) *(11m)*
> - [ ] [03 - Fundamental Windows Management Tools](03%20-%20Fundamental%20Windows%20Management%20Tools.md) *(8m)*
> - [ ] [04 - Event Viewer & Windows Security Logs](04%20-%20Event%20Viewer%20&%20Windows%20Security%20Logs.md) *(7m)*
> - [ ] [05 - Windows User & Permissions Basics](05%20-%20Windows%20User%20&%20Permissions%20Basics.md) *(13m)*
> - [ ] [06 - Active Directory Basics](06%20-%20Active%20Directory%20Basics.md) *(9m)*
> - [ ] [07 - Windows Command Line Essentials](07%20-%20Windows%20Command%20Line%20Essentials.md) *(17m)*
>
> #### 🔹 Linux Fundamentals
> - [ ] [01 - Linux Architecture](01%20-%20Linux%20Architecture.md) *(19m)*
> - [ ] [02 - Users Groups & File Permissions](02%20-%20Users%20Groups%20&%20File%20Permissions.md) *(15m)*
> - [ ] [03 - Linux Command Line Essentials](03%20-%20Linux%20Command%20Line%20Essentials.md) *(17m)*
> - [ ] [04 - Linux Processes & Services](04%20-%20Linux%20Processes%20&%20Services.md) *(12m)*
> - [ ] [05 - Linux Networking & Remote Access](05%20-%20Linux%20Networking%20&%20Remote%20Access.md) *(12m)*
>
> #### 🔹 The Analyst Mindset
> - [ ] [01 - Thinking Like an Analyst](01%20-%20Thinking%20Like%20an%20Analyst.md) *(20m)*
> - [ ] [02 - Pattern Recognition](02%20-%20Pattern%20Recognition.md) *(16m)*
> - [ ] [03 - Avoiding Analytical Bias](03%20-%20Avoiding%20Analytical%20Bias.md) *(7m)*
> - [ ] [04 - Staying Current in Cybersecurity](04%20-%20Staying%20Current%20in%20Cybersecurity.md) *(10m)*
>
> #### 🔹 Compliance Ethics & Legal
> - [ ] [01 - Introduction to Compliance & Legal Responsibilities](01%20-%20Introduction%20to%20Compliance%20&%20Legal%20Responsibilities.md) *(11m)*
> - [ ] [02 - Privacy](02%20-%20Privacy.md) *(10m)*
> - [ ] [03 - Data Handling & Evidence Preservation](03%20-%20Data%20Handling%20&%20Evidence%20Preservation.md) *(14m)*

> ### 📂 03 — SOC Tools & Technology
> #### 🔹 SOC Foundations
> - [ ] [01 - The Evolution of Security Operations Centers](01%20-%20The%20Evolution%20of%20Security%20Operations%20Centers.md) *(22m)*
> - [ ] [02 - Modern Threat Landscape and Tool Requirements](02%20-%20Modern%20Threat%20Landscape%20and%20Tool%20Requirements.md) *(14m)*
> - [ ] [03 - Tool Categories Detection Analysis Response Intelligence](03%20-%20Tool%20Categories%20Detection%20Analysis%20Response%20Intelligence.md) *(14m)*
> - [ ] [04 - The SOC Analyst Role and Daily Tool Interactions](04%20-%20The%20SOC%20Analyst%20Role%20and%20Daily%20Tool%20Interactions.md) *(17m)*
>
> #### 🔹 Tool Architecture & Core SOC Platforms
> - [ ] [01 - Understanding Tool Integration and Data Flow](01%20-%20Understanding%20Tool%20Integration%20and%20Data%20Flow.md) *(30m)*
> - [ ] [02 - Endpoint Detection and Response (EDR)](02%20-%20Endpoint%20Detection%20and%20Response%20(EDR).md) *(25m)*
> - [ ] [03 - SIEM Overview](03%20-%20SIEM%20Overview.md) *(31m)*
> - [ ] [04 - SIEM Rules](04%20-%20SIEM%20Rules.md) *(19m)*
> - [ ] [05 - SOAR](05%20-%20SOAR.md) *(20m)*
> - [ ] [06 - Playbooks](06%20-%20Playbooks.md) *(23m)*
>
> #### 🔹 Threat Intelligence & Analysis
> - [ ] [01 - Threat Intelligence and IoC Enrichment](01%20-%20Threat%20Intelligence%20and%20IoC%20Enrichment.md) *(27m)*
> - [ ] [02 - Threat Intelligence and Types of IoCs Overview](02%20-%20Threat%20Intelligence%20and%20Types%20of%20IoCs%20Overview.md) *(17m)*
> - [ ] [03 - Threat Intelligence and Types of IoCs Demonstration](03%20-%20Threat%20Intelligence%20and%20Types%20of%20IoCs%20Demonstration.md) *(24m)*
> - [ ] [04 - Advanced Analysis Tools](04%20-%20Advanced%20Analysis%20Tools.md) *(33m)*
>
> #### 🔹 SOC Workflows & Scenarios
> - [ ] [01 - The Complete Toolkit Workflow](01%20-%20The%20Complete%20Toolkit%20Workflow.md) *(32m)*
> - [ ] [02 - Scenario Suspicious Login](02%20-%20Scenario%20Suspicious%20Login.md) *(21m)*
> - [ ] [03 - Scenario Ransomware](03%20-%20Scenario%20Ransomware.md) *(23m)*
> - [ ] [04 - Ethical Use of SOC Tools](04%20-%20Ethical%20Use%20of%20SOC%20Tools.md) *(20m)*
> - [ ] [05 - Build your SOC Analyst Toolkit](05%20-%20Build%20your%20SOC%20Analyst%20Toolkit.md) *(9m)*

---

## 🟦 Section 3 — SOC Analyst Operations

> ### 📂 01 — SOC Logging & Analysis
> #### 🔹 Introduction to Logging
> - [ ] [01 - Logging Introduction](01%20-%20Logging%20Introduction.md) *(7m)*
> - [ ] [02 - Log Sources & Types](02%20-%20Log%20Sources%20&%20Types.md) *(10m)*
> - [ ] [03 - Windows Event Logging](03%20-%20Windows%20Event%20Logging.md) *(8m)*
> - [ ] [04 - Linux Logging](04%20-%20Linux%20Logging.md) *(12m)*
>
> #### 🔹 The Logging Lifecycle
> - [ ] [01 - Logging Lifecycle](01%20-%20Logging%20Lifecycle.md) *(7m)*
> - [ ] [02 - Log Collection](02%20-%20Log%20Collection.md) *(8m)*
> - [ ] [03 - Log Shipping](03%20-%20Log%20Shipping.md) *(5m)*
> - [ ] [04 - Log Aggregation](04%20-%20Log%20Aggregation.md) *(8m)*
> - [ ] [05 - Log Collection & Aggregation with Splunk](05%20-%20Log%20Collection%20&%20Aggregation%20with%20Splunk.md) *(21m)*
>
> #### 🔹 Log Analysis
> - [ ] [01 - Basic Log Interpretation & Analysis](01%20-%20Basic%20Log%20Interpretation%20&%20Analysis.md) *(9m)*
> - [ ] [02 - Log Analysis Tools](02%20-%20Log%20Analysis%20Tools.md) *(8m)*
>
> #### 🔹 SIEM Fundamentals
> - [ ] [01 - Introduction to SIEM](01%20-%20Introduction%20to%20SIEM.md) *(18m)*
> - [ ] [02 - Dashboards & Visualizations](02%20-%20Dashboards%20&%20Visualizations.md) *(6m)*
> - [ ] [03 - Effectively Using ELK](03%20-%20Effectively%20Using%20ELK.md) *(25m)*
> - [ ] [04 - Events Alerts & Incidents](Section%203%20-%20SOC%20Operations/01%20-%20SOC%20Logging%20&%20Analysis/04%20-%20SIEM%20Fundamentals/04%20-%20Events%20Alerts%20&%20Incidents.md) *(10m)*
> - [ ] [05 - Alert Fatigue](05%20-%20Alert%20Fatigue.md) *(7m)*
> - [ ] [06 - Logging & Analysis Challenges](06%20-%20Logging%20&%20Analysis%20Challenges.md) *(12m)*

> ### 📂 02 — Incident Detection & Response
> #### 🔹 IR Fundamentals
> - [ ] [01 - What is Incident Response](01%20-%20What%20is%20Incident%20Response.md) *(5m)*
> - [ ] [02 - Incident Response Teams](02%20-%20Incident%20Response%20Teams.md) *(11m)*
> - [ ] [03 - Incident Response Process](03%20-%20Incident%20Response%20Process.md) *(14m)*
> - [ ] [04 - Events Alerts & Incidentss](Section%203%20-%20SOC%20Operations/02%20-%20Incident%20Detection%20&%20Response/01%20-%20IR%20Fundamentals/04%20-%20Events%20Alerts%20&%20Incidentss.md)
>
> #### 🔹 Detecting Incidents
> - [ ] [01 - Detecting Suspicious Activity](01%20-%20Detecting%20Suspicious%20Activity.md) *(12m)*
> - [ ] [02 - Phishing & Email Compromise](02%20-%20Phishing%20&%20Email%20Compromise.md) *(13m)*
> - [ ] [03 - Credential & Account Attacks](03%20-%20Credential%20&%20Account%20Attacks.md) *(11m)*
> - [ ] [04 - Malware & Endpoint Compromise](04%20-%20Malware%20&%20Endpoint%20Compromise.md) *(8m)*
> - [ ] [05 - Network Intrusions](05%20-%20Network%20Intrusions.md) *(12m)*
>
> #### 🔹 Incident Response
> - [ ] [01 - Contextualizing & Validating Alerts](01%20-%20Contextualizing%20&%20Validating%20Alerts.md) *(11m)*
> - [ ] [02 - Triaging Alerts](02%20-%20Triaging%20Alerts.md) *(9m)*
> - [ ] [03 - Incident Response Playbooks](03%20-%20Incident%20Response%20Playbooks.md) *(12m)*
> - [ ] [04 - Documentation & Reporting for Incident Response](04%20-%20Documentation%20&%20Reporting%20for%20Incident%20Response.md) *(14m)*
> - [ ] [05 - Tier 1 Incident Workflow](05%20-%20Tier%201%20Incident%20Workflow.md) *(11m)*

> ### 📂 03 — SOC Ticketing & Reporting
> #### 🔹 Ticketing Basics
> - [ ] [01 - Ticketing in the SOC](01%20-%20Ticketing%20in%20the%20SOC.md) *(12m)*
> - [ ] [02 - Anatomy of a SOC Ticket](02%20-%20Anatomy%20of%20a%20SOC%20Ticket.md) *(11m)*
> - [ ] [03 - Common Ticketing Solutions](03%20-%20Common%20Ticketing%20Solutions.md) *(5m)*
>
> #### 🔹 Working with Tickets
> - [ ] [01 - SOC Ticket Lifecycle](01%20-%20SOC%20Ticket%20Lifecycle.md) *(5m)*
> - [ ] [02 - Writing Quality Tickets](02%20-%20Writing%20Quality%20Tickets.md) *(8m)*
> - [ ] [03 - SOC Ticket Metadata](03%20-%20SOC%20Ticket%20Metadata.md) *(7m)*
>
> #### 🔹 Workflows and Documentation
> - [ ] [01 - SOC Ticket Escalation](01%20-%20SOC%20Ticket%20Escalation.md) *(12m)*
> - [ ] [02 - Collaborative Documentation](02%20-%20Collaborative%20Documentation.md) *(7m)*
> - [ ] [03 - Writing an Incident Report](03%20-%20Writing%20an%20Incident%20Report.md) *(8m)*
> - [ ] [04 - Soft Skills for the SOC](04%20-%20Soft%20Skills%20for%20the%20SOC.md) *(33m)*

> ### 📂 04 — Intelligence in Threat Hunting
> #### 🔹 Foundations of Cyber Threat Intelligence
> - [ ] [01 - The Role of Threat Intelligence in Cyber Defense](01%20-%20The%20Role%20of%20Threat%20Intelligence%20in%20Cyber%20Defense.md) *(8m)*
> - [ ] [02 - Strategic Operational Tactical & Technical Intelligence](02%20-%20Strategic%20Operational%20Tactical%20&%20Technical%20Intelligence.md) *(7m)*
> - [ ] [03 - Intelligence Lifecycle from Planning to Dissemination](03%20-%20Intelligence%20Lifecycle%20from%20Planning%20to%20Dissemination.md) *(9m)*
> - [ ] [04 - Applying the Intelligence Cycle in Real-World Operations](04%20-%20Applying%20the%20Intelligence%20Cycle%20in%20Real-World%20Operations.md) *(11m)*
>
> #### 🔹 Adversary Analysis & Detection
> - [ ] [01 - Using MITRE ATT&CK for Adversary Analysis](01%20-%20Using%20MITRE%20ATT&CK%20for%20Adversary%20Analysis.md) *(10m)*
> - [ ] [02 - Correlating IoCs Across Sources](02%20-%20Correlating%20IoCs%20Across%20Sources.md) *(9m)*
> - [ ] [03 - Integrating CTI into SIEMs & Detection Pipelines](03%20-%20Integrating%20CTI%20into%20SIEMs%20&%20Detection%20Pipelines.md) *(10m)*
> - [ ] [04 - IOC Enrichment & Contextualization](04%20-%20IOC%20Enrichment%20&%20Contextualization.md) *(8m)*
>
> #### 🔹 Threat Hunting Methodologies
> - [ ] [01 - Intelligence-Driven Threat Hunting Methodologies](01%20-%20Intelligence-Driven%20Threat%20Hunting%20Methodologies.md) *(9m)*
> - [ ] [02 - OSINT Commercial Feeds & Closed Sources](02%20-%20OSINT%20Commercial%20Feeds%20&%20Closed%20Sources.md) *(7m)*
> - [ ] [03 - STIX TAXII & the Traffic Light Protocol](03%20-%20STIX%20TAXII%20&%20the%20Traffic%20Light%20Protocol.md) *(6m)*
> - [ ] [04 - Structured Analytical Techniques for CTI](04%20-%20Structured%20Analytical%20Techniques%20for%20CTI.md) *(11m)*
>
> #### 🔹 Collaboration & Information Sharing
> - [ ] [01 - Sector ISACs Government Partnerships & Info Sharing Protocols](01%20-%20Sector%20ISACs%20Government%20Partnerships%20&%20Info%20Sharing%20Protocols.md) *(6m)*
> - [ ] [02 - Real-World CTI Applications](02%20-%20Real-World%20CTI%20Applications.md) *(13m)*

> ### 📂 05 — Malware Analysis
> #### 🔹 Introduction to Malware
> - [ ] [01 - What is Malware](01%20-%20What%20is%20Malware.md) *(14m)*
> - [ ] [02 - Malware Categories](02%20-%20Malware%20Categories.md) *(34m)*
> - [ ] [03 - Attacker Motivations](03%20-%20Attacker%20Motivations.md) *(17m)*
> - [ ] [04 - Malware Delivery](04%20-%20Malware%20Delivery.md) *(19m)*
> - [ ] [05 - Malware Execution](05%20-%20Malware%20Execution.md) *(27m)*
> - [ ] [06 - Malware Execution LOLbin DLL](06%20-%20Malware%20Execution%20LOLbin%20DLL.md) *(8m)*
> - [ ] [07 - Malware Persistence](07%20-%20Malware%20Persistence.md) *(21m)*
> - [ ] [08 - The SOC Analyst Role](08%20-%20The%20SOC%20Analyst%20Role.md) *(23m)*
>
> #### 🔹 MITRE ATTCK
> - [ ] [01 - MITRE ATTCK Framework](01%20-%20MITRE%20ATTCK%20Framework.md) *(14m)*
> - [ ] [02 - MITRE ATTCK Framework ATTCK Navigator](02%20-%20MITRE%20ATTCK%20Framework%20ATTCK%20Navigator.md) *(9m)*
>
> #### 🔹 Host Based Artifacts
> - [ ] [01 - Host Based Artifacts](01%20-%20Host%20Based%20Artifacts.md) *(20m)*
> - [ ] [02 - Host Based Artifacts Process Explorer](02%20-%20Host%20Based%20Artifacts%20Process%20Explorer.md) *(6m)*
> - [ ] [03 - Host Based Artifacts File System Artifacts](03%20-%20Host%20Based%20Artifacts%20File%20System%20Artifacts.md) *(15m)*
> - [ ] [04 - Host Based Artifacts Registry Artifacts](04%20-%20Host%20Based%20Artifacts%20Registry%20Artifacts.md) *(7m)*
>
> #### 🔹 Network Based Indicators
> - [ ] [01 - Network Based Indicators](01%20-%20Network%20Based%20Indicators.md) *(28m)*
> - [ ] [02 - Network Based Indicators Network Anomalies](02%20-%20Network%20Based%20Indicators%20Network%20Anomalies.md) *(15m)*
> - [ ] [03 - Hashing and File Identification](03%20-%20Hashing%20and%20File%20Identification.md) *(11m)*
> - [ ] [04 - Hashing and File Identification Demo](04%20-%20Hashing%20and%20File%20Identification%20Demo.md) *(10m)*
>
> #### 🔹 Extracting IOCs
> - [ ] [01 - Extracting IOCs from Files](01%20-%20Extracting%20IOCs%20from%20Files.md) *(17m)*
> - [ ] [02 - Extracting IOC Demo](02%20-%20Extracting%20IOC%20Demo.md) *(12m)*
>
> #### 🔹 Dynamic Analysis
> - [ ] [01 - Dynamic Analysis Foundations](01%20-%20Dynamic%20Analysis%20Foundations.md) *(10m)*
> - [ ] [02 - Dynamic Analysis Environment Safety](02%20-%20Dynamic%20Analysis%20Environment%20Safety.md) *(9m)*
> - [ ] [03 - Dynamic Analysis Demo](03%20-%20Dynamic%20Analysis%20Demo.md) *(11m)*

> ### 📂 06 — Phishing Mail Analysis
> #### 🔹 Phishing Fundamentals
> - [ ] [01 - Phishing Fundamentals](01%20-%20Phishing%20Fundamentals.md) *(14m)*
> - [ ] [02 - Types of Phishing Attacks](02%20-%20Types%20of%20Phishing%20Attacks.md) *(29m)*
> - [ ] [03 - Phishing Kill Chain](03%20-%20Phishing%20Kill%20Chain.md) *(33m)*
>
> #### 🔹 Analysis
> - [ ] [01 - Header Analysis](01%20-%20Header%20Analysis.md) *(27m)*
> - [ ] [02 - Header Analysis Demo](02%20-%20Header%20Analysis%20Demo.md) *(8m)*
> - [ ] [03 - Mail Content Analysis](03%20-%20Mail%20Content%20Analysis.md) *(9m)*
> - [ ] [04 - URL Analysis](04%20-%20URL%20Analysis.md) *(21m)*
>
> #### 🔹 Response
> - [ ] [01 - Phishing Response](01%20-%20Phishing%20Response.md) *(30m)*

> ### 📂 07 — AI in the SOC
> #### 🔹 What is AI & Why it Matters
> - [ ] [01 - What Is Artificial Intelligence](01%20-%20What%20Is%20Artificial%20Intelligence.md) *(8m)*
> - [ ] [02 - AI vs Machine Learning vs Automation](02%20-%20AI%20vs%20Machine%20Learning%20vs%20Automation.md) *(10m)*
> - [ ] [03 - How AI Is Used in Modern SOCs](03%20-%20How%20AI%20Is%20Used%20in%20Modern%20SOCs.md) *(7m)*
>
> #### 🔹 Key AI Terminology
> - [ ] [01 - Common AI & ML Terms You'll See in SOC Tools](01%20-%20Common%20AI%20&%20ML%20Terms%20You'll%20See%20in%20SOC%20Tools.md) *(16m)*
> - [ ] [02 - Understanding Anomaly Detection at a High Level](02%20-%20Understanding%20Anomaly%20Detection%20at%20a%20High%20Level.md) *(8m)*
>
> #### 🔹 AI in SIEM Platforms
> - [ ] [01 - How SIEMs Use AI for Alerting & Correlation](01%20-%20How%20SIEMs%20Use%20AI%20for%20Alerting%20&%20Correlation.md) *(12m)*
>
> #### 🔹 AI in EDR & Endpoint Tools
> - [ ] [01 - How EDR Uses AI to Detect Malicious Behavior](01%20-%20How%20EDR%20Uses%20AI%20to%20Detect%20Malicious%20Behavior.md) *(7m)*
> - [ ] [02 - Interpreting AI-Generated Alerts & Risk Scores](02%20-%20Interpreting%20AI-Generated%20Alerts%20&%20Risk%20Scores.md) *(6m)*
>
> #### 🔹 Generative AI Basics
> - [ ] [01 - What Generative AI Is & How SOCs Use It](01%20-%20What%20Generative%20AI%20Is%20&%20How%20SOCs%20Use%20It.md) *(7m)*
>
> #### 🔹 Prompting for SOC Tasks
> - [ ] [01 - Writing Effective Prompts for Alert Triage](01%20-%20Writing%20Effective%20Prompts%20for%20Alert%20Triage.md) *(13m)*
> - [ ] [02 - Using GenAI to Assist Investigations](02%20-%20Using%20GenAI%20to%20Assist%20Investigations.md) *(13m)*
> - [ ] [03 - Using GenAI for Reporting & Documentation](03%20-%20Using%20GenAI%20for%20Reporting%20&%20Documentation.md) *(12m)*
>
> #### 🔹 Limitations & Risks of AI
> - [ ] [01 - AI Bias False Positives & Analyst Oversight](01%20-%20AI%20Bias%20False%20Positives%20&%20Analyst%20Oversight.md) *(10m)*
>
> #### 🔹 Custom AI in SOCs
> - [ ] [01 - How Custom ML Models Are Used in SOCs](01%20-%20How%20Custom%20ML%20Models%20Are%20Used%20in%20SOCs.md) *(9m)*

---

## 🟦 Section 4 — Goodbye

> - [ ] [SOC Analyst Level 1 Summary](SOC%20Analyst%20Level%201%20Summary)

---

## ⏱️ Total Hours
| Section | Hours |
|---------|-------|
| Section 2 — Foundations | ~28h |
| Section 3 — SOC Operations | ~58h |
| **Total** | **~86 hours** |