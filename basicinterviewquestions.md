Here’s a list of **basic technical interview questions and answers** tailored for your role as a **Technical Support Engineer / Network & System Engineer**, including areas like Cisco networking, Linux, firewalls, scripting, and load balancers:

---

### 🔸 **Networking Questions**

**1. What is the difference between a router and a switch?**
**Answer:**
A **router** connects different networks and routes packets between them, often used for connecting to the internet.
A **switch** connects devices within the same network and uses MAC addresses to forward traffic.

---

**2. What is VLAN and why is it used?**
**Answer:**
A **VLAN (Virtual LAN)** segments a physical network into multiple logical networks to improve security, reduce broadcast domains, and better manage traffic.

---

**3. What is HSRP?**
**Answer:**
**HSRP (Hot Standby Router Protocol)** provides high availability by configuring a standby router that takes over if the active router fails.

---

**4. What is Port Security in a Cisco switch?**
**Answer:**
**Port Security** limits the number of MAC addresses on a switch port, helping prevent unauthorized devices from accessing the network.

---

**5. What is a Static Route?**
**Answer:**
A **static route** is a manually configured route that specifies the next hop for traffic to reach a specific destination network.

---

**6. What is the difference between OSPF and BGP?**
**Answer:**
**OSPF** is an interior gateway protocol used within an organization (IGP), while **BGP** is used to route traffic between different organizations (EGP).

---

### 🔸 **Linux/System Questions**

**7. How do you check IP address in Linux?**
**Answer:**
Using `ip a` or `ifconfig` command.

---

**8. How do you check running services in Linux?**
**Answer:**
Using `systemctl status` or `systemctl list-units --type=service`.

---

**9. How to check which process is using a port?**
**Answer:**
Using `netstat -tulnp` or `ss -tulnp`.

---

**10. What does chmod 755 mean?**
**Answer:**
It sets permissions: owner can read/write/execute (7), group and others can read/execute (5).

---

### 🔸 **Firewall & Load Balancer**

**11. What is the role of a firewall?**
**Answer:**
A **firewall** controls incoming and outgoing network traffic based on predefined security rules to protect the network.

---

**12. What is F5 Load Balancer used for?**
**Answer:**
**F5** distributes application traffic across multiple servers to ensure reliability, high availability, and better performance.

---

### 🔸 **Scripting / Automation**

**13. What is Netmiko and Paramiko?**
**Answer:**
**Netmiko** is a Python library to automate SSH-based interactions with network devices.
**Paramiko** is a Python library for SSH connections, often used for automation in both networking and Linux systems.

---

**14. Can you describe a simple automation task you’ve done?**
**Answer:**
Yes, I wrote a Python script using Netmiko to log into multiple Cisco switches, retrieve interface status, and save the output automatically.

---

### 🔸 **General & Behavioral**

**15. How do you handle a situation where a user reports no internet?**
**Answer:**
Start with basic troubleshooting: check cable/Wi-Fi, IP configuration, ping default gateway, DNS settings, and escalate if needed.

---

**16. What tools do you use for troubleshooting?**
**Answer:**
Wireshark, tcpdump, ping, traceroute, netstat, system logs, and Python scripts for automation.

---

Would you like a PDF or Word document version of these Q\&A, or questions specific to Check Point, NetApp, or AWS?
