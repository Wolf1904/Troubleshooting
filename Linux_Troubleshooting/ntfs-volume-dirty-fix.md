# NTFS Volume Fails to Mount on Linux (Dirty Bit Set)

## Problem:

The NTFS volume on `/dev/sdX` fails to mount on a Linux system. Mounting attempts lead to errors such as:


---

## Cause:

This happens when the NTFS partition was not cleanly unmounted from a Windows system. This sets the "dirty bit", which Linux NTFS drivers detect and **refuse to mount** to avoid corruption.

Common scenarios include:
- Unplugging the drive without safely ejecting
- Windows crash or improper shutdown
- Fast Startup or Hibernation enabled in Windows
- Ongoing or incomplete file operations

The volume is effectively "locked" by Windows and marked as needing a filesystem check.

---

## Solution:

### **Preferred (Safe) Method – Clean via Windows**

1. **Connect the drive to a Windows machine.**
2. Open **Command Prompt** as Administrator:
   - Press `Win + S`, type `cmd`
   - Right-click → **Run as administrator**
3. Identify the drive letter (e.g., `E:`), then run:
   ```cmd
   chkdsk E: /f

### **Alternate (Risky) Method – Force Mount in Linux**

Only if you can't access Windows.

1. Create a mount point:
   ```bash
   mkdir -p ~/ntfs_mount
   ```

2. Force mount the volume:
   ```bash
   sudo mount -t ntfs3 -o force /dev/sdX ~/ntfs_mount
   ```

Replace sdX with the correct device name.

Warning: May lead to further corruption if the file system is actually damaged.
