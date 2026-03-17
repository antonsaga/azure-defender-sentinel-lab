# Azure Defender & Sentinel Security Lab

This repository documents a hands-on Azure security lab focused on building,
observing, and improving a cloud security monitoring environment using
Microsoft Defender for Cloud and Microsoft Sentinel.

The goal of this lab is to develop and demonstrate practical security
operations skills, including cloud posture management, endpoint protection,
SIEM onboarding, detection engineering, and investigation workflows, using
real Azure services rather than simulated tooling.

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

The repository is organised into stages to reflect how the environment evolves
over time:

## Lab Structure

The repository is organised into stages to reflect how the environment evolves over time:

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

Each stage includes:
- A concise explanation of actions taken
- Supporting screenshots as evidence
- Observations on Defender behaviour and security posture changes

---

## Current Progress

### Day 1 — Azure Defender for Cloud Setup
- Created a dedicated Azure resource group and virtual network
- Deployed a Windows Server virtual machine
- Enabled Microsoft Defender for Cloud at the subscription level
- Confirmed VM onboarding and visibility in Defender for Cloud
- Reviewed initial security posture and baseline recommendations

📁 Day 1:  
👉 [day-1-setup/README.md](day-1-setup/README.md)

📐 Architecture overview  
👉 [View architecture documentation](architecture/README.md)

---

### Day 2 — Network Hardening (NSG + RDP Exposure)
- Reviewed VM networking configuration and NSG inbound rules
- Identified unrestricted inbound RDP (TCP/3389) exposure
- Restricted RDP access to a trusted source IP
- Observed Defender for Cloud re-evaluation and recommendation changes
- Reduced external attack surface while maintaining administrative access

📁 Day 2:  
👉 [day-2-network-hardening/README.md](day-2-network-hardening/README.md)

---

### Day 3 — Defender for Cloud Vulnerability Assessment Validation
- Investigated Defender for Cloud vulnerability assessment recommendations
- Verified Defender for Servers Plan 2 configuration at the subscription level
- Confirmed vulnerability assessment and agentless scanning settings
- Validated that recommendations depend on observed scan telemetry
- Documented scan latency and inventory population behaviour on a newly started VM

📁 Day 3:  
👉 [day-3-defender-investigation/README.md](day-3-defender-investigation/README.md)

---

### Day 4 — Microsoft Sentinel Onboarding
- Created a dedicated Log Analytics workspace for security monitoring
- Enabled Microsoft Sentinel on the workspace
- Verified successful Sentinel deployment
- Confirmed Sentinel availability through the Microsoft Defender portal
- Validated SIEM readiness prior to telemetry ingestion

📁 Day 4:  
👉 [day-4-sentinel-onboarding/README.md](day-4-sentinel-onboarding/README.md)

---

### Day 5 — Analytics Rule Enablement (Defender XDR → Sentinel)
- Installed the Microsoft Defender XDR solution from Sentinel Content Hub
- Reviewed built-in analytics rule templates mapped to MITRE ATT&CK
- Enabled a small baseline set of Microsoft-provided scheduled analytics rules
- Verified rules are active and correctly mapped (severity / tactics / techniques)
- Used Sentinel Logs (KQL) to confirm table availability (no telemetry yet)

📁 Day 5:  
👉 [day-5-analytics-rules/README.md](day-5-analytics-rules/README.md)

---

### Day 6 — Defender Telemetry & XDR Integration
- Confirmed Defender XDR telemetry ingestion into Microsoft Sentinel
- Validated availability of endpoint telemetry tables within Log Analytics
- Explored Microsoft Defender tables such as DeviceProcessEvents and DeviceNetworkEvents
- Confirmed SIEM readiness for detection engineering and alert generation
- Observed how Defender telemetry becomes searchable through Sentinel KQL queries

📁 Day 6:  
👉 [day-6-defender-telemetry-xdr/README.md](day-6-defender-telemetry-xdr/README.md)

---

### Day 7 — Custom Detection Rule Development
- Created a custom Microsoft Sentinel analytics rule using KQL
- Designed the rule to detect suspicious activity within Defender telemetry
- Configured rule scheduling, severity level, and incident creation settings
- Validated rule deployment within Sentinel Analytics
- Documented rule configuration and monitoring behaviour

📁 Day 7:  
👉 [day-7-custom-detection-rule/README.md](day-7-custom-detection-rule/README.md)

---

### Day 8 — Detection Engineering: Enterprise Rule Pack
- Designed a set of custom Sentinel detection rules targeting common attacker behaviours
- Implemented multiple KQL-based analytics rules mapped to MITRE ATT&CK techniques
- Detected activity including PowerShell abuse, malicious Office macro execution,
  Living-Off-The-Land binary abuse, suspicious account creation, and abnormal network activity
- Documented detection logic and rule behaviour
- Explored potential SOC automation workflows and response playbooks

📁 Day 8:  
👉 [day-8-detection-engineering/README.md](day-8-detection-engineering/README.md)

---

### Day 9 — Detection Validation (Attack Simulation)
- Simulated attacker techniques to trigger detections:
  - Encoded PowerShell execution
  - LOLBIN abuse using certutil
  - Privilege escalation via account creation
- Validated custom analytics rules successfully triggered alerts
- Reviewed alert details and underlying telemetry
- Improved detection rules by adding entity mapping
- Observed duplicate alerts due to rule scheduling and query windows

📁 Day 9:
📁 👉 [day-9-detection-validation/README.md](day-9-detection-validation/README.md)

---

### Day 9 part 2 — SOC Investigation Workflow
- Investigated alerts generated from simulated attack activity
- Performed threat hunting using KQL queries to validate events
- Analysed account creation and privilege escalation behaviour
- Conducted process analysis using Microsoft Defender timeline
- Correlated findings across alerts, logs, and endpoint telemetry
- Classified alerts as a True Positive based on observed activity
- Assessed the potential impact of the behaviour in a real environment
- Defined appropriate response and remediation actions

This stage focuses on the investigation side of security operations, showing how alerts are analysed and validated rather than just generated.

📁 Day 9 part 2:
📁 👉 [day-9-part-2-SOC-investigation/README.md](day-9-part-2-SOC-investigation/README.md)

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
- GitHub for documentation

---

## Future Work

Future work for this lab will look to potentially implement:

- Expand attack simulations (e.g. lateral movement, persistence techniques)
- Implement automated response playbooks using Logic Apps
- Introduce identity-based detections and Conditional Access scenarios
- Develop more advanced threat hunting queries
- Extend investigation workflows across multiple data sources

---

## Lab Outcome

This lab demonstrates an end-to-end security workflow, including:

- Detection engineering using Microsoft Sentinel  
- Validation of alerts through simulated attacker behaviour  
- Threat hunting using KQL queries  
- Endpoint investigation using Microsoft Defender  
- SOC-style triage and decision making  

The project reflects how security analysts work in real environments, moving from detection to investigation and making informed decisions based on evidence.
