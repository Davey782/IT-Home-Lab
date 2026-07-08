# Windows Remote Desktop (RDP)

## Objective

Remotely connect from a Kali Linux virtual machine to a Windows 11 virtual machine using RDP.

---

## Environment

- VMware Workstation
- Windows 11
- Kali Linux
- xfreerdp

---

## Steps

1. Enabled Remote Desktop on Windows.
2. Found the Windows IP address.
3. Connected from Kali using xfreerdp.
4. Verified successful remote connection.

---

## Issue Encountered

The RDP connection failed.

### Cause

Windows Defender Firewall blocked inbound RDP traffic.

### Solution

Enabled the Windows Firewall rules for Remote Desktop.

---

## Commands Used

```bash
ping -c
```

```bash
ipconfig
```

```bash
xfreerdp /v:<IP> /u:<username> /p:<password> /clipboard /dynamic-resolution
```

```bash
query user
```

---

## Skills Practiced

- Windows administration
- Remote Desktop Protocol (RDP)
- Windows Firewall
- Troubleshooting
- Remote administration from Linux
