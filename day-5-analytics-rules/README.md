# Day 5 — Analytics Rule Enablement (Microsoft Defender XDR)

## Objective
Establish baseline detection capability in Microsoft Sentinel by enabling
built-in analytics rules prior to live telemetry ingestion.

## Actions Performed
- Reviewed available Microsoft Defender XDR analytics rule templates
- Selected a high-severity execution-based detection mapped to MITRE ATT&CK
- Enabled the built-in analytics rule within Microsoft Sentinel
- Verified rule status and configuration within the unified rules page

## Enabled Detection
- Rule: Java Executing cmd to run PowerShell
- Severity: High
- Tactic: Execution
- Technique: T1059
- Data source: Microsoft Defender XDR
- Status: Enabled

## Evidence
Screenshots demonstrating:
- Enabled analytics rule in Microsoft Sentinel
- Rule details including severity, MITRE mapping, and query logic

## Observations
- Analytics rules can be enabled independently of active telemetry ingestion
- Built-in detections are MITRE-aligned and production-ready
- No alerts are generated yet, which is expected without endpoint activity

## Outcome
Microsoft Sentinel now has active detection logic in place and is prepared
to generate alerts once endpoint telemetry is ingested.

