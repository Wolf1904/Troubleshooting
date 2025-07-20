# GRUB Bootloader Boot Error After Battery Disconnection

## Problem
After disconnecting the laptop battery, the system failed to boot into Linux. Instead, it showed a GRUB bootloader error or failed to detect the OS.

### Error Seen:
- System boots to a blank screen or BIOS repeatedly
- GRUB not loading properly after BIOS reset

## Root Cause
BIOS was reset to default settings after the battery was disconnected. This re-enabled **Secure Boot**, which blocked the Linux GRUB bootloader from executing.

## Solution: Disable Secure Boot in BIOS

1. **Power off** the system completely.
2. **Enter BIOS/UEFI settings** by pressing `F2`, `F10`, `DEL`, or `ESC` during boot (depends on manufacturer).
3. Navigate to **Boot → Secure Boot**.
4. Set `Secure Boot` to **Disabled**.
5. Save changes and **exit BIOS**.
6. System should now boot properly into GRUB and then into your Linux OS.

## Outcome
Disabling Secure Boot allowed GRUB to execute successfully, restoring normal boot behavior.

## Notes
- Secure Boot often prevents unsigned bootloaders (like some Linux installs) from loading.
- Always check boot settings (UEFI vs Legacy, boot order, etc.) after BIOS reset.

## Tags
`GRUB`, `Secure Boot`, `BIOS Reset`, `Linux Bootloader`, `Troubleshooting`, `UEFI`

