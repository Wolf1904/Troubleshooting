# Swap Usage and Tuning in Kali Linux

## Problem
System performance degraded or out-of-memory errors observed when running multiple tools or browsers.

### Observed:
- System becomes unresponsive under memory pressure
- Applications crash with no clear logs
- Swap usage appears 0 or very high in `free -h`

## Root Cause
Kali Linux uses swap when RAM is exhausted. High swap usage indicates memory pressure; no swap means the system may crash when RAM is full. Default swappiness may not suit VM workloads.

## Swap Management and Fix Steps

### Steps Performed:
1. Checked memory and swap usage:
   ```bash
   free -h
   swapon --show
   ```

2. Adjusted swap usage behavior:
   ```bash
   sudo sysctl vm.swappiness=10
   ```
   - Optional: To make it persistent, add to /etc/sysctl.conf:
     ```
     vm.swappiness=10
     ```

3. (Optional) Created swap file if swap is missing:
   ```bash
   sudo fallocate -l 2G /swapfile
   sudo chmod 600 /swapfile
   sudo mkswap /swapfile
   sudo swapon /swapfile
   echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
   ```

---

## Tags  

`Linux` `KaliLinux` `Swap` `MemoryManagement` `PerformanceTuning` `Sysctl` `VMOptimization` `OutOfMemory`
