# 🛡️ Mastercard Cybersecurity Virtual Experience Program
### Forage | Security Awareness Team Simulation | Completed: June 6, 2026

![Mastercard](https://img.shields.io/badge/Mastercard-Cybersecurity-EB001B?style=for-the-badge&logo=mastercard&logoColor=white)
![Forage](https://img.shields.io/badge/Forage-Virtual%20Experience-4B8BBE?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)
![Focus](https://img.shields.io/badge/Focus-Phishing%20%7C%20Security%20Awareness-orange?style=for-the-badge)

---

## 📌 Overview

This repository documents my completion of the **Mastercard Cybersecurity Virtual Experience Program** hosted on [Forage](https://www.theforage.com/). In this simulation, I took on the role of an **analyst on Mastercard's Security Awareness Team**, working directly under the Chief Security Officer (CSO).

The program covered two core security tasks that mirror real-world responsibilities in a corporate cybersecurity environment:

- **Designing a phishing simulation campaign** to test employee vulnerability
- **Analyzing simulation results** and identifying which teams needed targeted security training

---

## 🎯 Objectives

- Understand the anatomy of a phishing attack and what makes it effective
- Identify red flags in suspicious emails from an analyst's perspective
- Design a convincing, contextual phishing email for use in a controlled simulation
- Analyze phishing campaign data to identify high-risk departments
- Recommend and design security awareness training for vulnerable teams

---

## 📂 Project Structure

```
mastercard-cybersecurity-forage/
│
├── README.md                                              # Full project documentation
│
├── training-presentation/
│   └── security-awareness-training-HR-Marketing.pptx    # Training deck for HR & Marketing
│
└── certificate/
    └── mastercard-cybersecurity-certificate.pdf          # Completion certificate
```

---

## 🔍 Task 1 — Design a Phishing Email Simulation

### Background

Mastercard runs monthly phishing simulation campaigns to keep employees alert. My task was to take an **obvious fake phishing email** and redesign it to be significantly more convincing — the kind a real threat actor would send.

### The Original (Obvious Fake)

```
From: mastercardsIT@gmail.com
To: employee@email.com
Subject: URGENT!  Password Reset Required

Body:
Hello (insert name) ,

Your email account has been compromised.  immediate action is required to reset your password!

Click here to reset your password in the next hour or your account will be locked:
https://en.wikipedia.org/wiki/Phishing

Regards,
Mastercard IT
```

### 🚩 Red Flags I Identified

| # | Red Flag | Why It's Suspicious |
|---|----------|-------------------|
| 1 | `mastercardsIT@gmail.com` | Typo in "Mastercards" + uses Gmail, not a corporate domain |
| 2 | `URGENT!` in subject line | Legitimate IT departments rarely use all-caps urgency tactics |
| 3 | `Hello (insert name)` | Unfilled template placeholder — immediately breaks trust |
| 4 | Poor grammar & formatting | `immediate` not capitalized; inconsistent spacing |
| 5 | Visible phishing URL | Link is not masked — destination is clearly visible and suspicious |

**Quiz Result — Question 1:** ✅ Correctly identified *"Suspicious looking source email address"* as the first and most obvious red flag.

**Quiz Result — Question 2:** ✅ Correctly identified *"Improve the spelling, grammar & sloppy layout"* as the primary improvement needed (with hyperlink masking as an additional fix).

---

### ✉️ My Improved Phishing Email

```
From: IT@mastercard.com
To: employee@email.com
Subject: Password Reset Required

Body:
Hello,

Our IT department received an incident alert indicating that your email account 
may have been compromised. Immediate action is required to secure your account 
and reset your password.

Please click here to reset your password immediately, or your account access 
will be suspended within 24 hours.

For any questions, contact IT Support at it-support@mastercard.com.

Regards,
Mastercard IT Department
```

### 🔧 Improvements Made

| Improvement | Before | After |
|-------------|--------|-------|
| Sender address | `mastercardsIT@gmail.com` | `IT@mastercard.com` |
| Subject line | `URGENT! Password Reset Required` | `Password Reset Required` |
| Greeting | `Hello (insert name) ,` | `Hello,` |
| Grammar | Multiple errors | Clean, professional tone |
| Hyperlink | Visible URL | Masked as plain text anchor link |
| Legitimacy signals | None | Support contact email added |
| Urgency framing | Aggressive/panicked | Calm but firm (more believable) |

### 💡 Key Lesson

> A well-crafted phishing email doesn't scream urgency — it **looks routine**. The most dangerous phishing emails are the ones that feel completely normal until it's too late.

---

## 📊 Task 2 — Interpret Phishing Simulation Results

### Background

After the phishing simulation campaign was run across Mastercard's departments, results were collected and analyzed. My role was to identify which teams performed poorly and design targeted training to reduce future risk.

### 📈 Campaign Results Data

| Team | Email Open Rate | Click-Through Rate | Phishing Success Rate |
|------|----------------|-------------------|----------------------|
| IT | 80% | 2% | 0% |
| **HR** | **100%** | **85%** | **75%** |
| Card Services | 60% | 50% | 10% |
| Reception | 40% | 10% | 0% |
| Engineering | 70% | 4% | 1% |
| **Marketing** | **65%** | **40%** | **38%** |
| R&D | 50% | 5% | 2% |
| **Overall Average** | **66%** | **28%** | **18%** |

> **Metrics Explained:**
> - **Email Open Rate** — % of staff who opened the simulated phishing email
> - **Click-Through Rate** — % of staff who clicked the malicious link
> - **Phishing Success Rate** — % of staff who clicked AND submitted personal information

### 🎯 Analysis — Most Vulnerable Teams

**Quiz Result — Question 1:** ✅ Correctly identified **HR and Marketing** as the two worst-performing teams.

**HR Department:**
- 100% email open rate — everyone opened it
- 85% click-through rate — nearly all who opened it clicked the link
- **75% phishing success rate** — far above the 18% average; highest risk team

**Marketing Department:**
- 65% email open rate
- 40% click-through rate
- **38% phishing success rate** — double the company average; second highest risk

**Why these teams?** HR and Marketing roles involve high volumes of external communication and frequently open attachments or click links as part of their daily workflow. This behavioral pattern makes them prime targets for social engineering attacks.

---

### 🎓 Security Awareness Training Presentation

Based on the analysis, I created a **5-slide security awareness presentation** for HR and Marketing teams:

📎 [Download Presentation → security-awareness-training-HR-Marketing.pptx](https://github.com/artiomcyber/forage-cybersecurity-projects/raw/main/01-mastercard-cybersecurity/security-awareness-training-HR-Marketing.pptx)

| Slide | Title | Content |
|-------|-------|---------|
| 1 | Don't Take the Bait 🎣 | Overview of most at-risk teams and why |
| 2 | What is Phishing? | Definition, tactics, and impact stats |
| 3 | Spot a Phishing Email | Real annotated example with 5 red flags |
| 4 | How Do We Stop Getting Phished? | 6-step employee survival guide |
| 5 | Key Takeaways | Report it, don't delete it |

> **Design Principle:** Training should be clear, concise, and non-technical. Employees who find security training boring won't retain it — so real examples and visual cues were prioritized over walls of text.
---

## 🧠 Skills Demonstrated

| Skill | Application |
|-------|-------------|
| **Threat Analysis** | Identified multiple attack vectors in a real phishing email |
| **Social Engineering Awareness** | Understood psychological manipulation tactics used in phishing |
| **Data Analysis** | Interpreted campaign metrics to identify high-risk departments |
| **Security Awareness Training** | Designed targeted training for vulnerable teams |
| **Communication** | Translated technical findings into clear, actionable recommendations |
| **Problem Solving** | Approached each task with a structured, evidence-based methodology |

---

## 🏆 Certificate

**Mastercard Cybersecurity Virtual Experience Program**
Issued by Forage · Completed: June 6, 2026

> *"I recently participated in Mastercard's job simulation on the Forage platform, and it was incredibly useful to understand what it might be like to participate on a Security Awareness team at Mastercard. I worked on a project to identify phishing emails and design security awareness training courses."*

---

## 🚀 About Me

**Artsiom** | Aspiring Cybersecurity Professional

I am an aspiring cybersecurity professional holding SC-900 (Microsoft Security, Compliance & Identity Fundamentals) and SEC0 certifications, actively expanding my hands-on experience through industry simulations, labs, and real-world projects. My focus areas include Governance, Risk & Compliance (GRC) and Security Operations (SOC) — working towards a career where I can help organizations build resilient security programs and respond effectively to evolving cyber threats.

- 🐙 GitHub: [@artiomcyber](https://github.com/artiomcyber)
- 🏅 Certifications: SC-900 | SEC0
- 🎯 Target Roles: SOC Analyst | GRC Analyst | Security Awareness | Threat Analyst

---

## ⚠️ Disclaimer

This project was completed as part of an **educational simulation**. All phishing email examples are for **defensive and awareness purposes only** — designed to help organizations recognize and prevent real-world attacks. No actual phishing was conducted.

---

*⭐ If you found this project useful or informative, feel free to star the repository!*
