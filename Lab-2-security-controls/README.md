# Lab 2: Security Controls & Hardening Lab

> **Status:** 🔄 In Progress — actively being built. Days will be added as the lab develops.

---

## Overview

Where **Lab 1** focused on detection, monitoring, and SOC investigation, **Lab 2** shifts to the other side of the security stack: **prevention, hardening, and control engineering**.

This lab simulates how a security team implements, enforces, and monitors endpoint and identity security controls using the Microsoft security stack — without a dedicated enterprise environment. Everything here is self-hosted and self-directed.

The goal is to demonstrate practical, hands-on experience with the controls that underpin real-world endpoint and identity security programmes.

---

## What This Lab Covers

| Area | Tools / Technology | Focus |
|---|---|---|
| Application Control | AppLocker, Group Policy | Allow-listing, audit vs enforcement, rule design |
| Attack Surface Reduction | Microsoft Defender ASR Rules | LOLBin prevention, Office-based attack chains |
| Device Control | Intune / Defender for Endpoint | USB restriction, data exfiltration prevention |
| Data Loss Prevention | Microsoft Purview DLP | Sensitive data detection, endpoint + email policy |
| Identity & Access Control | Azure AD Conditional Access | MFA enforcement, Zero Trust access policies |
| Monitoring & Validation | Defender, Sentinel | Control effectiveness, log correlation |

---

## Lab Structure

```
lab-2-security-controls/
│
├── README.md                        ← You are here
├── images/                          ← Architecture diagrams & overview screenshots
│
├── day-01-environment-setup/        ✅ Complete
├── day-02-applocker-audit-mode/     ✅ Complete
├── day-03-applocker-enforcement/    🔄 In progress
├── day-04-asr-rules/                ⏳ Planned
├── day-05-device-control-usb/       ⏳ Planned
├── day-06-dlp-policy/               ⏳ Planned
├── day-07-dlp-testing/              ⏳ Planned
├── day-08-conditional-access/       ⏳ Planned
├── day-09-monitoring-logs/          ⏳ Planned
├── day-10-review-lessons-learned/   ⏳ Planned
```

Each day folder contains a `README.md` writeup with objective, key actions, observations, and screenshots.

---

## Key Themes

**Allow-listing over block-listing** — AppLocker is configured using an allow-list model, which is significantly more secure than traditional AV/deny-list approaches. The lab explores the operational tradeoffs of this in practice.

**Audit before enforcement** — A deliberate methodology is followed throughout: policies are first run in audit mode to understand real-world impact before enforcement is applied. This reflects production best practice and avoids service disruption.

**Controls generate telemetry** — Each control implemented is treated not just as a prevention mechanism but as a data source. Logs and alerts are reviewed in Defender and Sentinel, tying back to the detection work in Lab 1.

**Failure is documented** — Where configurations caused issues (e.g. AppLocker lockout scenarios), the cause, impact, and fix are written up. These are as valuable to document as successes.

---

## How This Complements Lab 1

| | Lab 1 | Lab 2 |
|---|---|---|
| **Focus** | Detection & SOC | Prevention & Hardening |
| **Primary tools** | Sentinel, Defender XDR, KQL | AppLocker, ASR, Purview DLP, Conditional Access |
| **Simulates** | SOC analyst / detection engineer | Security engineer / control implementer |
| **Output** | Detection rules, alert triage, incident response | Hardened endpoint baseline, access policies, DLP |

Together, they cover both sides of a security programme: **detecting threats** and **preventing them from materialising in the first place**.

---

## Environment

- Windows 10/11 VM (local lab environment)
- Microsoft 365 Developer Tenant (E5 trial)
- Azure AD / Entra ID
- Microsoft Defender for Endpoint (trial)
- Microsoft Purview compliance portal
- Microsoft Sentinel (connected from Lab 1)

---

## Related

- 🔗 [Lab 1 — Azure Sentinel Detection Engineering Lab](../README.md)
