# SOC Investigation Case Study — Privilege Escalation Detection

## Objective
This case study demonstrates a full SOC investigation workflow using Microsoft Defender and Microsoft Sentinel.

The scenario focuses on detecting and analysing a privilege escalation event involving the creation of a local administrator account.

---

## Scenario Overview
A high-severity alert was generated indicating that a new local administrator account had been created on a Windows Server.

This type of activity is commonly associated with attacker persistence and privilege escalation techniques.

---

## Alert Overview
![Alert Overview](./images/Alert_initial_details.png)

![Alert Overview 2](./images/Alert_initial_details_2.png)

## Incident Overview

An alert was triggered indicating that a new local user account was created and added to the Administrators group on a Windows Server.

### Key Details:
- **Alert Name:** New Local Administrator Account Created
- **Severity:** High
- **Category:** Persistence
- **Device:** win-srv-sec-lab-01
- **Account Created:** soclab
- **Detection Source:** Microsoft Sentinel Analytics Rule

### Initial Assessment:
The creation of a privileged account represents a high-risk action, as it grants full control over the system.

This behaviour is commonly observed in post-compromise scenarios where attackers establish persistence.

## Initial Triage

The alert indicates that a new account was created and assigned administrative privileges.

This activity is suspicious because:
- Administrative accounts provide full system access
- Attackers frequently create accounts to maintain persistence
- This may indicate post-compromise behaviour

Key investigation questions we would look for in these situations:
- Who created the account?
- When was it created?
- Is the activity authorised?
- Were additional actions performed on the system?

##  Alert Investigation

The alert details confirm that a new account named **soclab** was created and added to the local Administrators group.

This action was performed on the device:

- **Device:** win-srv-sec-lab-01

The alert was generated based on endpoint telemetry collected by Microsoft Defender and analysed through a custom Sentinel analytics rule.

### Alert Details
![Alert Details](./images/Alert_further_details_2.png)

![Alert Details 2](./images/Alert_further_details.png)

## Detection Behaviour Observation

During investigation, multiple alerts were generated for the same activity.

This occurred because the analytics rule runs on a scheduled interval while querying a time window of historical data.

As a result, the same event was detected multiple times across consecutive rule executions.

This highlights the importance of:
- Alert deduplication
- Rule tuning
- Suppression logic

to reduce noise in real-world SOC environments.

## Threat Hunting (KQL Analysis)

To validate the alert, KQL queries were executed against endpoint telemetry in Microsoft Sentinel.

The query identified events showing that a new account was created and subsequently added to the local Administrators group.

### Key Findings:
- The account **soclab** was successfully created
- The account was added to the Administrators group shortly after
- The activity originated from the same device

### 📸 Query Results
![KQL Results](./images/day10-kql-results.png)
