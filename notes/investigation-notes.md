# Investigation Notes

## Investigation Objective

Investigate PowerShell execution using Sysmon telemetry collected by Wazuh. Analyze process creation events, parent-child relationships, command-line arguments, and determine whether the observed activity is benign or suspicious.

---

# Environment

## Operating System

- Windows 11

## Monitoring Tools

- Sysmon
- Wazuh Agent

## Analysis Platform

- Wazuh Dashboard

---

# Commands Executed

```powershell
Get-Date

Get-Process | Select-Object -First 5

Get-Service | Select-Object -First 5

Get-ChildItem C:\Windows

Get-ExecutionPolicy

Get-ComputerInfo | Select-Object WindowsProductName,WindowsVersion
```

---

# Investigation Steps

## Step 1

Verified that the Sysmon service was running successfully.

---

## Step 2

Verified that the Wazuh Agent service was running and forwarding endpoint telemetry.

---

## Step 3

Executed multiple PowerShell commands to generate endpoint activity.

---

## Step 4

Opened the Wazuh Dashboard and searched for PowerShell process creation events.

Collected the following information:

- Process Name
- Parent Process
- User
- Process ID
- Parent Process ID
- Command Line
- Timestamp
- Image Path
- SHA256 Hash (if available)

---

## Step 5

Analyzed the collected telemetry.

Observed:

- Interactive PowerShell session
- Legitimate administrative commands
- Normal parent-child process relationship
- No encoded PowerShell commands
- No suspicious child processes

---

# Timeline Reconstruction

| Time | Activity |
|------|----------|
| HH:MM:SS | powershell.exe started |
| HH:MM:SS | Get-Date executed |
| HH:MM:SS | Get-Process executed |
| HH:MM:SS | Get-Service executed |
| HH:MM:SS | Get-ChildItem executed |
| HH:MM:SS | Get-ExecutionPolicy executed |
| HH:MM:SS | Get-ComputerInfo executed |

---

# MITRE ATT&CK Mapping

| Activity | Technique | ATT&CK ID |
|----------|-----------|-----------|
| PowerShell Execution | Command and Scripting Interpreter: PowerShell | T1059.001 |

---

# Investigation Findings

- Sysmon successfully captured PowerShell process creation events.
- Wazuh successfully ingested endpoint telemetry.
- Parent-child process relationships were clearly visible.
- Command-line arguments were available for investigation.
- No Indicators of Compromise (IOCs) were identified.
- Activity was classified as legitimate administrative behavior.

---

# Analyst Assessment

**Severity:** Informational

**Threat Level:** Low

**Status:** Closed

## Conclusion

The observed PowerShell activity represented normal administrative usage performed by an authorized user. No suspicious behavior, persistence mechanisms, or malicious execution patterns were detected.
