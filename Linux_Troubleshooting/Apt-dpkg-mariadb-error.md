# 📦 apt install / dpkg broken due to MariaDB

## 🐛 Problem
Running `apt install -f` or `apt --fix-broken install` failed due to MariaDB-related errors.

### 💬 Observed:
- Errors such as:
  ```
  update-alternatives: error: alternative path /etc/mysql/mariadb.cnf doesn't exist
  ```
- Package mariadb-common or mariadb-server left unconfigured

## 🔍 Root Cause
MariaDB installation is broken or partially configured, causing dpkg to fail during alternative management. Files may be missing from /etc/mysql due to interruption.

## 🛠️ Fix Steps

### ✅ Steps Performed:
1. Reconfigured dpkg manually:
   ```bash
   sudo dpkg --configure -a
   ```

2. Cleaned and updated package lists:
   ```bash
   sudo apt clean
   sudo apt update
   ```

3. Fixed broken dependencies:
   ```bash
   sudo apt install -f
   ```

4. If issue persisted, purged and reinstalled MariaDB:
   ```bash
   sudo apt purge mariadb*
   sudo apt autoremove
   sudo apt install mariadb-server
   ```
