# Troubleshooting Notes

## Issue 1

### Problem

PowerShell events were not visible in the Wazuh Dashboard.

### Possible Cause

- Sysmon was not installed correctly.
- Wazuh Agent was not collecting the Sysmon Operational log.
- Wazuh Agent service was stopped.

### Resolution

Verified:

- Sysmon installation
- Sysmon service status
- Wazuh Agent status
- Wazuh Agent configuration
- Event forwarding configuration

Restarted the Wazuh Agent after confirming the configuration.

---

## Issue 2

### Problem

Process Create (Event ID 1) events were missing.

### Possible Cause

Sysmon configuration did not include Process Create events.

### Resolution

Verified the Sysmon configuration XML and reinstalled Sysmon using the correct configuration file.

---

## Issue 3

### Problem

Commands such as `whoami`, `hostname`, `ipconfig`, and `net` were not recognized.

### Cause

The Windows System PATH variable was missing the default Windows directories.

### Resolution

Restored the following directories to the System PATH:

```text
C:\Windows
C:\Windows\System32
C:\Windows\System32\Wbem
C:\Windows\System32\WindowsPowerShell\v1.0\
C:\Windows\System32\OpenSSH\
```

Restarted PowerShell and verified that all commands executed successfully.

---

## Issue 4

### Problem

Unable to locate PowerShell events in the Wazuh Dashboard.

### Possible Cause

Different Wazuh versions use different interfaces for event analysis.

### Resolution

Verified the Wazuh version and used the appropriate Threat Hunting or Discover interface to locate PowerShell process creation events.

---

# Verification Commands

## Verify Sysmon

```powershell
Get-Service Sysmon64
```

---

## Verify Wazuh Agent

```powershell
Get-Service WazuhSvc
```

---

## Verify Sysmon Events

```powershell
Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational" -MaxEvents 10
```

---

## Generate PowerShell Activity

```powershell
Get-Date

Get-Process | Select-Object -First 5

Get-Service | Select-Object -First 5

Get-ChildItem C:\Windows

Get-ExecutionPolicy

Get-ComputerInfo | Select-Object WindowsProductName,WindowsVersion
```

---

# Outcome

After resolving the identified issues:

- Sysmon successfully generated PowerShell telemetry.
- Wazuh successfully collected endpoint events.
- PowerShell execution was visible for investigation.
- Parent-child process relationships and command-line arguments could be analyzed.
- The lab objectives were successfully completed.
