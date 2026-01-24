# Day 2 — Network Hardening (NSG + RDP Exposure)

## Objective
Reduce unnecessary network exposure on the VM by reviewing and tightening NSG inbound rules, aligned with Defender for Cloud recommendations.

## Initial State
- VM assigned a Public IP
- Inbound RDP (TCP/3389) allowed from any source
- Defender for Cloud flagged this as a high-severity recommendation

## Change Implemented
Restricted inbound RDP (TCP/3389) by limiting the NSG rule to my public IP address instead of allowing access from any source.

## Evidence — Before
![RDP open to any source](./images/RDPopen.png)

## Evidence — After
![RDP restricted](./images/RDPChange.png)

## Defender for Cloud Status
Defender for Cloud continues to flag the recommendation as unhealthy because the VM still has a Public IP and RDP enabled. This reflects Defender’s binary evaluation model rather than partial risk reduction.

## Outcome
Inbound exposure was reduced while maintaining administrative access. This represents a risk-reduction step rather than full remediation.

## Next Steps
- Evaluate Just-In-Time (JIT) VM access
- Consider Azure Bastion or removing the Public IP
- Observe Defender recommendation status after further changes
