# Day 2 — Network Hardening (NSG + RDP Exposure)

## Goal
Reduce exposure of the VM by tightening inbound access (RDP/3389) and aligning with Microsoft Defender for Cloud recommendations.

## Initial state (baseline)
The virtual machine is assigned a Public IP address and allows inbound RDP (TCP/3389) from any source via a Network Security Group rule.

This configuration enables remote administration but increases exposure at the network layer, which is flagged by Defender for Cloud as a high-risk recommendation.

## Evidence — RDP exposed
![RDP exposed via NSG](./images/RDPopen.png)

## Changes applied
Restricted inbound RDP (TCP/3389) by limiting the NSG rule to my public IP address instead of allowing traffic from any source.

## Evidence — RDP restricted
![RDP restricted](./images/RDPChange.png)

## Outcome
Inbound exposure was reduced while maintaining administrative access. This change aligns with Microsoft Defender for Cloud network hardening recommendations.


