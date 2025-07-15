Great! Since you specifically work with **Cisco network switches**, here’s a **focused list of lesser-known but *very useful* things, tools, and troubleshooting tips** tailored for Cisco environments — especially valuable when you're working hands-on in operations, troubleshooting, or even doing changes.

These go beyond just `show running-config` and `show interface` — some are *hidden gems* even experienced engineers sometimes overlook:

---

## 🧰 **1. Interface counters tell stories**

* `show interface X counters errors`
  → Look for **input errors, CRC, frame, runts, giants**: often point to cabling, duplex mismatch, or bad optics.
* `show interface X | i rate`
  → Instant view of input/output rate; great for spotting spikes or sudden drops.

---

## 🧠 **2. Check for flaps and history**

* `show interfaces status err-disabled`
  → Shows which ports are disabled automatically (e.g., BPDU Guard, port-security).
* `show log | i LINEPROTO`
  → Find ports that flap (up/down frequently).
* `show interfaces counters last clear`
  → See when counters were last cleared.

---

## 🔍 **3. CDP / LLDP – know your neighbors**

* `show cdp neighbors detail`
  → Learn directly-connected devices, their IP, platform, software version, interface.
* Enable LLDP (`lldp run`) to see non-Cisco devices: `show lldp neighbors detail`.

---

## 🛣 **4. Trace route within the switch**

* `traceroute` command from the switch CLI helps see Layer 3 paths.

---

## 📦 **5. MAC address table is your friend**

* `show mac address-table dynamic vlan X`
  → Find which port has which MAC.
* `show mac address-table address aaaa.bbbb.cccc`
  → Trace where a client is plugged in.

---

## 📚 **6. Understand VLAN and trunking**

* `show vlan brief` → Which ports are in which VLAN.
* `show interfaces trunk` → Which ports are actually trunking, and which VLANs are allowed.

---

## 🔒 **7. Port security (often overlooked)**

* `show port-security interface X` → See violations, configured limits, and learned MACs.
* Troubleshooting sticky MAC issues: remember sticky MACs stay until removed.

---

## ⚡ **8. Spanning Tree insight**

* `show spanning-tree vlan X`
  → See root port, root bridge ID, cost, port states.
* `show spanning-tree summary`
  → Quick view: blocked, forwarding, listening ports.
* Helps find loops or blocked links.

---

## 🧪 **9. Test cables directly**

* On newer switches: `test cable-diagnostics tdr interface X`
* After a few seconds: `show cable-diagnostics tdr interface X`
  → Find cable faults, length, open/short detection.

---

## 📊 **10. CPU & process monitoring**

* `show processes cpu sorted`
* `show processes memory sorted`
  → Helps when the switch is slow; sometimes an SNMP walk or a process is spiking CPU.

---

## 📦 **11. Check TCAM / hardware table usage**

* `show platform tcam utilization`
* `show system resources`
  → When adding ACLs, many forget the switch has limited TCAM space.

---

## 🧰 **12. NetFlow / SPAN for deeper troubleshooting**

* SPAN (port mirroring): `monitor session 1 source interface X`, `monitor session 1 destination interface Y`
  → Capture traffic in Wireshark for detailed analysis.
* NetFlow (if supported): analyze flow data over time.

---

## 🏷 **13. EtherChannel & load balancing**

* `show etherchannel summary`
* `show etherchannel port-channel`
  → Understand which physical links are active and how traffic is distributed.

---

## 🧩 **14. Logs & Syslog**

* `show logging`
  → But better to send logs to a **Syslog server** for history and search.

---

## 📄 **15. Config best practices**

* Use `archive` feature:

  ```
  archive
   path flash:backup-$h-$t
   write-memory
  ```

→ Keeps backups of config after every `write memory`.

* Use `description` on every interface. Future you (and your teammates) will thank you.

---

## ⚙️ **16. Hidden but powerful commands**

| What             | Command                         | Why useful                           |
| ---------------- | ------------------------------- | ------------------------------------ |
| Detailed IP info | `show ip interface brief`       | Status of all interfaces             |
| ACL hit counts   | `show access-lists`             | Shows which ACEs are matching        |
| DHCP snooping    | `show ip dhcp snooping binding` | Find which IP is on which port       |
| Check NTP        | `show ntp status`               | Time sync issues cause log confusion |

---

## 🧩 **17. Practical mindset for Cisco switch troubleshooting**

✅ Always:

* Check physical first (cable, LEDs).
* Look for **duplex & speed mismatches**: `show interfaces status`.
* Confirm VLAN membership & trunking.
* Use `ping` & `traceroute` directly from the switch.
* Correlate with logs: when did it start?

---

If you'd like, tell me:
✅ Exact Cisco models you use (2960, 9200, etc.)
✅ Typical tasks: do you do design, config, monitoring, or mostly troubleshooting?

I can then write you a **tailored cheat sheet** or even a **Python script / tool** to automate some checks (e.g., auto collect `show` commands and parse them).

Want me to do that? 🚀
