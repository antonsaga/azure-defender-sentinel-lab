# Azure Defender & Sentinel Security Lab

This repository documents a hands-on Azure security lab focused on building, observing, and improving a cloud security monitoring environment using Microsoft Defender for Cloud and Microsoft Sentinel.

The goal of this lab is to develop and demonstrate practical security operations skills, including cloud posture management, endpoint protection, detection engineering, and incident investigation, using real Azure services rather than simulated tooling.

---

## Objectives

- Build a controlled Azure environment suitable for security experimentation
- Onboard infrastructure into Microsoft Defender for Cloud
- Observe baseline security posture and recommendations
- Incrementally introduce logging, detections, and alerts
- Investigate security findings and document decision-making

This lab is designed to mirror realistic SOC and cloud security workflows rather than follow a purely academic or certification-driven approach.

---

## Lab Structure

The repository is organised into stages to reflect how the environment evolves over time:

```text
azure-defender-sentinel-lab/
├─ README.md
├─ architecture/
│  ├─ README.md
│  └─ images/
└─ day-1-setup/
   ├─ README.md
   └─ images/
   
```


Each stage includes:
- A short explanation of what was done
- Supporting screenshots as evidence
- Notes on observations and design decisions

---

## Current Progress

### Day 1 – Azure Defender for Cloud Setup
- Created a dedicated Azure resource group and virtual network
- Deployed a Windows Server virtual machine
- Enabled Microsoft Defender for Cloud at the subscription level
- Confirmed VM onboarding and visibility in Defender for Cloud
- Reviewed initial security posture and baseline recommendations

📁 Day 1 link:  
👉 [`day-1-setup/README.md`](./day-1-setup/README.md)

📐 Architecture overview:  
👉 [`architecture/README.md`](./architecture/README.md)

---

## Tools & Technologies

- Microsoft Azure
- Microsoft Defender for Cloud
- Windows Server (Azure VM)
- Azure networking (VNet, NSG)
- GitHub for documentation and evidence tracking

---

## Future work

- Enable and configure Log Analytics
- Onboard Microsoft Sentinel
- Generate and investigate security alerts
- Create and tune detection rules
- Simulate security incidents and document response workflows.
