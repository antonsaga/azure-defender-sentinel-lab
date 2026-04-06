# Azure Defender & Sentinel Security Lab

This project simulates a real-world cloud security monitoring environment using Microsoft Defender for Cloud and Microsoft Sentinel.

The lab focuses on how security analysts actually work in practice - onboarding systems, improving security posture, building detections, and investigating alerts using real telemetry.

Rather than following a certification-style setup, this environment was built to reflect day-to-day SOC and cloud security workflows.

---

## What This Lab Demonstrates

- Azure security configuration and cloud environment setup  
- Microsoft Defender for Cloud onboarding and posture analysis  
- Microsoft Sentinel (SIEM) deployment and data integration  
- Detection engineering using KQL  
- Alert validation through simulated attacker activity  
- SOC-style investigation and triage using endpoint telemetry  

---

## Objectives

- Build a controlled Azure environment suitable for security experimentation
- Onboard infrastructure into Microsoft Defender for Cloud
- Observe baseline security posture and security recommendations
- Reduce exposure through targeted hardening actions
- Validate security controls and Defender evaluation behaviour
- Onboard and validate SIEM readiness using Microsoft Sentinel
- Incrementally introduce logging, detections, and alerts
- Develop custom detection rules using KQL
- Document SOC-style monitoring and detection engineering workflows

This lab mirrors realistic SOC and cloud security workflows rather than
following a purely academic or certification-driven approach.

---

## Lab Structure

The lab is organised into stages to reflect how a security environment evolves over time:

Each stage includes:
- Actions performed  
- Supporting screenshots  
- Observations on system behaviour and security impact

```text
azure-defender-sentinel-lab/
├── README.md
├── architecture/
│   ├── README.md
│   └── images/
├── day-1-setup/
│   ├── README.md
│   └── images/
├── day-2-network-hardening/
│   ├── README.md
│   └── images/
├── day-3-defender-investigation/
│   ├── README.md
│   └── images/
├── day-4-sentinel-onboarding/
│   ├── README.md
│   └── images/
├── day-5-analytics-rules/
│   ├── README.md
│   └── images/
├── day-6-defender-telemetry-xdr/
│   ├── README.md
│   └── images/
├── day-7-custom-detection-rule/
│   ├── README.md
│   └── images/
├── day-8-detection-engineering/
│   ├── README.md
│   └── images/
├── day-9-detection-validation/
│   ├── README.md
│   └── images/
└── day-9-part-2-soc-investigation/
    ├── README.md
    └── images/
```

## Current Progress

### Day 1 — Azure Defender for Cloud Setup
- Created a dedicated Azure resource group and virtual network  
- Deployed a Windows Server virtual machine  
- Enabled Microsoft Defender for Cloud at the subscription level  
- Confirmed VM onboarding and visibility in Defender for Cloud  
- Reviewed initial security posture and baseline recommendations  

📁 [Day 1 Documentation](day-1-setup/README.md)  
📐 [Architecture Overview](architecture/README.md)

---

### Day 2 — Network Hardening (NSG + RDP Exposure)
- Reviewed VM networking configuration and NSG inbound rules  
- Identified unrestricted inbound RDP (TCP/3389) exposure  
- Restricted RDP access to a trusted source IP  
- Observed Defender for Cloud recommendation updates  
- Reduced external attack surface while maintaining access  

📁 [Day 2 Documentation](day-2-network-hardening/README.md)

---

### Day 3 — Defender for Cloud Vulnerability Assessment
- Investigated vulnerability assessment recommendations  
- Verified Defender for Servers Plan 2 configuration  
- Confirmed agentless scanning and assessment settings  
- Observed scan latency and inventory behaviour  

📁 [Day 3 Documentation](day-3-defender-investigation/README.md)

---

### Day 4 — Microsoft Sentinel Onboarding
- Created a Log Analytics workspace  
- Enabled Microsoft Sentinel  
- Verified successful deployment  
- Confirmed SIEM readiness  

📁 [Day 4 Documentation](day-4-sentinel-onboarding/README.md)

---

### Day 5 — Analytics Rule Enablement
- Installed Microsoft Defender XDR solution  
- Reviewed built-in detection templates (MITRE ATT&CK mapped)  
- Enabled baseline analytics rules  
- Validated rule configuration and availability  

📁 [Day 5 Documentation](day-5-analytics-rules/README.md)

---

### Day 6 — Defender Telemetry Integration
- Confirmed Defender telemetry ingestion into Sentinel  
- Validated endpoint telemetry tables  
- Queried DeviceProcessEvents and DeviceNetworkEvents  
- Verified SIEM readiness for detection engineering  

📁 [Day 6 Documentation](day-6-defender-telemetry-xdr/README.md)

---

### Day 7 — Custom Detection Rule Development
- Built a custom detection rule using KQL  
- Designed logic to detect suspicious activity  
- Configured rule scheduling and alerting  
- Validated rule behaviour  

📁 [Day 7 Documentation](day-7-custom-detection-rule/README.md)

---

### Day 8 — Detection Engineering
- Created multiple detection rules targeting attacker techniques  
- Covered PowerShell abuse, LOLBins, account creation, and network anomalies  
- Mapped detections to MITRE ATT&CK  
- Explored automation opportunities  

📁 [Day 8 Documentation](day-8-detection-engineering/README.md)

---

### Day 9 — Detection Validation
- Simulated attacker techniques:
  - Encoded PowerShell execution  
  - LOLBin abuse (certutil)  
  - Privilege escalation  
- Triggered and validated alerts  
- Improved detections using entity mapping  
- Observed alert duplication behaviour  

📁 [Day 9 Documentation](day-9-detection-validation/README.md)

---

### Day 9 Part 2 — SOC Investigation Workflow
- Investigated alerts from simulated activity  
- Performed KQL-based threat hunting  
- Analysed process and account behaviour  
- Correlated logs across Defender and Sentinel  
- Classified alerts as True Positive  
- Defined response and remediation actions  

📁 [SOC Investigation Documentation](day-9-part-2-SOC-Investigation/README.md)

---

## Tools & Technologies

- Microsoft Azure  
- Microsoft Defender for Cloud  
- Microsoft Defender for Endpoint (XDR)  
- Microsoft Sentinel (SIEM)  
- Log Analytics Workspace  
- KQL (Kusto Query Language)  
- Windows Server (Azure VM)  
- Azure Networking (VNet, NSG)  
- GitHub  

---

## Future Work

- Improve security posture using Defender recommendations  
- Implement endpoint controls (ASR rules, AppLocker)  
- Explore Conditional Access policies  
- Build automation using Logic Apps  
- Simulate advanced attacker behaviour (persistence, lateral movement)  
- Expand threat hunting using KQL  

A follow-up lab focuses on security controls (AppLocker, DLP, endpoint hardening).

---

## Lab Outcome

This lab demonstrates the end-to-end workflow of detecting and investigating security events in a cloud environment.

- Built and secured an Azure environment using Defender for Cloud  
- Onboarded Microsoft Sentinel and validated telemetry ingestion  
- Developed and tested detection rules using KQL  
- Simulated attacker behaviour to generate alerts  
- Investigated alerts using Defender and Sentinel data  
- Performed triage and validated activity using endpoint telemetry  

The lab highlights how detection logic, telemetry, and alerting work together in practice. It also shows real-world challenges such as alert duplication, timing behaviour, and pre-emptive blocking by Defender.

Overall, this reflects real SOC and cloud security workflows — not just generating alerts, but understanding what happened and deciding what action is required.

---

## Next Steps

A second lab focuses on implementing security controls (AppLocker, DLP, and endpoint hardening) to move from detection into prevention.
