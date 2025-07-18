Sure! Here’s how to **find the WWPN (World Wide Port Name)** of your server’s HBA (Fibre Channel) ports, depending on your operating system.

---

## ✅ **Linux**

### Option 1: Using `sysfs` (built-in, no extra tools)

```bash
cat /sys/class/fc_host/host*/port_name
```

Output will look like:

```
0x10000090fa1b2c3d
0x10000090fa1b2c4d
```

These are your WWPNs (one per HBA port).

---

### Option 2: Using `systool` (part of `sysfsutils`)

First, install if needed:

```bash
sudo yum install sysfsutils    # RHEL/CentOS
sudo apt install sysfsutils    # Debian/Ubuntu
```

Then:

```bash
systool -c fc_host -v | grep port_name
```

---

## ✅ **Windows**

### Option 1: Using PowerShell

```powershell
Get-WmiObject -Namespace "root\WMI" -Class MSFC_FCAdapterHBAAttributes | 
    ForEach-Object {
        $_.NodeWWN | ForEach-Object { "{0:X}" -f $_ }
        $_.PortWWN | ForEach-Object { "{0:X}" -f $_ }
    }
```

### Option 2: Use `HBAInfo` utility

Vendors like QLogic, Emulex, or Broadcom have tools like:

* **QConvergeConsole** (for QLogic)
* **OneCommand Manager** (for Emulex)

These tools show WWPN, WWNN, driver versions, and link status in GUI.

---

## ✅ **VMware ESXi** (if your server is a hypervisor)

```shell
esxcli storage core adapter list
```

or

```shell
esxcfg-scsidevs -a
```

---

## 📌 **Tip:**

* `WWPN` → World Wide Port Name (unique to the port).
* `WWNN` → World Wide Node Name (unique to the node, i.e., the HBA).

---

If you want, tell me your **OS and HBA vendor/model**, and I can give you the exact command or screenshot.
Would you like that?
