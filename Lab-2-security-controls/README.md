# Lab 2 – Security Controls & Endpoint Hardening

> **Status:** 🔄 In Progress — actively being built. 
> Days will be added as the lab develops.

---

## Overview

Where Lab 1 focused on detection, monitoring, and SOC investigation, 
Lab 2 shifts to the other side of the security stack: prevention, 
hardening, and control engineering.

This lab simulates how a security team implements, enforces, and 
validates endpoint security controls using the Microsoft security 
stack — without a dedicated enterprise environment. Everything here 
is self-hosted and self-directed.

The goal is to demonstrate practical, hands-on experience with the 
controls that underpin real-world endpoint security programmes.

---

## Environment

- **VM:** lab2-endpoint (Azure, UK West, Windows 10)
- **Access:** Azure Bastion
- **Tools:** AppLocker, Group Policy, Microsoft Defender ASR, 
  Microsoft Purview, Intune, Azure AD / Entra ID, Sentinel

---

## What This Lab Covers

| Area | Tools | Focus |
|---|---|---|
| Application Control | AppLocker, Group Policy | Allow-listing, audit vs enforcement, rule design |
| Attack Surface Reduction | Microsoft Defender ASR Rules | LOLBin prevention, Office-based attack chains |
| Device Control | Intune / Defender for Endpoint | USB restriction, data exfiltration prevention |
| Data Loss Prevention | Microsoft Purview DLP | Sensitive data detection, endpoint and email policy |
| Identity & Access Control | Azure AD Conditional Access | MFA enforcement, Zero Trust access policies |
| Monitoring & Validation | Defender, Sentinel | Control effectiveness, log correlation |

---

## Lab Structure
```
Lab-2-security-controls/
│
├── README.md                        ← You are here
│
├── day-1-Applocker/                 ✅ Complete
│   └── day1.md
│
├── day-2-Applocker/                 ✅ Complete
│   └── day2.md
│
├── day-3-applocker-enforcement/     🔄 In Progress
│   └── day3.md
│
├── day-4-asr-rules/                 ⏳ Planned
├── day-5-device-control-usb/        ⏳ Planned
├── day-6-dlp-policy/                ⏳ Planned
├── day-7-dlp-testing/               ⏳ Planned
├── day-8-conditional-access/        ⏳ Planned
├── day-9-monitoring-logs/           ⏳ Planned
├── day-10-review-lessons-learned/   ⏳ Planned
```
Each day folder contains a README writeup covering objective, 
actions taken, observations, analyst commentary, and screenshots.

---

## Key Themes

**Allow-listing over block-listing** — AppLocker is configured 
using an allow-list model, which is significantly more resilient 
than traditional AV or deny-list approaches. The lab explores the 
operational trade-offs of this in practice, including the risk of 
misconfiguration and VM lockout.

**Audit before enforcement** — All policies are first run in audit 
mode to understand real-world impact before enforcement is applied. 
This reflects production change management practice and avoids 
unintended service disruption.

**Controls generate telemetry** — Each control is treated not just 
as a prevention mechanism but as a data source. AppLocker block 
events, ASR alerts, and DLP detections are reviewed and exported, 
tying prevention back to the detection work in Lab 1.

**Failure is documented** — Where configurations caused issues 
(such as the Azure Bastion failure following subscription 
reactivation, and the AppLocker administrator exemption behaviour 
during enforcement testing), the cause, impact, and resolution are 
written up. These are as instructive to document as successes.

---

## Day-by-Day Summary

| Day | Topic | Status |
|---|---|---|
| Day 1 | AppLocker setup and audit mode configuration | ✅ Complete |
| Day 2 | AppLocker policy tuning and controlled enforcement | ✅ Complete |
| Day 3 | AppLocker enforcement testing and validation | 🔄 In Progress |
| Day 4 | Attack Surface Reduction (ASR) rules | ⏳ Planned |
| Day 5 | Device control — USB restriction | ⏳ Planned |
| Day 6 | DLP policy configuration | ⏳ Planned |
| Day 7 | DLP testing and validation | ⏳ Planned |
| Day 8 | Conditional Access policies | ⏳ Planned |
| Day 9 | Monitoring and log correlation | ⏳ Planned |
| Day 10 | Review and lessons learned | ⏳ Planned |

---

## How This Complements Lab 1

| | Lab 1 | Lab 2 |
|---|---|---|
| **Focus** | Detection & SOC | Prevention & Hardening |
| **Primary tools** | Sentinel, Defender XDR, KQL | AppLocker, ASR, Purview, Conditional Access |
| **Simulates** | SOC analyst / detection engineer | Security engineer / control implementer |
| **Output** | Detection rules, alert triage, incident response | Hardened endpoint baseline, access policies, DLP |

Together they cover both sides of a security programme — detecting 
threats and preventing them from materialising in the first place.

---

## Related

- 🔗 [Lab 1 — Azure Defender & Sentinel SOC Lab](../README.md)
