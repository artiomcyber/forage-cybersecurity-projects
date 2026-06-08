# 🟣 Datacom — Cyber Security Operations Job Simulation
### Forage | Cybersecurity Consulting | Completed: June 8, 2026

![Datacom](https://img.shields.io/badge/Datacom-Cyber%20Security%20Operations-1F3864?style=for-the-badge&logoColor=white)
![Forage](https://img.shields.io/badge/Forage-Virtual%20Experience-4B8BBE?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)
![Focus](https://img.shields.io/badge/Focus-Incident%20Response%20%7C%20Risk%20Assessment-orange?style=for-the-badge)

---

## 📌 Overview

This repository documents my completion of the **Datacom Cyber Security Operations Job Simulation** hosted on [Forage](https://www.theforage.com/). In this simulation I worked as a **Cybersecurity Analyst** within Datacom's consulting team, handling two real-world client engagements back to back — a ransomware incident investigation and a full cybersecurity risk assessment.

This was the most demanding simulation in the portfolio so far. Both tasks required producing professional deliverables that a real analyst would submit to a client's executive team.

---

## 🎯 Objectives

- Investigate a ransomware attack and produce a comprehensive Security Breach Impact Report
- Identify the attack chain, vulnerabilities exploited, and business consequences
- Conduct a full cybersecurity risk assessment for a retail organisation
- Systematically identify and prioritise risks using a structured framework
- Develop and communicate practical mitigation strategies with implementation timelines and cost estimates

---

## 📂 Project Structure

```
03-datacom-cybersecurity-operations/
│
├── README.md                                                  # Full project documentation
├── Orion Health Security Breach Impact Report.docx            # Task 1 — Ransomware incident report
├── RetailNova Risk Assessment.docx                            # Task 2 — Cybersecurity risk assessment
└── DATACOM Cyber Security Operations Job Simulation.pdf       # Completion certificate
```

---

## 🔍 Task 1 — Ransomware Incident Investigation

### Client: Orion Health Services

Orion Health Services is a mid-sized healthcare technology provider with 250 employees, managing sensitive patient data and providing cloud-based software to clinics across Australia and New Zealand.

On a Monday morning, their IT team detected unusual outbound traffic from an internal server. By midday, employees were locked out of systems, and a ransom note had appeared on the shared drive.

### The Attack

| Stage | MITRE ATT&CK | What Happened |
|-------|-------------|---------------|
| Initial Access | T1566.001 — Spearphishing Attachment | Finance employee opened a malicious Excel file with an embedded macro |
| Execution | T1204.002 — Malicious File | Macro executed and installed malware silently |
| Credential Access | T1003 — Credential Dumping | Mimikatz used to harvest internal credentials from memory |
| Lateral Movement | T1021 — Remote Services | Attacker moved across the network using stolen credentials |
| Command & Control | T1071 — Application Layer Protocol | Suspicious login detected from an overseas IP address |
| Impact | T1486 — Data Encrypted for Impact | Ransomware deployed — files encrypted with .orionlock extension |

### Compromised Data
- Employee payroll records
- Patient appointment schedules across Australian and NZ clinics
- Internal system credentials

### Systems Affected
- File server — fully encrypted
- HR and finance systems
- Backup server — partially encrypted, eliminating standard recovery options

### Key Findings

**The attack was not sophisticated — it was opportunistic.** The entry point was a standard phishing email. What made it damaging was the absence of basic controls: no MFA, no EDR, no offline backups, and a backup server connected to the same network it was supposed to protect.

**Estimated financial exposure: $770K — $3.2M+ AUD** across ransom demand, forensic investigation, system recovery, downtime, legal costs and customer notification.

### Recommendations Summary

| Priority | Recommendation | Timeline | Est. Cost |
|----------|---------------|----------|-----------|
| 🔴 Critical | Isolate and contain affected systems | Immediate | Internal IT |
| 🔴 Critical | Engage forensic cybersecurity firm | 24–48 hours | $50K–$200K |
| 🔴 Critical | Notify OAIC under NDB scheme | Within 30 days | $20K–$80K |
| 🟠 High | Deploy MFA on all systems | 2–4 weeks | $5K–$20K/yr |
| 🟠 High | Implement 3-2-1 offline backup strategy | 4–8 weeks | $10K–$50K |
| 🟠 High | Deploy EDR solution | 4–8 weeks | $15K–$60K/yr |
| 🟢 Medium | Phishing awareness training programme | 2–4 weeks | $2K–$10K/yr |
| 🟢 Medium | Develop incident response plan | 1–2 months | $5K–$25K |

📎 [Download Full Report](https://github.com/artiomcyber/forage-cybersecurity-projects/blob/main/03-datacom-cybersecurity-operations/Orion%20Health%20Security%20Breach%20Impact%20Report.docx?raw=true)

---

## 📊 Task 2 — Cybersecurity Risk Assessment

### Client: RetailNova Pty Ltd

RetailNova is a Melbourne-based retail company founded in 2012, employing approximately 1,200 staff and generating $450 million in annual revenue. The company sells consumer electronics and home appliances through 85 physical stores and a custom-built e-commerce platform integrated with PayPal and Afterpay.

RetailNova has experienced three confirmed security incidents between 2023 and 2025 — a phishing attack, a ransomware attempt, and a third-party vendor data leak — which significantly informed the likelihood ratings throughout this assessment.

### Risk Assessment Summary

| Risk ID | Risk | Inherent Rating | Residual Rating | Priority Action |
|---------|------|----------------|----------------|----------------|
| R-001 | Phishing / Credential Compromise | 🔴 EXTREME | 🟠 HIGH | MFA + anti-phishing gateway |
| R-002 | Ransomware Attack | 🔴 EXTREME | 🟠 HIGH | EDR + offline backup strategy |
| R-003 | Third-Party Vendor Breach | 🟠 HIGH | 🟠 HIGH | TPRM programme + vendor contracts |
| R-004 | Insider Threat | 🟠 HIGH | 🟡 MEDIUM | DLP + offboarding procedure |
| R-005 | E-Commerce Platform Breach | 🔴 EXTREME | 🟠 HIGH | WAF + annual penetration testing |

### Risk Matrix Used (5x5 Likelihood × Consequence)

| | Insignificant (1) | Minor (2) | Moderate (3) | Major (4) | Extreme (5) |
|---|---|---|---|---|---|
| **5 — Almost Certain** | MEDIUM | HIGH | HIGH | EXTREME | EXTREME |
| **4 — Likely** | MEDIUM | MEDIUM | HIGH | HIGH | EXTREME |
| **3 — Possible** | LOW | MEDIUM | MEDIUM | HIGH | HIGH |
| **2 — Unlikely** | LOW | LOW | MEDIUM | MEDIUM | HIGH |
| **1 — Rare** | LOW | LOW | LOW | MEDIUM | MEDIUM |

### Key Findings

**Three out of five risks rated EXTREME on inherent assessment.** RetailNova's security posture is being held together by basic controls — firewalls and antivirus — that are not sufficient for the complexity of their environment. The company's history of three incidents in three years confirms the threat is real and active, not hypothetical.

The highest priority gap identified: **no MFA on corporate accounts**. Given that phishing already succeeded in 2023 and a ransomware attempt occurred in 2024, enforcing MFA should be the first action taken — it is low cost, fast to implement, and would have prevented or significantly limited both previous incidents.

### Methodology

- Framework: **NIST CSF 2.0** — Identify function
- Risk rating: **5x5 Likelihood × Consequence matrix**
- Each risk assessed with **Inherent Risk** (before controls) and **Residual Risk** (after existing controls)
- Vulnerabilities mapped to specific assets with existing controls documented

📎 [Download Full Report](https://github.com/artiomcyber/forage-cybersecurity-projects/blob/main/03-datacom-cybersecurity-operations/RetailNova%20Risk%20Assessment.docx?raw=true)

---

## 🧠 Skills Demonstrated

| Skill | Application |
|-------|-------------|
| **Incident Response** | Investigated and documented a full ransomware attack following NIST SP 800-61 methodology |
| **MITRE ATT&CK** | Mapped each stage of the attack to specific tactics and technique IDs |
| **Risk Assessment** | Conducted a structured 5x5 risk assessment across 5 risk categories for a complex retail environment |
| **Threat Analysis** | Identified threats, vulnerabilities and existing controls for 7 key business assets |
| **Security Reporting** | Produced two executive-level reports with findings, impact analysis and costed recommendations |
| **Legal & Compliance** | Applied knowledge of Australian Privacy Act, NDB scheme and OAIC notification requirements |
| **Risk Management** | Calculated inherent and residual risk ratings and developed risk treatment plans |
| **Analytical Thinking** | Connected incident history data to likelihood ratings throughout the risk assessment |

---

## 🏆 Certificate

**Datacom Cyber Security Operations Job Simulation**
Issued by Forage · Completed: June 8, 2026

📎 [Download Certificate](https://github.com/artiomcyber/forage-cybersecurity-projects/blob/main/03-datacom-cybersecurity-operations/DATACOM%20Cyber%20Security%20Operations%20Job%20Simulation.pdf?raw=true)

---

## 🚀 About Me

**Artsiom Pankrashkin** | Aspiring Cybersecurity Professional

I am an aspiring cybersecurity professional holding SC-900 (Microsoft Security, Compliance & Identity Fundamentals) and SEC0 certifications, actively expanding my hands-on experience through industry simulations, labs, and real-world projects. My focus areas include Governance, Risk & Compliance (GRC) and Security Operations (SOC).

- 🐙 GitHub: [@artiomcyber](https://github.com/artiomcyber)
- 🏅 Certifications: SC-900 | SEC0
- 🎯 Target Roles: SOC Analyst | GRC Analyst | Security Awareness | Threat Analyst

---

## ⚠️ Disclaimer

This project was completed as part of an **educational simulation** provided by Forage in partnership with Datacom. All company names, incident scenarios and data used are fictional and created for training purposes only.

---

*⭐ If you found this project useful, feel free to star the repository!*
