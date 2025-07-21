# Accessing Windows Recovery Environment (WinRE)

This guide covers how to access the **Windows Recovery Environment (WinRE)** under different scenarios like boot failure, black screen, and forgotten password.

---

## Normal Method (If System Boots)

1. Click **Start** → **Power**
2. Hold **Shift** and click **Restart**
3. The system will reboot into **WinRE**

---

## Method 1: Force Recovery on Boot Failure

> Use this if Windows won't start or you're stuck on a boot screen.

1. Turn on the PC
2. When the Windows logo appears, **hold the power button** to force shutdown
3. Repeat this process **3 times**
4. On the 4th boot, the system will auto-load **Windows Recovery**

---

## Method 2: Black Screen After Boot

> Screen is black but the system powers on.

### Step 1: Try Force Recovery (same as above)

1. 3x Forced shutdown method → WinRE
2. In WinRE:
   - Select **Advanced options**
   - Choose **Startup Repair** or **System Restore**
   - Or go to **Startup Settings** → **Restart** → Press **4 or 5** to enter Safe Mode

### Step 2: External Display Check

- If using a laptop, connect an **external monitor** to test for display output issues

---

## Method 3: Forgot Windows Password

> Works only for **local accounts**, not Microsoft cloud accounts.

### Step 1: Boot into WinRE

- Use 3x shutdown method **or**
- Boot using a **Windows Installation USB**:
  - Click **Repair your computer**
  - Go to **Troubleshoot** → **Advanced Options** → **Command Prompt**

### Step 2: Replace Accessibility Tool with Command Prompt

```bash
move C:\Windows\System32\utilman.exe C:\
copy C:\Windows\System32\cmd.exe C:\Windows\System32\utilman.exe
```

---

## Tags  

`Windows` `WinRE` `Recovery` `BootIssues` `PasswordReset` `StartupRepair` `SafeMode` `BlackScreen` `Troubleshooting`
