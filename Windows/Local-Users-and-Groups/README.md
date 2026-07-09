# Windows Local User & Group Management
## Objective
Create, manage, and remove local users and groups on Windows 11 using both the GUI (Computer Management) and the command line (PowerShell), and verify permission boundaries between standard and administrator accounts.
---
## Environment
- VMware Workstation
- Windows 11
- Computer Management (lusrmgr.msc)
- PowerShell
---
## Steps
### GUI (Computer Management)
1. Created a new standard local user.
2. Added the user to the Administrators group and verified membership.
### CLI (PowerShell)
1. Listed existing local users with `Get-LocalUser`.
2. Created a new local user and verified its creation.
3. Disabled and re-enabled the user account.
4. Added the user to the Administrators group and verified membership.
5. Removed the user from the group and verified removal.
6. Deleted the user and verified it no longer exists.
### Testing
1. Signed into a standard user account.
2. Attempted an administrator-only action to confirm it was blocked by UAC.
---
## Commands Used
```powershell
Get-LocalUser
```
```powershell
New-LocalUser -Name "Fedora"
```
```powershell
Disable-LocalUser -Name "Fedora"
```
```powershell
Enable-LocalUser -Name "Fedora"
```
```powershell
Add-LocalGroupMember -Group "Administrators" -Member "Fedora"
```
```powershell
Get-LocalGroupMember -Group "Administrators"
```
```powershell
Remove-LocalGroupMember -Group "Administrators" -Member "Fedora"
```
```powershell
Remove-LocalUser -Name "Fedora"
```
---
## Skills Practiced
- Windows local user administration
- Windows local group administration
- PowerShell (Get-LocalUser, New-LocalUser, Add-LocalGroupMember, etc.)
- Principle of least privilege
- Verifying changes through the CLI and GUI
## What I Learned
- How to create, disable, enable, and delete local user accounts through both the GUI and PowerShell.
- How to add and remove users from local groups, and how to verify group membership.
- That `New-LocalUser` in PowerShell does not automatically add the account to any group, unlike the GUI, which places new users in the "Users" group by default.
- How Windows enforces the principle of least privilege: standard users are blocked from admin-level actions until elevated through UAC.
- The value of verifying every change (create, modify, delete) instead of assuming a command succeeded.
## Screenshots
The following screenshots show the key stages of user and group management through both the GUI and PowerShell.
 
**GUI**
