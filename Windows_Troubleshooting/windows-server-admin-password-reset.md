# Windows Admin Password Reset via Sticky Keys Exploit

## Problem

Administrator password was forgotten or lost on a Windows machine (Client or Server). No other accounts available, and the user is locked out.

---

## Affected Systems

- Windows Server (2016 / 2019 / 2022)
- Windows Client (Windows 10 / Windows 11)
- Access: Physical or VM console access with ability to boot from ISO

---

## Cause

- Administrator password lost or forgotten
- No secondary login account with administrative privileges
- No access to password reset disk or recovery tool

---

## Solution: Sticky Keys Hack (Offline Command Prompt)

This method replaces the Sticky Keys binary (`sethc.exe`) with `cmd.exe`, allowing SYSTEM-level access from the login screen.

---

## Requirements

- A bootable **Windows installation ISO** (matching or similar version)
- Console or BIOS/UEFI access to **boot from ISO**

---

## Steps

### 1. Boot into Windows Setup

- Attach the Windows ISO to your machine (VM or physical).
- Boot from the ISO.
- On the "Install Windows" screen, press `Shift + F10` to open the command prompt.

---

### 2. Identify Windows System Drive

From the command prompt (`X:\Sources>`), check drives:

```cmd
dir C:\
dir D:\
dir E:\
```
- Identify the drive letter of your Windows system drive (usually `C:`).

Look for the drive containing the Windows\System32 directory.

Let’s assume it's C:\ for the steps below.

### 3. Backup & Replace Sticky Keys with cmd.exe

```cmd
move C:\Windows\System32\sethc.exe C:\
copy C:\Windows\System32\cmd.exe C:\Windows\System32\sethc.exe
```

This replaces the Sticky Keys handler with a command prompt.

### 4. Reboot the System

Exit setup and reboot the system normally.

Remove the ISO (if on VM or physical media).

### 5. Launch SYSTEM Command Prompt

At the login screen, press the Shift key 5 times.

A command prompt opens running as SYSTEM. Now reset the admin password:

```cmd
net user Administrator NewPassword123
```

Replace NewPassword123 with your new desired password.

You can also list users first:

```cmd
net user
```

Then:

```cmd
net user <username> <new_password>
```

### 6. (Optional but Recommended) Restore Original Sticky Keys

After successfully logging in, open a command prompt as Administrator and run:

```cmd
copy C:\sethc.exe C:\Windows\System32\sethc.exe
```

This restores the original Sticky Keys binary for accessibility purposes.

### Warnings

- This method works only if BitLocker is not enabled.
- May be flagged as unauthorized access in enterprise environments.
- Use this responsibly on systems you own or are authorized to work on.

### Notes

This trick works on:
    - Physical machines (using bootable USB/DVD)
    - Virtual machines (with ISO attached)
    - Windows Server & Client editions without Secure Boot + BitLocker

For systems with Secure Boot or BitLocker, alternate recovery methods (like AD password reset, recovery key, or booting into safe mode with known credentials) are required.