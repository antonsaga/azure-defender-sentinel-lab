# Day 5 — Analytics Rule Enablement (Microsoft Defender XDR → Sentinel)

## Objective

Establish baseline detection readiness in Microsoft Sentinel by installing Microsoft Defender XDR content and enabling built-in analytics rules before any endpoint telemetry is ingested.

---

## Environment

- SIEM: Microsoft Sentinel
- Data Source: Microsoft Defender XDR
- Workspace: azure-sentinel-security-lab
- Rule Type: Scheduled analytics rules
- Status: Enabled (no alerts expected until endpoint telemetry is onboarded)

---

## Actions Performed

---

### 1. Installed Microsoft Defender XDR content in Sentinel

- Installed the Microsoft Defender XDR solution from the Sentinel Content Hub
- Verified successful installation and availability of analytics rule templates

**Evidence**

![Microsoft Defender XDR Installed](images/InstalledXDR.png)

---

### 2. Reviewed Available Analytics Rule Templates

- Navigated to **Analytics → Rule templates**
- Reviewed execution, persistence, and lateral movement detections mapped to MITRE ATT&CK
- Selected high-signal rules suitable for baseline SOC coverage

**Evidence**

![Analytics Rule Templates](images/Analyticspage.png)

---

### 3. Enabled the following Microsoft-provided analytics rules:

Enabled the following Microsoft-provided detections:

**Java Executing cmd to run PowerShell**
- Severity: High
- MITRE Tactic: Execution
- Technique: T1059

**Service Accounts Performing Remote PS**
- Severity: High
- MITRE Tactic: Lateral Movement
- Technique: T1210

**Rare Process as a Service**
- Severity: Medium
- MITRE Tactic: Persistence
- Technique: T1543

All rules were enabled as scheduled analytics rules with default thresholds.

**Evidence**

![Enabling Built-in XDR Rule](images/EnablingXDRbuiltinrule.png)

---

### 4. Verified Rule Status in Unified Rules Page

- Confirmed all enabled rules appear as **Active**
- Verified severity, MITRE mapping, and scheduled execution status
- Confirmed rules are associated with Microsoft Defender XDR telemetry

**Evidence**

![Unified Rules Page](images/EnabledRules.png)

---

### 5. Log Availability Validation (No Telemetry Yet)

- Queried Sentinel Logs to confirm table availability:
  - `SecurityAlert`
  - `DeviceProcessEvents`
- No results returned, as expected
- Endpoints and attack simulation not yet configured
- This confirms the detection pipeline is correctly configured, even though no telemetry is present yet.

**Evidence**

![Sentinel Log Search](images/logsearch.png)

---

## Key Learnings & Takeaways

- Analytics rules can be enabled and validated before any telemetry exists
- Installing Defender XDR content provides detection logic, but alerts require:
  - Endpoint onboarding
  - Real or simulated execution activity
- KQL exploration highlighted the difference between:
  - Table availability
  - Actual event ingestion
- This stage focuses on detection preparation rather than alert volume


---

## Next Steps

- Onboard a Windows endpoint to Microsoft Defender for Endpoint
- Generate controlled execution activity (PowerShell / LOLBins)
- Validate alert creation and incident generation
- Perform alert triage and investigation workflow

---

## Why This Matters

This lab demonstrates:

This lab demonstrates:

- Correct sequencing of SIEM detection setup
- Realistic SOC preparation before attack simulation
- Practical experience with Sentinel, Defender XDR, and MITRE ATT&CK
- Understanding detection engineering beyond simply generating alerts


