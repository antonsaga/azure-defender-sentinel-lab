# Day 6 – Defender Telemetry vs XDR Analytics Rules

## Objective
Validate endpoint telemetry ingestion in Microsoft Defender for Endpoint and understand why certain endpoint behaviours do not result in alerts or Sentinel incidents when using XDR analytics rules.

---

## Environment
- Windows Server 2022 VM
- Microsoft Defender for Endpoint onboarded
- Microsoft Sentinel enabled
- XDR analytics rule templates enabled

---

## Phase 1 – Baseline Telemetry Validation

### PowerShell Activity
Initial PowerShell commands were executed on the endpoint to confirm that activity was being ingested and displayed in the Defender timeline.

![PowerShell Commands Executed](images/01-powershell-baseline.png)

### Defender Timeline
The PowerShell activity was successfully captured in Microsoft Defender for Endpoint, confirming telemetry ingestion and endpoint visibility.

![Defender Timeline](images/02-defender-powershell-telemetry.png)

---

## Phase 2 – Attempted Detection via Java

### Java Installation
Java (OpenJDK) was installed to simulate a realistic application execution chain.

![Java Installed](images/03-java-installed.png)

### Java Launching PowerShell
A Java program was created to launch PowerShell using execution policy bypass, simulating a potentially suspicious parent-child process relationship.

![Java Launches PowerShell](images/04-java-launches-powershell.png)

---

## Detection Outcome

### Defender Alerts
Despite PowerShell execution and the Java → PowerShell process chain being recorded, no Defender alert or incident was generated.

![No Defender Alerts](images/05-defender-no-alerts.png)

This demonstrates that:
- Telemetry alone does not guarantee alert creation
- XDR analytics rules depend on Defender generating alerts
- Behaviour that is not classified as malicious will not be forwarded to Sentinel

---

## Endpoint Validation
The endpoint was confirmed as successfully onboarded and reporting to Microsoft Defender for Endpoint.

![Endpoint Onboarded](images/06-endpoint-onboarded.png)

---

## Outcome and Key Takeaways
- Defender telemetry provides visibility without necessarily generating alerts
- XDR analytics rules forward alerts; they do not independently detect behaviour
- Behaviour-based detection requires custom Sentinel analytics rules
- Understanding these distinctions is critical for effective SOC detection engineering
