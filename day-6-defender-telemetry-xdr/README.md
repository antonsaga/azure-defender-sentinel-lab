# Day 6 – Defender Telemetry vs XDR Analytics Rules

## Objective
Understand how Microsoft Defender for Endpoint telemetry, alerts, and XDR-based analytics rules in Microsoft Sentinel interact, and why certain endpoint behaviours do not automatically result in incidents.

---

## Environment
- Windows Server 2022 VM
- Microsoft Defender for Endpoint onboarded
- Microsoft Sentinel enabled
- XDR analytics rule templates enabled

---

## Activity Performed

### 1. Java Installation
Java (OpenJDK) was installed on the endpoint to simulate a realistic application execution chain.

![Java Installed](images/01-java-installed.png)

---

### 2. Java Launching PowerShell
A simple Java program was created to launch PowerShell using execution policy bypass, simulating a potentially suspicious parent-child process relationship.

![Java Launches PowerShell](images/02-java-launches-powershell.png)

---

### 3. Defender Telemetry Observation
The PowerShell activity was fully captured within Microsoft Defender for Endpoint, confirming that endpoint telemetry and process relationships were being recorded correctly.

![Defender Telemetry](images/03-defender-powershell-telemetry.png)

---

### 4. Alert Outcome
Despite the suspicious execution chain, no Defender alert or incident was generated for this activity.

![No Defender Alerts](images/04-defender-no-alerts.png)

This demonstrates that:
- Telemetry alone does not guarantee alert generation
- XDR analytics rules rely on Defender creating alerts first
- Not all suspicious behaviour is classified as malicious by default

---

### 5. Endpoint Validation
The endpoint was confirmed as successfully onboarded and reporting to Microsoft Defender for Endpoint.

![Endpoint Onboarded](images/05-endpoint-onboarded.png)

---

## Validation Test (Control)
To confirm that end-to-end alerting was functional, a controlled malware test (EICAR) was executed. This successfully generated a Defender alert, validating that alerting and ingestion pipelines were working as expected.

![EICAR Alert](images/06-eicar-alert-validation.png)

---

## Outcome and Key Takeaways
- XDR analytics rules forward Defender alerts; they do not independently detect behaviour
- Benign or low-confidence behaviour may generate telemetry without alerts
- Behaviour-based detection requires custom KQL analytics rules in Sentinel
- Understanding platform detection boundaries is critical for SOC operations

This day highlights the difference between telemetry visibility and actionable detections.

