# Troubleshooting Knowledge Base

Welcome to the **Troubleshooting** repository — a structured collection of real-world system issues, their root causes, and practical solutions. This project serves as a personal knowledge base and a reference for IT professionals, system admins, CTF players, and developers dealing with Linux and Windows environments.

---

## Repository Structure

The issues are categorized into two main directories:

```
├── GitHub_Troubleshooting
├── Linux_Troubleshooting
└── Windows_Troubleshooting
```

---

## File Format

Each `.md` file follows this structure:

- **Problem** – What issue was encountered?
- **Cause** – What caused the issue?
- **Solution** – How was it fixed?
- **Notes** – Optional logs or extra commands

---

## GitHub Troubleshooting Topics

| File | Description |
|------|-------------|
| [`github-initial-commit.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/GitHub_Troubleshooting/github-initial-commit.md) | Step-by-step guide to perform the first commit and push to a GitHub repo |
| [`github-authentication-error.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/GitHub_Troubleshooting/github-authentication-error.md) | Fixing authentication failure due to removed password support (use PAT or SSH) |

---

## Linux Troubleshooting Topics

| File | Description |
|------|-------------|
| [`cron-job-automation.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/Linux_Troubleshooting/cron-job-automation.md) | Automating tasks via crontab in Kali |
| [`disk-space-troubleshooting.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/Linux_Troubleshooting/disk-space-troubleshooting.md) | Identifying and freeing up disk usage |
| [`Enum4linux-smbv1-null-session.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/Linux_Troubleshooting/Enum4linux-smbv1-null-session.md) | SMBv1 enumeration with null sessions |
| [`grub-secure-boot-error.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/Linux_Troubleshooting/grub-secure-boot-error.md) | GRUB boot failure due to Secure Boot |
| [`Nslookup-dig-query-type-error.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/Linux_Troubleshooting/Nslookup-dig-query-type-error.md) | DNS query type issues in Kali |
| [`ntfs-volume-dirty-fix.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/Linux_Troubleshooting/ntfs-volume-dirty-fix.md) | Handling "volume is dirty" on NTFS |
| [`Scapy-summary-undefined.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/Linux_Troubleshooting/Scapy-summary-undefined.md) | Scapy crash due to undefined summary |
| [`Smbclient-access-denied-fix.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/Linux_Troubleshooting/Smbclient-access-denied-fix.md) | Samba share permission denial fix |
| [`Swap-usage-kali-linux.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/Linux_Troubleshooting/Swap-usage-kali-linux.md) | Managing and reducing swap usage |

---

## Windows Troubleshooting Topics

| File | Description |
|------|-------------|
| [`windows-domain-join-failure.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/Windows_Troubleshooting/windows-domain-join-failure.md) | Domain controller unreachable (ERROR_NO_SUCH_DOMAIN) |
| [`windows-recovery-access.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/Windows_Troubleshooting/windows-recovery-access.md) | Entering recovery mode using various methods |
| [`windows-server-admin-password-reset.md`](https://github.com/Wolf1904/Troubleshooting/blob/master/Windows_Troubleshooting/windows-server-admin-password-reset.md) | Resetting Windows Server 2016 admin password via registry |

---

## How to Use

1. **Clone the repo:**
   ```bash
   git clone https://github.com/Wolf1904/Troubleshooting.git
   cd Troubleshooting
   ```

2. Navigate by OS:

   - GitHub_Troubleshooting/
   - Linux_Troubleshooting/
   - Windows_Troubleshooting/

3. Open the relevant file and follow the documented fix.

---

## Why This Repo?

Maintaining this repository helps:
- Avoid repetitive Googling
- Speed up debugging in live environments
- Document niche and CTF-prone issues
- Share knowledge with the community

---

## Contributing

Want to add your own fixes or enhance existing ones?
- Fork the repo
- Use the same file format
- Submit a pull request

---

## Contact

- Maintained by: Wolf1904
- Questions or suggestions? Open an issue or PR.

