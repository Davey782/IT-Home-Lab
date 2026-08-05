# Windows Service Management — Print Spooler Startup Recovery
## Objective
Diagnose and fix a Windows service misconfigured with the wrong startup type, using both the GUI (Services) and the command line (PowerShell), and verify the fix through Event Viewer.
---
## Environment
- VMware Workstation
- Windows 11 Pro
- Services (services.msc)
- PowerShell
- Event Viewer (eventvwr.msc)
---
## Scenario
Print Spooler was set to Manual startup instead of Automatic, meaning it would not start on its own after a reboot — a common cause of recurring "printer not working" tickets. The fix requires changing the startup type back to Automatic and confirming the change actually took effect, not just assuming the setting stuck.

---
## Steps
### GUI (Services)
1. Opened Print Spooler Properties and confirmed the broken state: Startup type Manual, Service status Stopped.
2. Changed Startup type to Automatic, applied, and started the service.
3. Confirmed the fixed state: Startup type Automatic, Service status Running.
4. Verified the change was logged in Event Viewer (System log, Service Control Manager source, Event ID 7040).

### CLI (PowerShell)
1. Reverted the service to Manual/Stopped so the fix would demonstrate a real change.
2. Ran `Set-Service` and `Start-Service` to reapply the fix.
3. Ran `Get-Service` to confirm Status: Running.
4. Verified the change was logged in Event Viewer with a new Event ID 7040 entry, timestamped to match the PowerShell fix.

---
## Commands Used
```powershell
Get-Service -Name Spooler
```
```powershell
Set-Service -Name Spooler -StartupType Manual
Stop-Service -Name Spooler
```
```powershell
Set-Service -Name Spooler -StartupType Automatic
Start-Service -Name Spooler
Get-Service -Name Spooler
```

---
## Skills Practiced
- Windows service management (startup type, start/stop)
- PowerShell (Get-Service, Set-Service, Start-Service, Stop-Service)
- Event Viewer log filtering
- Root-cause verification instead of assuming a fix worked

## What I Learned
- Startup type (Manual/Automatic) and current status (Running/Stopped) are separate properties — changing one doesn't automatically change the other.
- Service Control Manager logs startup type changes under Event ID 7040, with the message using "demand start" and "auto start" instead of the GUI's "Manual" and "Automatic" labels.
- Verifying through Event Viewer confirms the change was actually applied and logged by the system, not just reflected in the GUI or terminal output at that moment.
- The same fix can be applied two different ways (GUI and CLI) and independently verified through the same log source.

## Screenshots
The following screenshots show the key stages of diagnosing and fixing the Print Spooler startup issue through both the GUI and PowerShell.
