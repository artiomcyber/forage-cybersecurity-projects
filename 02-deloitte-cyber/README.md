# 🟢 Deloitte Australia — Cyber Job Simulation
### Forage | Cybersecurity Threat Investigation | Completed: June 7, 2026

![Deloitte](https://img.shields.io/badge/Deloitte-Cyber-86BC25?style=for-the-badge&logoColor=white)
![Forage](https://img.shields.io/badge/Forage-Virtual%20Experience-4B8BBE?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)
![Focus](https://img.shields.io/badge/Focus-Log%20Analysis%20%7C%20Threat%20Detection-orange?style=for-the-badge)

---

## 📌 Overview

This repository documents my completion of the **Deloitte Australia Cyber Job Simulation** hosted on [Forage](https://www.theforage.com/). In this simulation, I joined Deloitte's cybersecurity team to investigate a suspected data breach at **Daikibo Industrials** — a manufacturing client whose sensitive production data had been leaked to a major news publication.

The simulation involved one core investigation task requiring real SOC analyst skills:

- **Analyzing web activity logs** to identify the source and method of the breach
- **Determining the attack vector** — external vs internal threat
- **Identifying suspicious automated behavior** within thousands of log entries

---

## 🎯 Objectives

- Determine whether the breach originated from an external attacker or an insider threat
- Read and interpret web server access logs (`web_requests.log`) at scale
- Identify anomalous patterns indicating automated/scripted data exfiltration
- Locate the specific compromised user account and document the attack timeline

---

## 📂 Project Structure

```
02-deloitte-cyber/
│
├── README.md                          # Full investigation documentation (this file)
│
├── evidence/
│   ├── automated-polling-pattern.png  # Screenshot showing hourly automated requests
│   ├── token-expiry-401.png           # Screenshot showing midnight 401 UNAUTHORIZED
│   └── session-resume-pattern.png     # Screenshot showing re-authentication next day
│
└── certificate/
    └── deloitte-cyber-certificate.pdf # Completion certificate
```

---

## 🔍 Task 1 — Cyber Security Investigation

### Background

Daikibo Industrials operates a **telemetry dashboard** (hosted on the company's internal intranet) that monitors the real-time status of factory machines across four global locations: **Meiyo, Seiko, Shenzhen, and Berlin**.

A major news publication revealed sensitive production information that could only have been obtained by accessing this internal dashboard. Daikibo suspects a security breach and engaged Deloitte's cyber team to investigate.

---

### 🌐 Question 1 — Could This Be an External Attack?

**Question:** Could the breach have been executed by an attacker on the internet with no access to Daikibo's VPN?

**Answer: No.**

**Reasoning:**

The telemetry dashboard is hosted on Daikibo's **internal intranet**, meaning it is only accessible from within the company's VPN. An external attacker without VPN access would:

- Receive no response from the internal IP addresses
- Trigger firewall alerts attempting to reach internal-only resources
- Have no way to authenticate against an internal authentication system

For the breach to have occurred, the attacker must have already had **legitimate or stolen VPN credentials** and been operating from inside the network perimeter. This narrows the investigation to either a malicious insider or a compromised internal account.

**Implication:** This is not a direct internet attack — it is an **insider threat or compromised credential** scenario.

---

### 🔎 Question 2 — Identifying Suspicious Activity in the Logs

**The Log File Structure:**

Each block in `web_requests.log` represents a unique IP address on Daikibo's internal network. The typical legitimate user session follows this pattern:

```
GET "/"              → 401 (redirect to login)
GET "/login"         → 200
POST "/login"        → 200 (authentication)
GET "/"              → 200 (authenticated)
GET "/api/factory/..." → 200 (manual data browsing)
```

Legitimate users browse factories manually, at irregular intervals, checking specific machines — human behavior is inherently inconsistent in timing.

---

### 🚨 Suspicious IP Identified: 192.168.0.101

After reviewing all IP blocks in the log file, **IP address `192.168.0.101`** with **user ID `mdB7yD2dp1BFZPontHBQ1Z`** was flagged as highly suspicious.

#### 🤖 Red Flag 1 — Automated Hourly Polling (Bot Behavior)

Starting from `2021-06-25T17:00:48.000Z`, this user begins making requests to **all four factories simultaneously** at **exact 1-hour intervals** with a consistent `:48` second timestamp:

```
2021-06-25T17:00:48.000Z GET /api/factory/machine/status?factory=meiyo&machine=*
2021-06-25T17:00:48.000Z GET /api/factory/machine/status?factory=seiko&machine=*
2021-06-25T17:00:48.000Z GET /api/factory/machine/status?factory=shenzhen&machine=*
2021-06-25T17:00:48.000Z GET /api/factory/machine/status?factory=berlin&machine=*

2021-06-25T18:00:48.000Z GET /api/factory/machine/status?factory=meiyo&machine=*
2021-06-25T18:00:48.000Z GET /api/factory/machine/status?factory=seiko&machine=*
... (repeating every hour)
```

This pattern is **impossible for a human to maintain** — four simultaneous requests to all factories at exactly `:48` seconds past every hour. This is unmistakably an **automated script or bot** performing scheduled data exfiltration.

#### 🔓 Red Flag 2 — Session Token Expiry at Midnight (Continued Unauthorized Requests)

At `2021-06-26T00:00:48.000Z` the session token expired and all requests began returning `401 UNAUTHORIZED` — yet the automated script **continued running regardless**:

```
2021-06-26T00:00:48.000Z GET /api/factory/machine/status?factory=meiyo&machine=*   401 (UNAUTHORIZED)
2021-06-26T00:00:48.000Z GET /api/factory/machine/status?factory=seiko&machine=*   401 (UNAUTHORIZED)
2021-06-26T00:00:48.000Z GET /api/factory/machine/status?factory=shenzhen&machine=* 401 (UNAUTHORIZED)
2021-06-26T00:00:48.000Z GET /api/factory/machine/status?factory=berlin&machine=*   401 (UNAUTHORIZED)
```

The unauthorized requests continued **hourly through the night** — from midnight until approximately 16:00 the following day. A legitimate user would have noticed the session expiry and logged back in. The script had no such awareness, confirming automated behavior.

> **Note:** This token expiry and continued unauthorized polling behavior was not highlighted in the simulation materials — it was independently identified during log analysis as an additional indicator of compromise.

#### 🔄 Red Flag 3 — Re-authentication and Resumption of Attack

At `2021-06-26T16:04:00.000Z`, the attacker manually re-authenticated:

```
2021-06-26T16:04:00.000Z GET "/"                            → 401
2021-06-26T16:04:01.000Z GET "/login"                       → 200
2021-06-26T16:04:54.000Z POST "/login"                      → 200
2021-06-26T16:04:54.000Z GET "/" {authorizedUserId: "mdB7yD2dp1BFZPontHBQ1Z"} → 200
```

Immediately after re-authentication at `17:00:48`, the **automated hourly polling resumed** — confirming that whoever controls this account intentionally re-authenticated to continue the exfiltration campaign.

---

### 📊 Attack Timeline Summary

| Time | Event |
|------|-------|
| `2021-06-25T16:14:00Z` | Initial login by `192.168.0.101` |
| `2021-06-25T17:00:48Z` | **Automated polling begins** — all 4 factories, every hour |
| `2021-06-26T00:00:48Z` | **Session token expires** — 401 errors begin |
| `2021-06-26T00:00:48Z` – `16:03:59Z` | Script continues running despite 401 responses |
| `2021-06-26T16:04:54Z` | **Manual re-authentication** — attacker re-logs in |
| `2021-06-26T17:00:48Z` | **Automated polling resumes** for second day |

---

### 🎯 Findings Summary

| Finding | Detail |
|---------|--------|
| **Suspicious IP** | `192.168.0.101` |
| **Compromised User ID** | `mdB7yD2dp1BFZPontHBQ1Z` |
| **Attack Type** | Automated data exfiltration via scheduled API polling |
| **Attack Vector** | Internal network (VPN access required — insider or stolen credentials) |
| **Data Exfiltrated** | Machine status data from all 4 factories (meiyo, seiko, shenzhen, berlin) |
| **Duration** | June 25–26, 2021 (minimum) |
| **Detection Method** | Exact-interval timestamp pattern + simultaneous multi-factory requests |

---

## 🧠 Skills Demonstrated

| Skill | Application |
|-------|-------------|
| **Log Analysis** | Manually reviewed thousands of web server log entries across 40+ IP addresses |
| **Threat Detection** | Identified automated bot behavior from timing and request patterns |
| **Incident Investigation** | Reconstructed full attack timeline from raw log data |
| **Computer Networking** | Applied understanding of VPN, HTTP status codes, session tokens, and API calls |
| **Web Security** | Identified session token expiry exploitation and credential-based access |
| **Critical Thinking** | Independently identified token expiry exploitation not covered in simulation materials |
| **Data Analysis** | Pattern recognition across large, unstructured log datasets |

---

## 🏆 Certificate

**Deloitte Australia Cyber Job Simulation**
Issued by Forage · Completed: June 7, 2026

📎 [Download Certificate](https://github.com/artiomcyber/forage-cybersecurity-projects/blob/main/02-deloitte-cyber/certificate/deloitte-cyber-certificate.pdf?raw=true)

---

## 🚀 About Me

**Artsiom Pankrashkin** | Aspiring Cybersecurity Professional

I am an aspiring cybersecurity professional holding SC-900 (Microsoft Security, Compliance & Identity Fundamentals) and SEC0 certifications, actively expanding my hands-on experience through industry simulations, labs, and real-world projects. My focus areas include Governance, Risk & Compliance (GRC) and Security Operations (SOC).

- 🐙 GitHub: [@artiomcyber](https://github.com/artiomcyber)
- 🏅 Certifications: SC-900 | SEC0
- 🎯 Target Roles: SOC Analyst | GRC Analyst | Security Awareness | Threat Analyst

---

## ⚠️ Disclaimer

This project was completed as part of an **educational simulation** provided by Forage in partnership with Deloitte Australia. All log files and company names are fictional and used for training purposes only.

---

*⭐ If you found this investigation write-up useful, feel free to star the repository!*
