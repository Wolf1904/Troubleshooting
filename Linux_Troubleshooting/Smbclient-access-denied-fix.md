# 📁 NT_STATUS_ACCESS_DENIED with smbclient

## 🐛 Problem
Accessing a Samba share using smbclient fails with an NT_STATUS_ACCESS_DENIED error when uploading or retrieving files.

### 💬 Observed:
- Command used: `smbclient //192.168.1.11/Users -U username`
- Uploading a file (e.g., `put badfile.txt`) fails with:
  ```
  NT_STATUS_ACCESS_DENIED opening remote file
  ```

## 🔍 Root Cause
Insufficient permissions for the user account on the Samba server or share misconfiguration in smb.conf.

## 🛠️ Fix Steps

### ✅ Steps Performed:
1. Verified smb.conf share block:
   ```ini
   [Users]
   path = /your/path
   read only = no
   writable = yes
   valid users = username
   ```
2. Ensured correct permissions on directory:
   ```bash
   sudo chown -R username:username /your/path
   sudo chmod -R 755 /your/path
   ```
3. Tested Samba configuration:
   ```bash
   sudo testparm
   ```
4. Restarted Samba services:
   ```bash
   sudo systemctl restart smbd
   ```

