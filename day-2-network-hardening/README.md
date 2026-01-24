# Day 2 — Network Hardening (NSG + RDP exposure)

## Goal
Reduce exposure of the VM by tightening inbound access (RDP/3389) and aligning with Defender for Cloud recommendations.

## What I’m focusing on today
- Confirm whether the VM has a Public IP and whether RDP is exposed to the internet
- Review NSG inbound rules (especially 3389)
- Apply a safer configuration (least exposure that still lets me manage the VM)
- Capture before/after evidence and the Defender recommendation status

## Evidence to capture (screenshots)
- VM Networking page showing Public IP + NSG name
- NSG inbound rule list showing the RDP rule (before)
- Updated rule / new approach (after)
- Defender for Cloud recommendation page before/after (if it changes)

## Notes / decisions
- Why I changed the rule the way I did
- Any trade-offs (e.g., keeping RDP open temporarily vs locking it down fully)


## Initial findings

The VM is currently assigned a Public IP and allows inbound RDP (TCP/3389) from any source via an NSG rule.

This configuration allows remote administrative access but also increases exposure at the network layer.

### Evidence
![RDP exposed via NSG](./images/RDPopen.png)
