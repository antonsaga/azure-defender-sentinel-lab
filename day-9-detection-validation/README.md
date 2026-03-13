## Simulation 1 – Suspicious PowerShell Execution

### Objective

The purpose of this simulation was to validate the custom analytics rule **"Suspicious PowerShell Execution Flags"** created in Day 8.

The rule is designed to detect PowerShell executions that contain suspicious command line arguments commonly used by attackers to bypass security controls or execute malicious scripts.

---

### Attack Simulation

To simulate attacker behaviour, a PowerShell command containing suspicious execution flags was executed on the test VM.

Example command executed:


