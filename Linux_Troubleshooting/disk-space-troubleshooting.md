# Linux Disk Space Draining — General Troubleshooting Guide

## Problem
System storage is draining rapidly or unexpectedly full.

### Observed:
- System slowdowns
- Errors like “No space left on device”
- Unexpectedly high disk usage in certain directories

---

## Step-by-Step Diagnosis

### 1. Check overall disk usage
```bash
df -h
```

### 2. Identify which top-level directory is taking space

```bash
sudo du -h --max-depth=1 / | sort -hr | head -n 10
```

### 3. Dig deeper into the heaviest directory

Example for /var:

```bash
sudo du -h --max-depth=1 /var | sort -hr
```

---

#### 🔹 Log files

```bash
sudo journalctl --disk-usage
sudo journalctl --vacuum-size=200M
```

To automate log cleanup:

  ``` bash
￼ sudo crontab -e
  @weekly journalctl --vacuum-size=200M
  ```

---

#### 🔹 Old kernels

List:

  ```bash
  dpkg --list | grep linux-image
  ```

Remove unused ones carefully:

  ```bash
  sudo apt purge linux-image-x.x.x-xx-generic
  ```

---

#### 🔹 Trash & Downloads

```bash
rm -rf ~/.local/share/Trash/*
rm -rf ~/Downloads/*
```

---

#### 🔹 Large orphaned packages

```bash
sudo apt autoremove
```

---

#### Tools for Space Management

- GUI Tool:
```bash
sudo apt install baobab
baobab  # GNOME Disk Usage Analyzer
```

- CLI Alternative:
```bash
sudo ncdu /
```

Use ncdu to explore and delete large files interactively.

---

### Prevention Tips:

  - Regularly run: sudo du -sh /*
  - Set log rotation policies in /etc/logrotate.conf
  - Use LVM or partitions wisely for separation
  - Monitor disk with cron + alerts
