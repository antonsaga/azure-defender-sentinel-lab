# Azure Defender & Sentinel Security Lab

This repository documents a hands-on Azure security lab focused on building,
observing, and improving a cloud security monitoring environment using
Microsoft Defender for Cloud and Microsoft Sentinel.

The goal of this lab is to develop and demonstrate practical security
operations skills, including cloud posture management, endpoint protection,
detection engineering, and investigation workflows, using real Azure services
rather than simulated tooling.

---

## Objectives

- Build a controlled Azure environment suitable for security experimentation
- Onboard infrastructure into Microsoft Defender for Cloud
- Observe baseline security posture and recommendations
- Reduce exposure through targeted hardening actions
- Validate security controls and Defender evaluation behaviour
- Incrementally introduce logging, detections, and alerts

This lab mirrors realistic SOC and cloud security workflows rather than
following a purely academic or certification-driven approach.

---

## Lab Structure

The repository is organised into stages to reflect how the environment evolves
over time:

```text
azure-defender-sentinel-lab/
├─ README.md
├─ architecture/
│  ├─ README.md
│  └─ images/
├─ day-1-setup/
│  ├─ README.md
│  └─ images/
├─ day-2-network-hardening/
│  ├─ README.md
│  └─ images/
└─ day-3-defender-investigation/
   ├─ README.md
   └─ images/
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
👉 [`day-1-setup/README.md`](./day-1-setup/README.md)

📐 Architecture overview:  
👉 [`architecture/README.md`](./architecture/README.md)

---

### Day 2 — Network Hardening (NSG + RDP Exposure)
- Reviewed VM networking configuration and NSG inbound rules
- Identified unrestricted inbound RDP (TCP/3389) exposure
- Restricted RDP access to a trusted source IP
- Observed Defender for Cloud re-evaluation and recommendation changes
- Reduced external attack surface while maintaining administrative access

📁 Day 2:  
👉 [`day-2-network-hardening/README.md`](./day-2-network-hardening/README.md)

---

### Day 3 — Defender for Cloud Vulnerability Assessment Validation
- Investigated Defender for Cloud vulnerability assessment recommendations
- Verified Defender for Servers Plan 2 configuration at the subscription level
- Confirmed vulnerability assessment and agentless scanning settings
- Validated that recommendations depend on observed scan telemetry
- Documented scan latency and inventory population behaviour on a newly started VM

📁 Day 3:  
👉 [`day-3-defender-investigation/README.md`](./day-3-defender-investigation/README.md)

---

## Tools & Technologies
- Microsoft Azure
- Microsoft Defender for Cloud
- Microsoft Defender Vulnerability Management
- Windows Server (Azure VM)
- Azure networking (VNet, NSG)
- GitHub for documentation and evidence tracking

---

## Future Work
- Enable and configure Log Analytics workspace
- Onboard Microsoft Sentinel
- Collect and query security telemetry
- Create and tune detection rules
- Generate and investigate security alerts
- Simulate incidents and document response workflows
