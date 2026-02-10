# Day 6 – Defender Telemetry vs XDR Analytics Rules

## Objective

Validate endpoint telemetry ingestion in Microsoft Defender for Endpoint and understand why certain endpoint behaviours do not result in alerts or Sentinel incidents when using XDR analytics rule templates.

This day focuses on telemetry confidence, timeline visibility, and analysing the gap between raw endpoint activity and alert generation.

---

## Environment

- Windows Server 2022 VM  
- Microsoft Defender for Endpoint onboarded  
- Microsoft Sentinel enabled  
- XDR analytics rule templates enabled  
- Endpoint accessed via Azure Bastion  

---

## Phase 1 – Baseline Telemetry Validation

Before attempting to trigger any alerts, the environment was checked to confirm a clean baseline state.

- No active alerts
- No existing endpoint timeline activity

![Empty Alerts Page](images/EmptyAlertsPageDefenderforEndpoint.png)  
![Empty Timeline](images/EmptyTimelineDefenderforEndpoint.png)

---

## Phase 2 – PowerShell Activity Generation

Several PowerShell commands were executed directly on the endpoint to generate controlled, benign activity.  
The purpose was to confirm that Defender was capturing:

- Process execution events
- User context
- Command-line activity

![Running PowerShell Commands](images/RunningPowershellCommands.png)  
![Running PowerShell Commands Continued](images/RunningPowershellCommands2.png)

---

## Phase 3 – Defender Timeline & MITRE ATT&CK Mapping

The executed PowerShell activity appeared correctly in the Defender for Endpoint device timeline.

Key observations:
- `powershell.exe` execution recorded
- Parent–child relationships visible
- Events enriched with **MITRE ATT&CK technique mapping**
- User context (`labadmin`) clearly shown

The **Additional information** column provides Defender’s interpretation of the activity, including mapped ATT&CK techniques (e.g. PowerShell execution and user-initiated execution).  
This confirms that Defender is not only ingesting telemetry, but also **classifying behaviour against known attack techniques**.

![PowerShell Activity in Defender Timeline](images/PowershellactivityinDefenderforEndpoint.png)

---

## Phase 4 – Endpoint Visibility & Asset Context

The endpoint was reviewed within Defender to confirm onboarding status, OS details, and exposure context prior to further testing.

![Defender Endpoint Assets](images/Defenderforendpointassets.png)  
![Defender Endpoint Details](images/Defenderforendpointdetails.png)

---

## Phase 5 – Attempted XDR Analytics Rule Scenario (Java → PowerShell)

To test a more suspicious execution chain, Java was installed with the intention of triggering an analytics rule based on a non-standard parent process launching PowerShell.

### Java Installation & Validation

![Java Installed and Version Verified](images/javainstalledversionshowing.png)

---

### Java Executing PowerShell

A simple Java program was created to execute PowerShell using execution policy bypass flags.

![Java File Launching PowerShell](images/JavaFiletolaunchPowershell.png)

---

### Execution Outcome

The Java application successfully launched PowerShell and executed commands on the endpoint.  
However, no Defender alert or Sentinel incident was generated.

![Java PowerShell Execution Successful](images/Javapowershellcommandsuccessful.png)

---

## Findings & Analysis

### Confirmed

- Defender for Endpoint telemetry ingestion is working
- Endpoint timeline captures PowerShell activity reliably
- MITRE ATT&CK technique mapping is applied at the event level
- Parent–child execution relationships are visible

### Not Observed

- No XDR analytics rule alert
- No Sentinel incident created

### Analysis

Although the execution chain (Java spawning PowerShell) appears suspicious in isolation, it did not meet the conditions required by the enabled XDR analytics rules.

This highlights that:
- Analytics rules rely on specific behaviour patterns and signal confidence
- Not all ATT&CK-mapped activity results in an alert
- Telemetry visibility and detection logic are separate concerns

---

## Next Steps

- Review and adjust analytics rule logic and thresholds
- Validate rule conditions directly using KQL
- Introduce more deterministic detection scenarios (e.g. encoded commands or known LOLBIN abuse)
- Correlate Defender signals into Sentinel incidents

---
