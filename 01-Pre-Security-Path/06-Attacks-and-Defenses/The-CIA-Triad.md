## 🛡️ The CIA Triad & Core Terminology

The **CIA Triad** is the core foundation of cybersecurity. It defines the three primary pillars required to protect digital data and assets from attacks, unauthorised access, or disruption.

---

### 🏛️ The Three Pillars

* **Confidentiality:** 
  * **Concept:** Ensures sensitive data can only be accessed or read by authorized individuals.
  * **Violations:** Data leaks, credentials written on sticky notes, or login interception over open Wi-Fi networks.
  * **Protections:** Encryption, strict access controls, and multi-factor authentication.

* **Integrity:** 
  * **Concept:** Ensures data is accurate, trustworthy, and cannot be modified or tampered with without permission.
  * **Violations:** Intercepting and altering bank transaction details, or unauthorised grade/record changes.
  * **Protections:** Hashing, digital signatures, and strict input validation/sanitisation.

* **Availability:** 
  * **Concept:** Ensures data, systems, and services remain accessible to authorised users whenever needed.
  * **Violations:** Distributed Denial of Service (DDoS) attacks crashing a site, power failures, or system disruption caused by bad updates.
  * **Protections:** Load balancing, redundant power sources, firewalls/WAFs with rate-limiting, and regular backups.

---

### 📊 Real-World Scenario Matrix

| Scenario | CIA Pillar Affected | Outcome |
| :--- | :--- | :--- |
| **Credentials on sticky notes / Intercepted logins** | Confidentiality | **Breached** (Unauthorized access) |
| **Approved data change by an administrator** | Integrity | **Achieved** (Authorized modification) |
| **Checkout order price modified before payment** | Integrity | **Breached** (Unauthorized tampering) |
| **Website goes offline during business hours** | Availability | **Breached** (Service disruption) |
| **All systems accessible during working hours** | Availability | **Achieved** (Normal operations) |

---

## 🛡️ Security & Forensics Perspective

Understanding how the CIA Triad applies to incident response and digital forensics enables security analysts to quickly categorize threats, assess damage, and preserve evidence during a breach:

* **Forensic Evidence & Data Confidentiality:** When a confidentiality breach occurs (e.g., unauthorized data exfiltration), forensic investigators analyze network packet captures (PCAPs), server access logs, and DLP (Data Loss Prevention) alerts. The objective is to identify precisely what sensitive data was exposed, determine the entry vector, and confirm whether encrypted channels were bypassed or unencrypted protocols were exploited.
* **Tamper Evident Forensics & Data Integrity:** Digital forensics relies heavily on data integrity to ensure that evidence remains admissible in court. Analysts generate cryptographic hashes (such as SHA-256) for drive images and forensic log files immediately upon collection. Any unauthorized modification—whether by an attacker altering audit trails or an investigator mishandling evidence—invalidates the chain of custody.
* **Availability Incident Post-Mortems:** When evaluating Denial of Service (DoS/DDoS) attacks, system crashes, or ransomware outbreaks that disrupt services, incident responders focus on availability recovery. Forensics teams analyze log timestamps, bandwidth consumption spikes, and system resource exhaustion to trace the source of the outage and re-establish normal operations safely.
* **Impact Assessment via Threat Modeling:** Security operations centers (SOCs) use the CIA Triad as a scoring matrix to prioritize alerts. Incidents affecting all three pillars simultaneously—such as a ransomware attack that exfiltrates data (Confidentiality), encrypts/corrupts files (Integrity), and locks systems (Availability)—are classified at the highest severity level.
