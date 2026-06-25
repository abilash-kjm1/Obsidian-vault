![](Attachments/Pasted%20image%2020260624213305.png)

- **Tier 1 (Triage):** The front-line watchers who monitor security alerts, filter out the false alarms, and pass real threats up the chain.

- **Tier 2 (Responder):** The deep-dive investigators who step in to figure out how a real attack happened and actively work to stop it.

- **Tier 3 (Hunter/Expert):** The advanced pros who proactively hunt for hidden, sneaky threats and handle the most complex, high-level security emergencies.


![](Attachments/Pasted%20image%2020260624214623.png)


**Tier 1 Analyst** does, following their step-by-step workflow:

- **Step 1: Monitor (First Line of Defense)** They constantly watch security dashboards and alerts (like SIEM systems) to spot any unusual activity.

- **Step 2: Triage (Sort the Alerts)** They do an initial check on incoming alerts to figure out if a threat is real (legitimate) or just a false alarm (false positive).

- **Step 3: Resolve & Document (Close Simple Issues)** They close out the simple stuff—like known safe events or false alarms—and write down their findings so there is a clear record.

![](Attachments/Pasted%20image%2020260624215735.png)



> [!NOTE] What is Triage
> **triage** means **sorting and prioritizing incoming security alerts** to figure out which ones are real threats and which ones are false alarms.

Think of it like a hospital emergency room: instead of treating patients in the exact order they arrive, a nurse checks everyone quickly to treat the most critical injuries first.

In a SOC, a Tier 1 analyst performs this initial triage:

1. **Separates the noise:** They check if an alert is a _false positive_ (a harmless glitch/normal activity) or a _true positive_ (an actual security issue).

2. **Assigns priority:** They decide how dangerous the real threat is so the team knows what to fix first.

3. **Escalates:** If it's a serious, real attack, they pass it up to Tier 2 investigators to handle.

--- 

![](Attachments/Pasted%20image%2020260624215130.png)
![](Attachments/Pasted%20image%2020260624215546.png)

- **Investigates Escalated Alerts:** They look at the alerts sent up by Tier 1 to confirm if a real security incident is actually happening.

- **In-Depth Analysis:** They dig deep into the data to figure out the full scope of the attack and exactly what systems or data are impacted.

- **Response Actions:** They take immediate, necessary actions to stop the attack and begin the remediation (fixing/healing) process.

- **Coordination with IT Staff:** They collaborate closely with the broader IT team to completely resolve the incident and collect extra information about what happened.

---

![](Attachments/Pasted%20image%2020260624220219.png)

 
 Their responsibilities include:

- **Handling the Hardest Attacks:** They are the senior security experts called upon to manage the most advanced or confusing security incidents.

- **Hunting for Hidden Threats:** As Threat Hunters, they proactively search for potential attacks that have already bypassed existing security tools and _did not_ trigger any initial alerts.

- **Digging Deep to Find the "Why":** They perform complete forensic analysis to investigate an incident's "root cause"—basically, they determine _exactly_ how the attacker got in and what they did.

- **Making the SOC Stronger:** Their expertise is used to improve the entire SOC's capabilities. They do this by:

    - Developing new "use cases" (new methods to find attackers).
    
    - "Tuning" security controls (making firewalls and alerts more precise).
    
    - Mentoring and training junior analysts.

![](Attachments/Pasted%20image%2020260624220553.png)

- **The Entry Points:** Tier 3 workflow begins in one of two ways:
    
    - **Proactive Path (Threat Hunting):** Instead of waiting for an alert, they create a hypothesis (a theory on where a sneaky attacker might hide) and search the network for hidden dangers.
    
    - **Reactive Path (Forensics):** A highly complex, advanced incident is escalated to them from Tier 2.
    
- **The Investigation Phase:**
    
    - They pull deep data logs and perform **deep digital forensics** to uncover the **Root Cause** (figuring out _exactly_ how the attacker slipped in).
    
- **The Advanced Response:**
    
    - They take precise actions to neutralize sophisticated threats that standard automated tools cannot handle.
    
- **The Feedback Loop (Improving the SOC):**
    
    - This is what makes Tier 3 unique. Once the issue is resolved, they use their findings to make the entire SOC smarter. They create new **Use Cases** (rules to spot this attack automatically next time), **Tune Security Controls** to block it, and **Mentor** Tier 1 and Tier 2 analysts to raise the whole team's skill level.