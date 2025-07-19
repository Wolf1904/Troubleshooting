# 📄 File: enum4linux-smbv1-null-session.md

# 🕵️‍♂️ Enum4linux Enumeration Failure Over SMBv2+

## 🐛 Problem
Enum4linux fails to retrieve information from a target system.

### 💬 Observed:
- Firewall is off
- Target accessible via ping or nmap
- Enum4linux returns little or no useful data

## 🔍 Root Cause
Enum4linux relies on SMBv1 and often null sessions. If SMBv2 or higher is enforced or null sessions are disabled, enum4linux is ineffective.

## 🛠️ Fix Steps

### ✅ Steps Performed:
1. Scanned for supported SMB versions:
   ```bash
   nmap --script smb-protocols -p445 <target_ip>
   ```

2. If SMBv1 not supported:
   - Used smbclient, crackmapexec, or other SMBv2+ compatible tools

3. If null sessions required:
   - Verified that the target allows unauthenticated access:
     ```bash
     smbclient -L //<target_ip> -N
     ```
   - Otherwise, used valid credentials for enumeration
