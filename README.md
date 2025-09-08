# FUTURE_CS_02 – Security Alert Monitoring & Incident Response

This repository contains Task 2 of the FUTURE Cyber Security Internship.  
The objective was to perform **security alert monitoring** using SIEM tools (Splunk/ELK) and generate an **Incident Response Report**.  

---

## 📝 Executive Summary
Between **July 3, 2025**, multiple suspicious activities were detected across monitored systems via **Splunk dashboards**.  
Key incidents included:  
- **Brute Force login attempts** from both internal and external IPs.  
- **Malware detections** (Ransomware, Rootkits, Trojans, Worms, Spyware).  

Affected user accounts: **bob, alice, david, charlie, eve**.  
Impact level: **High**, due to risk of credential theft, persistence, and ransomware-driven data loss.  

---

## 📊 Summary of Security Alerts

### A. Brute Force Alerts (Failed Logins)

| Date/Time (UTC) | User    | Source IP       | Action  | Observed Behavior             | Severity |
|-----------------|---------|-----------------|---------|------------------------------|----------|
| 2025-07-03 09:02 | david   | 203.0.113.77    | login failed | External failed login attempt | High |
| 2025-07-03 07:02 | alice   | 203.0.113.77    | login failed | External failed login attempt | High |
| 2025-07-03 04:47 | bob     | 10.0.0.5        | login failed | Multiple repeated failures   | High |
| 2025-07-03 04:23 | bob     | 172.16.0.3      | login failed | Internal suspicious attempts | Medium |
| 2025-07-03 04:23 | charlie | 198.51.100.42   | login failed | External failed login attempt | High |

---

### B. Malware Detection Alerts

| User    | Malware Detected           | Severity | Associated IPs                                |
|---------|---------------------------|----------|-----------------------------------------------|
| bob     | Ransomware, Trojan, Worm  | High/Med | 10.0.0.5, 172.16.0.3, 192.168.1.101, 198.51.100.42, 203.0.113.77 |
| david   | Trojan                    | High/Low | 10.0.0.5, 172.16.0.3, 198.51.100.42, 203.0.113.77 |
| charlie | Trojan                    | High/Low | 10.0.0.5, 172.16.0.3, 192.168.1.101, 198.51.100.42, 203.0.113.77 |
| alice   | Rootkit, Spyware, Trojan  | High/Low | 172.16.0.3, 192.168.1.101, 198.51.100.42, 203.0.113.77 |
| eve     | Rootkit, Trojan           | High/Med | 10.0.0.5, 172.16.0.3, 192.168.1.101, 203.0.113.77 |

---

## ⚠ Impact Assessment
- **Bob**: Ransomware risk → possible full system encryption & data loss.  
- **Alice**: Rootkit + Spyware → persistence & credential theft risk.  
- **David/Charlie**: Trojan infections → possible backdoor access.  
- **Eve**: Multiple Trojans → medium-high risk of compromise.  
- **Systems Impacted**: Internal IPs (10.0.0.5, 172.16.0.3, 192.168.1.101) and External IPs (203.0.113.77, 198.51.100.42). Evidence of **lateral movement attempts**.  

---

## 🛡 Recommended Remediation Steps

### Immediate Containment
- Block external malicious IPs: `203.0.113.77`, `198.51.100.42`.  
- Isolate compromised hosts: `10.0.0.5`, `172.16.0.3`, `192.168.1.101`.  
- Disable impacted accounts: bob, alice, david, charlie, eve.  

### Eradication & Recovery
- Run **EDR scans** on all affected machines.  
- Wipe/rebuild systems if ransomware or rootkits are confirmed.  
- Reset all user passwords, enforce **MFA**.  

### Prevention
- Implement brute force detection rules with **account lockouts**.  
- Patch and update all endpoints.  
- Deploy SIEM correlation rules for repeated login failures + malware alerts.  
- Conduct **security awareness training** (phishing, malware prevention).  

---

## 📢 Communication to Stakeholders
Our monitoring detected **coordinated brute force attempts** and **malware infections** affecting multiple accounts.  
- Most critical risk: **Ransomware** on Bob’s account → potential large-scale data loss.  
- Current status: Containment measures applied (firewall blocking, account lockouts, malware scans).  
- Next update: Confirmation of eradication, recovery of accounts, final incident resolution.  

---


---

## ✅ Conclusion
This exercise demonstrated end-to-end **incident monitoring and response** using SIEM tools.  
Key takeaways:  
- Brute force + malware campaigns often occur together.  
- Rapid **detection, containment, and remediation** are critical to limit damage.  
- Effective SOC workflows depend on **tools + analyst expertise**.  
