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

> - [x] [[SOC Analyst Level 1 Overview]]

---

## 🟦 Section 2 — Foundations of SOC Operations

> ### 📂 01 — Introduction to the SOC
> #### 🔹 Security Operations Centers
> - [ ] [[01 - What is a SOC]] *(14m)*
> - [ ] [[02 - SOC Roles & Responsibilities]] *(16m)*
> - [ ] [[03 - SOC Operations]] *(15m)*
>
> #### 🔹 Guides & Frameworks
> - [ ] [[04 - Cyber Kill Chain]] *(13m)*
> - [ ] [[05 - NIST Cybersecurity Framework]] *(8m)*
> - [ ] [[06 - MITRE ATT&CK]] *(6m)*
>
> #### 🔹 Working in a SOC
> - [ ] [[07 - SOC Tools & Technology]] *(19m)*
> - [ ] [[08 - Introduction to DFIR]] *(11m)*
> - [ ] [[09 - SOC Maturity Levels]] *(9m)*

> ### 📂 02 — Core Skills for SOC Analysts
> #### 🔹 Cybersecurity Foundations
> - [ ] [[01 - What is Information Security]] *(9m)*
> - [ ] [[02 - Defense in Depth]] *(17m)*
> - [ ] [[03 - Common Threats & Attacks]] *(16m)*
> - [ ] [[04 - Risk Concepts]] *(6m)*
> - [ ] [[05 - Security Controls]] *(14m)*
>
> #### 🔹 Networking Fundamentals
> - [ ] [[01 - Network Models (OSI & TCP-IP)]] *(17m)*
> - [ ] [[02 - Fundamentals of IP Addressing]] *(15m)*
> - [ ] [[03 - IPv4 Addressing]] *(23m)*
> - [ ] [[04 - IPv6 Addressing]] *(18m)*
> - [ ] [[05 - Common Protocols & Port Numbers]] *(14m)*
> - [ ] [[06 - Network Devices & Their Security Roles]] *(19m)*
>
> #### 🔹 Windows Fundamentals
> - [ ] [[01 - Windows Architecture & Components]] *(18m)*
> - [ ] [[02 - Key System Locations & Files]] *(11m)*
> - [ ] [[03 - Fundamental Windows Management Tools]] *(8m)*
> - [ ] [[04 - Event Viewer & Windows Security Logs]] *(7m)*
> - [ ] [[05 - Windows User & Permissions Basics]] *(13m)*
> - [ ] [[06 - Active Directory Basics]] *(9m)*
> - [ ] [[07 - Windows Command Line Essentials]] *(17m)*
>
> #### 🔹 Linux Fundamentals
> - [ ] [[01 - Linux Architecture]] *(19m)*
> - [ ] [[02 - Users Groups & File Permissions]] *(15m)*
> - [ ] [[03 - Linux Command Line Essentials]] *(17m)*
> - [ ] [[04 - Linux Processes & Services]] *(12m)*
> - [ ] [[05 - Linux Networking & Remote Access]] *(12m)*
>
> #### 🔹 The Analyst Mindset
> - [ ] [[01 - Thinking Like an Analyst]] *(20m)*
> - [ ] [[02 - Pattern Recognition]] *(16m)*
> - [ ] [[03 - Avoiding Analytical Bias]] *(7m)*
> - [ ] [[04 - Staying Current in Cybersecurity]] *(10m)*
>
> #### 🔹 Compliance Ethics & Legal
> - [ ] [[01 - Introduction to Compliance & Legal Responsibilities]] *(11m)*
> - [ ] [[02 - Privacy]] *(10m)*
> - [ ] [[03 - Data Handling & Evidence Preservation]] *(14m)*

> ### 📂 03 — SOC Tools & Technology
> #### 🔹 SOC Foundations
> - [ ] [[01 - The Evolution of Security Operations Centers]] *(22m)*
> - [ ] [[02 - Modern Threat Landscape and Tool Requirements]] *(14m)*
> - [ ] [[03 - Tool Categories Detection Analysis Response Intelligence]] *(14m)*
> - [ ] [[04 - The SOC Analyst Role and Daily Tool Interactions]] *(17m)*
>
> #### 🔹 Tool Architecture & Core SOC Platforms
> - [ ] [[01 - Understanding Tool Integration and Data Flow]] *(30m)*
> - [ ] [[02 - Endpoint Detection and Response (EDR)]] *(25m)*
> - [ ] [[03 - SIEM Overview]] *(31m)*
> - [ ] [[04 - SIEM Rules]] *(19m)*
> - [ ] [[05 - SOAR]] *(20m)*
> - [ ] [[06 - Playbooks]] *(23m)*
>
> #### 🔹 Threat Intelligence & Analysis
> - [ ] [[01 - Threat Intelligence and IoC Enrichment]] *(27m)*
> - [ ] [[02 - Threat Intelligence and Types of IoCs Overview]] *(17m)*
> - [ ] [[03 - Threat Intelligence and Types of IoCs Demonstration]] *(24m)*
> - [ ] [[04 - Advanced Analysis Tools]] *(33m)*
>
> #### 🔹 SOC Workflows & Scenarios
> - [ ] [[01 - The Complete Toolkit Workflow]] *(32m)*
> - [ ] [[02 - Scenario Suspicious Login]] *(21m)*
> - [ ] [[03 - Scenario Ransomware]] *(23m)*
> - [ ] [[04 - Ethical Use of SOC Tools]] *(20m)*
> - [ ] [[05 - Build your SOC Analyst Toolkit]] *(9m)*

---

## 🟦 Section 3 — SOC Analyst Operations

> ### 📂 01 — SOC Logging & Analysis
> #### 🔹 Introduction to Logging
> - [ ] [[01 - Logging Introduction]] *(7m)*
> - [ ] [[02 - Log Sources & Types]] *(10m)*
> - [ ] [[03 - Windows Event Logging]] *(8m)*
> - [ ] [[04 - Linux Logging]] *(12m)*
>
> #### 🔹 The Logging Lifecycle
> - [ ] [[01 - Logging Lifecycle]] *(7m)*
> - [ ] [[02 - Log Collection]] *(8m)*
> - [ ] [[03 - Log Shipping]] *(5m)*
> - [ ] [[04 - Log Aggregation]] *(8m)*
> - [ ] [[05 - Log Collection & Aggregation with Splunk]] *(21m)*
>
> #### 🔹 Log Analysis
> - [ ] [[01 - Basic Log Interpretation & Analysis]] *(9m)*
> - [ ] [[02 - Log Analysis Tools]] *(8m)*
>
> #### 🔹 SIEM Fundamentals
> - [ ] [[01 - Introduction to SIEM]] *(18m)*
> - [ ] [[02 - Dashboards & Visualizations]] *(6m)*
> - [ ] [[03 - Effectively Using ELK]] *(25m)*
> - [ ] [[04 - Events Alerts & Incidents]] *(10m)*
> - [ ] [[05 - Alert Fatigue]] *(7m)*
> - [ ] [[06 - Logging & Analysis Challenges]] *(12m)*

> ### 📂 02 — Incident Detection & Response
> #### 🔹 IR Fundamentals
> - [ ] [[01 - What is Incident Response]] *(5m)*
> - [ ] [[02 - Incident Response Teams]] *(11m)*
> - [ ] [[03 - Incident Response Process]] *(14m)*
> - [ ] [[04 - Events Alerts & Incidents]] *(12m)*
>
> #### 🔹 Detecting Incidents
> - [ ] [[01 - Detecting Suspicious Activity]] *(12m)*
> - [ ] [[02 - Phishing & Email Compromise]] *(13m)*
> - [ ] [[03 - Credential & Account Attacks]] *(11m)*
> - [ ] [[04 - Malware & Endpoint Compromise]] *(8m)*
> - [ ] [[05 - Network Intrusions]] *(12m)*
>
> #### 🔹 Incident Response
> - [ ] [[01 - Contextualizing & Validating Alerts]] *(11m)*
> - [ ] [[02 - Triaging Alerts]] *(9m)*
> - [ ] [[03 - Incident Response Playbooks]] *(12m)*
> - [ ] [[04 - Documentation & Reporting for Incident Response]] *(14m)*
> - [ ] [[05 - Tier 1 Incident Workflow]] *(11m)*

> ### 📂 03 — SOC Ticketing & Reporting
> #### 🔹 Ticketing Basics
> - [ ] [[01 - Ticketing in the SOC]] *(12m)*
> - [ ] [[02 - Anatomy of a SOC Ticket]] *(11m)*
> - [ ] [[03 - Common Ticketing Solutions]] *(5m)*
>
> #### 🔹 Working with Tickets
> - [ ] [[01 - SOC Ticket Lifecycle]] *(5m)*
> - [ ] [[02 - Writing Quality Tickets]] *(8m)*
> - [ ] [[03 - SOC Ticket Metadata]] *(7m)*
>
> #### 🔹 Workflows and Documentation
> - [ ] [[01 - SOC Ticket Escalation]] *(12m)*
> - [ ] [[02 - Collaborative Documentation]] *(7m)*
> - [ ] [[03 - Writing an Incident Report]] *(8m)*
> - [ ] [[04 - Soft Skills for the SOC]] *(33m)*

> ### 📂 04 — Intelligence in Threat Hunting
> #### 🔹 Foundations of Cyber Threat Intelligence
> - [ ] [[01 - The Role of Threat Intelligence in Cyber Defense]] *(8m)*
> - [ ] [[02 - Strategic Operational Tactical & Technical Intelligence]] *(7m)*
> - [ ] [[03 - Intelligence Lifecycle from Planning to Dissemination]] *(9m)*
> - [ ] [[04 - Applying the Intelligence Cycle in Real-World Operations]] *(11m)*
>
> #### 🔹 Adversary Analysis & Detection
> - [ ] [[01 - Using MITRE ATT&CK for Adversary Analysis]] *(10m)*
> - [ ] [[02 - Correlating IoCs Across Sources]] *(9m)*
> - [ ] [[03 - Integrating CTI into SIEMs & Detection Pipelines]] *(10m)*
> - [ ] [[04 - IOC Enrichment & Contextualization]] *(8m)*
>
> #### 🔹 Threat Hunting Methodologies
> - [ ] [[01 - Intelligence-Driven Threat Hunting Methodologies]] *(9m)*
> - [ ] [[02 - OSINT Commercial Feeds & Closed Sources]] *(7m)*
> - [ ] [[03 - STIX TAXII & the Traffic Light Protocol]] *(6m)*
> - [ ] [[04 - Structured Analytical Techniques for CTI]] *(11m)*
>
> #### 🔹 Collaboration & Information Sharing
> - [ ] [[01 - Sector ISACs Government Partnerships & Info Sharing Protocols]] *(6m)*
> - [ ] [[02 - Real-World CTI Applications]] *(13m)*

> ### 📂 05 — Malware Analysis
> #### 🔹 Introduction to Malware
> - [ ] [[01 - What is Malware]] *(14m)*
> - [ ] [[02 - Malware Categories]] *(34m)*
> - [ ] [[03 - Attacker Motivations]] *(17m)*
> - [ ] [[04 - Malware Delivery]] *(19m)*
> - [ ] [[05 - Malware Execution]] *(27m)*
> - [ ] [[06 - Malware Execution LOLbin DLL]] *(8m)*
> - [ ] [[07 - Malware Persistence]] *(21m)*
> - [ ] [[08 - The SOC Analyst Role]] *(23m)*
>
> #### 🔹 MITRE ATTCK
> - [ ] [[01 - MITRE ATTCK Framework]] *(14m)*
> - [ ] [[02 - MITRE ATTCK Framework ATTCK Navigator]] *(9m)*
>
> #### 🔹 Host Based Artifacts
> - [ ] [[01 - Host Based Artifacts]] *(20m)*
> - [ ] [[02 - Host Based Artifacts Process Explorer]] *(6m)*
> - [ ] [[03 - Host Based Artifacts File System Artifacts]] *(15m)*
> - [ ] [[04 - Host Based Artifacts Registry Artifacts]] *(7m)*
>
> #### 🔹 Network Based Indicators
> - [ ] [[01 - Network Based Indicators]] *(28m)*
> - [ ] [[02 - Network Based Indicators Network Anomalies]] *(15m)*
> - [ ] [[03 - Hashing and File Identification]] *(11m)*
> - [ ] [[04 - Hashing and File Identification Demo]] *(10m)*
>
> #### 🔹 Extracting IOCs
> - [ ] [[01 - Extracting IOCs from Files]] *(17m)*
> - [ ] [[02 - Extracting IOC Demo]] *(12m)*
>
> #### 🔹 Dynamic Analysis
> - [ ] [[01 - Dynamic Analysis Foundations]] *(10m)*
> - [ ] [[02 - Dynamic Analysis Environment Safety]] *(9m)*
> - [ ] [[03 - Dynamic Analysis Demo]] *(11m)*

> ### 📂 06 — Phishing Mail Analysis
> #### 🔹 Phishing Fundamentals
> - [ ] [[01 - Phishing Fundamentals]] *(14m)*
> - [ ] [[02 - Types of Phishing Attacks]] *(29m)*
> - [ ] [[03 - Phishing Kill Chain]] *(33m)*
>
> #### 🔹 Analysis
> - [ ] [[01 - Header Analysis]] *(27m)*
> - [ ] [[02 - Header Analysis Demo]] *(8m)*
> - [ ] [[03 - Mail Content Analysis]] *(9m)*
> - [ ] [[04 - URL Analysis]] *(21m)*
>
> #### 🔹 Response
> - [ ] [[01 - Phishing Response]] *(30m)*

> ### 📂 07 — AI in the SOC
> #### 🔹 What is AI & Why it Matters
> - [ ] [[01 - What Is Artificial Intelligence]] *(8m)*
> - [ ] [[02 - AI vs Machine Learning vs Automation]] *(10m)*
> - [ ] [[03 - How AI Is Used in Modern SOCs]] *(7m)*
>
> #### 🔹 Key AI Terminology
> - [ ] [[01 - Common AI & ML Terms You'll See in SOC Tools]] *(16m)*
> - [ ] [[02 - Understanding Anomaly Detection at a High Level]] *(8m)*
>
> #### 🔹 AI in SIEM Platforms
> - [ ] [[01 - How SIEMs Use AI for Alerting & Correlation]] *(12m)*
>
> #### 🔹 AI in EDR & Endpoint Tools
> - [ ] [[01 - How EDR Uses AI to Detect Malicious Behavior]] *(7m)*
> - [ ] [[02 - Interpreting AI-Generated Alerts & Risk Scores]] *(6m)*
>
> #### 🔹 Generative AI Basics
> - [ ] [[01 - What Generative AI Is & How SOCs Use It]] *(7m)*
>
> #### 🔹 Prompting for SOC Tasks
> - [ ] [[01 - Writing Effective Prompts for Alert Triage]] *(13m)*
> - [ ] [[02 - Using GenAI to Assist Investigations]] *(13m)*
> - [ ] [[03 - Using GenAI for Reporting & Documentation]] *(12m)*
>
> #### 🔹 Limitations & Risks of AI
> - [ ] [[01 - AI Bias False Positives & Analyst Oversight]] *(10m)*
>
> #### 🔹 Custom AI in SOCs
> - [ ] [[01 - How Custom ML Models Are Used in SOCs]] *(9m)*

---

## 🟦 Section 4 — Goodbye

> - [ ] [[SOC Analyst Level 1 Summary]]

---

## ⏱️ Total Hours
| Section | Hours |
|---------|-------|
| Section 2 — Foundations | ~28h |
| Section 3 — SOC Operations | ~58h |
| **Total** | **~86 hours** |