# Day 4 — Microsoft Sentinel Onboarding

## Objective
Onboard Microsoft Sentinel to the environment and validate SIEM readiness

---

## Actions Performed

Created a dedicated Log Analytics workspace for security monitoring
Enabled Microsoft Sentinel on the workspace
Validated successful Sentinel deployment
Confirmed Sentinel availability via the Microsoft Defender portal

---

## Evidence

### Log Analytics Workspace Created
![Log Analytics workspace created](./images/SentinelLogworkspace.png)

### Microsoft Sentinel Enabled
![Sentinel successfully added](./images/AddingSentineltoworkspace.png)

### Sentinel Overview
![Sentinel overview](./images/AzureSentinelView.png)

### Sentinel in Defender Portal
![Sentinel in Defender portal](./images/DefenderSentinelWorkbooks.png)

---

## Observations
Microsoft Sentinel is now accessed through the Microsoft Defender portal as part of Microsoft’s unified SecOps experience
No data connectors or workbooks are present yet, which is expected prior to telemetry ingestion
The SIEM platform is operational and ready for log source onboarding

---

## Outcome
Microsoft Sentinel has been successfully onboarded and is ready for data ingestion, analytics rule creation, and SOC workflows in subsequent stages.
