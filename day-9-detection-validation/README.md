## Simulation 1 – Suspicious PowerShell Execution Detection

### Objective

The goal of this simulation was to validate the custom Microsoft Sentinel analytics rule **"Suspicious PowerShell Execution Flags"** created during Day 8.

This rule detects PowerShell executions containing suspicious command-line arguments commonly used by attackers to bypass security controls or execute malicious scripts.

---

## 1. Simulating Suspicious PowerShell Activity

To simulate attacker behaviour, a PowerShell command containing an encoded payload was executed on the test VM.

This mimics how attackers often hide malicious commands using Base64 encoding.

Example command executed:

'powershell.exe -EncodedCommand ZQBjAGgAbwAgACIAUwBpAG0AdQBsAGEAdABlAGQAIABBAHQAdABhAGMAawAiAA=='


This technique maps to the MITRE ATT&CK technique:

**T1059.001 – Command and Scripting Interpreter: PowerShell**

![PowerShell Command Executed](images/Suspiciouspowershell_sim1.png)

---

## 2. Detection Rule Triggered

After the command was executed, the Microsoft Sentinel analytics rule successfully detected the suspicious activity and generated an alert.

The alert appeared within the **Microsoft Defender Incident portal**, confirming the detection rule was functioning correctly.

![Alert Triggered](images/Alert_firing_sim1.png)

---

## 3. Reviewing Alert Details

Opening the alert reveals additional context about the detected activity.

Key information captured by the detection rule includes:

- Device Name
- Account Name
- Executed Process
- Full PowerShell command line
- Initiating process

This confirms the telemetry captured by the KQL query successfully detected the suspicious PowerShell execution.

![Alert Details](images/Alert_sim1_furtherdetails.png)

---

## 4. Query Results Validation

The alert also provides access to the raw query results that triggered the detection rule.

These results display the telemetry returned from the **DeviceProcessEvents** table, including the exact command that executed on the endpoint.

This allows analysts to verify that the detection rule correctly matched the suspicious command line arguments.

![Query Results](images/Alert_sim1_Queryresults.png)

---

## 5. Detection Rule Improvement – Entity Mapping

During investigation it was observed that the incident graph did not automatically populate related entities such as the device or user responsible for the activity.

This occurred because the original analytics rule did not include **entity mapping configuration**.

To improve investigation capabilities, entity mapping was added to the rule.

The following mappings were configured:

- **Host → DeviceName**
- **Account → AccountName**
- **Process → ProcessCommandLine**

This allows Microsoft Sentinel to automatically associate alerts with relevant devices and users during investigations.

![Entity Mapping Configuration](images/Sim1_alerttuning_entitymapping.png)

---

## 6. Retesting the Detection Rule

After configuring entity mapping, the PowerShell command was executed again to validate the updated rule.

Because the analytics rule runs every **5 minutes** while searching the previous **10 minutes of telemetry**, multiple alerts were generated for the same activity.

This behaviour highlights an important SIEM concept: detection rules may generate duplicate alerts if suppression or tuning is not configured.

![Multiple Alerts Generated](images/Sim1_multiplealertsfiring.png)

---

## 7. Improved Alert Context

The newly generated alert now includes the mapped entities.

Microsoft Sentinel is able to automatically associate the alert with the affected device and user account, improving investigation context for SOC analysts.

This demonstrates how **entity mapping enhances detection rules by providing richer investigation data**.

![Entity Mapping Working](images/Sim1_entitymappingworking.png)

---

## Key Outcome

This simulation successfully demonstrated the full detection validation process:

- Simulating suspicious PowerShell execution
- Triggering a custom Sentinel analytics rule
- Investigating the resulting alert
- Validating telemetry through query results
- Improving the detection rule using entity mapping
- Retesting the rule to confirm improved alert context

This workflow mirrors the real-world process used by SOC analysts when validating and tuning SIEM detection rules.
