# 🔐 Windows Server 2016 Admin Password Reset (Sticky Keys Hack)

## 🐛 Problem

Administrator password forgotten on a Windows Server 2016 virtual machine. User unable to log in.

## 🧭 Environment

- OS: Windows Server 2016
- Platform: Virtual Machine (VM)
- Access: VM console with ability to boot from ISO

---

## 📌 Cause

Loss of admin credentials with no secondary account available. No built-in password reset tool on login screen.

---

## 🛠️ Solution: Sticky Keys Hack (Using Installation ISO)

### 🧰 Prerequisites

- Windows Server 2016 ISO attached to the VM
- Access to VM boot menu or settings

---

### 🔧 Steps

#### 1. Boot into Windows Setup

- Attach the Windows Server 2016 ISO to the VM.
- Boot from it.
- On the installation screen, click:

#### 2. Identify Windows Partition

At the prompt `X:\Sources>`, run:

```cmd
dir C:\
dir D:\
dir E:\
```

#### 3. Replace Sticky Keys with cmd.exe

```cmd
move D:\Windows\System32\sethc.exe D:\
copy D:\Windows\System32\cmd.exe D:\Windows\System32\sethc.exe
```

#### 4. Reboot the VM
Remove the ISO and boot normally to the Windows login screen.

#### 5. Trigger Sticky Keys and Reset Password

At the login screen, press the Shift key 5 times.

A command prompt opens as SYSTEM. Then run:
```cmd
net user Administrator NewPassword123
```

Replace NewPassword123 with your desired password.

#### 6. (Optional) Restore Original Sticky Keys File

After login, open a new command prompt as Administrator and run:

```cmd
copy D:\sethc.exe D:\Windows\System32\sethc.exe
```
