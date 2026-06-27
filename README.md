# soc-lab-02-suspicious-powershell-investigation

## 📌 Overview

This project demonstrates how to investigate PowerShell execution using **Sysmon** and **Wazuh** in a simulated Security Operations Center (SOC) environment. The lab focuses on endpoint telemetry collection, process investigation, command-line analysis, and MITRE ATT&CK mapping to emulate Microsoft Defender XDR investigation workflows.

PowerShell is a legitimate Windows administration tool that is frequently abused by attackers for reconnaissance, payload execution, persistence, and defense evasion. This lab demonstrates how a SOC analyst can investigate PowerShell activity and determine whether it is benign or malicious.

---

# 🎯 Objectives

- Generate PowerShell activity on a monitored Windows endpoint
- Capture process creation events using Sysmon
- Collect endpoint telemetry with the Wazuh Agent
- Investigate PowerShell execution within Wazuh
- Analyze parent-child process relationships
- Review command-line arguments
- Build an investigation timeline
- Map activity to MITRE ATT&CK

---

# 🏗️ Lab Architecture

```text
Windows Host
│
├── Windows Defender Antivirus
├── Sysmon
├── Windows Event Logs
├── Wazuh Agent
│
▼
Wazuh Server
│
▼
Wazuh Dashboard
```

---

# 🛠️ Technologies Used

- Wazuh
- Sysmon
- Windows PowerShell
- Windows Event Viewer
- Windows Defender Antivirus

---

# 📋 Lab Activities

- Verified Sysmon service
- Verified Wazuh Agent service
- Generated PowerShell telemetry
- Investigated process creation events
- Reviewed command-line arguments
- Examined parent-child process relationships
- Correlated endpoint telemetry within Wazuh
- Built an investigation timeline
- Mapped findings to MITRE ATT&CK

---

# 🔍 PowerShell Commands Executed

```powershell
Get-Date

Get-Process | Select-Object -First 5

Get-Service | Select-Object -First 5

Get-ChildItem C:\Windows

Get-ExecutionPolicy

Get-ComputerInfo | Select-Object WindowsProductName,WindowsVersion
```

---

# 🔎 Investigation Workflow

1. Verified Sysmon was running.
2. Confirmed the Wazuh Agent was active.
3. Executed several PowerShell commands.
4. Opened the Wazuh Dashboard.
5. Located PowerShell process creation events.
6. Reviewed event details.
7. Identified parent-child process relationships.
8. Examined command-line arguments.
9. Built an execution timeline.
10. Mapped observed behavior to MITRE ATT&CK.

---

# 🎯 MITRE ATT&CK Mapping

| Activity | Technique | ATT&CK ID |
|----------|-----------|-----------|
| PowerShell Execution | Command and Scripting Interpreter: PowerShell | T1059.001 |

---

# 🔍 Investigation Findings

The executed PowerShell commands were successfully recorded by Sysmon and collected by Wazuh.

Analysis confirmed:

- PowerShell was launched interactively by the logged-in user.
- The executed commands performed legitimate system administration tasks.
- No suspicious child processes were spawned.
- No indicators of compromise (IOCs) were identified.
- The observed activity represented normal administrative behavior.

---


# 🚀 Skills Demonstrated

- Endpoint Monitoring
- PowerShell Investigation
- Windows Event Analysis
- Sysmon Event Analysis
- Process Investigation
- Parent-Child Process Analysis
- Threat Hunting
- Wazuh
- MITRE ATT&CK Mapping
- SOC Investigation Workflow

---

## 📄 License

This project is intended for cybersecurity education and defensive security training.
