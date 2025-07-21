# Windows 10 Pro Client Unable to Join Windows Server 2016 Domain

## Problem
The Windows 10 Pro virtual machine was unable to join the domain hosted by a Windows Server 2016 domain controller. The client showed the error:

Getting DC name failed: Status = 1355 0x54b ERROR_NO_SUCH_DOMAIN

Additionally, pinging the domain controller from the client resulted in: Destination host unreachable


## Cause
The issue occurred due to **network communication failure** between the client and the domain controller. Specifically:
- Both VMs were on **NAT network mode**, preventing internal communication.
- The **client couldn't resolve or reach the DC** because:
  - They were not on the same subnet.
  - The **firewall** on the DC blocked ICMP and domain traffic.
  - The **client's DNS** settings did not point to the domain controller.
  - **Netlogon and DNS SRV records** may not have been properly registered on the DC.

## Solution

### Step 1: Configure Network Mode
Switch both VMs to a **NAT Network**, **Host-Only**, or **Internal Network** mode to allow communication.

**Example for VirtualBox:**
- Go to `File > Preferences > Network > NAT Networks`
- Create a new NAT Network and assign it to both VMs under their **Network Settings**.

### Step 2: Set Static IPs - Example
Configure static IPs on both machines within the same subnet:
- **DC IP:** `10.0.2.10`
- **Client IP:** `10.0.2.20`
- **Subnet Mask:** `255.255.255.0`
- **Gateway:** `10.0.2.1`
- **DNS on Client:** `10.0.2.10` (DC's IP)

### Step 3: Disable Firewall Temporarily
To verify connectivity, temporarily disable the firewall on both machines:

```bash
netsh advfirewall set allprofiles state off```

Then test:

```bash
ping <DC-IP>
```

If ping works, re-enable firewall and allow ICMP + domain traffic:
- Open `wf.msc`

Enable:
	- File and Printer Sharing (Echo Request - ICMPv4-In)
	- DNS Server
	- Netlogon Service
	- RPC

#### Step 4: Restart Services on DC

```bash
net stop netlogon && net start netlogon
ipconfig /registerdns
```

Verify SRV records:
```bash
nslookup
set type=SRV
_ldap._tcp.yourdomain.local
```

#### Step 5: Join Domain

Once connectivity and DNS resolution are working:

```bash
netdom join %computername% /domain:yourdomain.local /userd:Administrator /passwordd:*
```

---

## Tags  

`Windows` `ActiveDirectory` `DomainJoin` `DNS` `Networking` `WindowsServer2016` `Virtualization` `Firewall` `Netlogon`
