## 🛡️ SOC Incident Handling – Phishing Alert (Event ID 257)

As part of a simulated **Security Operations Centre (SOC)** environment on the LetsDefend platform, I investigated and responded to a phishing incident triggered by **SOC282 – Phishing Alert: Deceptive Mail Detected** :contentReference[oaicite:0]{index=0}.

---

### 📌 Incident Overview
- **Event ID:** 257  
- **Alert Type:** Phishing – deceptive email containing a malicious link and attachment  
- **Target User:** Internal mailbox (simulated user)  
- **Email Subject:** *Free Coffee Voucher*  
- **Delivery Status:** Allowed and delivered  
- **Threat Outcome:** Malicious payload executed with outbound C2 communication observed  

---

### 🔍 Investigation & Analysis
Following the SOC playbook, I began by parsing email metadata to establish context and assess risk:
- Identified the **sender address**, **SMTP IP**, **recipient**, and **delivery timestamp**
- Observed **social engineering indicators** such as urgency language (“Hurry”, “Offer expires soon”)
- Detected a suspicious **URL and ZIP attachment** embedded in the email

Further analysis was conducted using third-party tools:
- **VirusTotal**: Multiple engines flagged the URL as malicious
- **ANY.RUN sandbox**: Confirmed the attachment executed a malicious **AsyncRAT variant**
- Analysis showed the phishing page imitated a legitimate login interface, increasing the likelihood of user compromise

---

### 🚨 Host & Network Investigation
- Verified the email was **opened by the user**
- Confirmed execution of the payload (`coffee.exe`) on the host
- Observed outbound **command-and-control (C2)** communication via proxy and endpoint logs
- Correlated browser, process, and network activity to build a clear attack timeline

---

### 🧯 Incident Response & Containment
- Deleted the malicious email from the user mailbox to prevent reinfection
- **Isolated the affected host** using endpoint security controls
- Documented indicators of compromise (IOC) and user impact
- Recommended credential resets and user awareness actions as part of remediation

---

### 🧠 Lessons Learned
- Phishing emails can closely mimic legitimate communications and rely on urgency to drive execution
- Email security controls must be complemented by **user awareness training**
- Early detection and rapid containment are critical to limiting post-exploitation impact

---

### 🗂️ Frameworks & Skills Demonstrated
- **Incident Response lifecycle:** Detection → Analysis → Containment → Lessons Learned  
- **MITRE ATT&CK Mapping:**  
  - Initial Access – Phishing (T1566)  
  - Execution – User Execution / Command & Scripting Interpreter  
  - Discovery – Account & System Service Discovery  
- **Hands-on Skills:**  
  SIEM investigation, email analysis, sandboxing, IOC handling, endpoint isolation, SOC documentation

---

💡 *This incident strengthened my practical understanding of phishing investigations, attacker behaviour, and structured SOC response workflows in a real-world-style environment.*

