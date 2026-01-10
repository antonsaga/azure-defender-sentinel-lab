# Day 1 – Environment Setup

## Objective
Build the foundational environment for a cloud-based security monitoring lab using Microsoft Defender for Endpoint and Microsoft Sentinel.

## What I built
- Azure resource group to logically separate lab resources
- Windows virtual machine to act as a monitored endpoint
- Microsoft Defender for Endpoint onboarding for endpoint telemetry
- Log Analytics Workspace for centralized logging
- Microsoft Sentinel SIEM connected to Defender and Azure activity logs

## Why this matters
This setup mirrors a real-world security monitoring environment where endpoint, identity, and cloud activity logs are centrally collected and analyzed. It provides the foundation required for detection engineering, alert investigation, and incident response.

## Evidence collected
- Defender portal showing onboarded endpoint
- Sentinel workspace ingesting security and sign-in logs
- Successful execution of KQL queries returning events

## Key observations
- Endpoint telemetry appears in Sentinel shortly after Defender onboarding
- Azure sign-in and activity logs provide useful context for investigations
- Log ingestion latency is minimal, enabling near real-time monitoring

## Next steps
- Create custom analytics rules in Sentinel
- Generate and investigate security alerts
- Tune detections to reduce false positives
- Simulate a basic security incident and document response steps
