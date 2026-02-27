# 🔍 Troubleshooting Lab 01: The Isolated Host & The Silent Gateway

## 📝 The Scenario
The IT department has received multiple tickets from users regarding connectivity issues. Your mission is to restore full communication between LAN 1 and LAN 2 by identifying and fixing misconfigurations.

### **Reported Symptoms:**
1. **VPC10 (LAN 1):** Cannot reach its own Default Gateway.
2. **VPC6 (LAN 2):** Can reach its gateway but cannot communicate with any device in LAN 1.

---

## 🗺️ Topology Overview
We are using the same infrastructure from the core labs, but with intentional configuration errors.
Note: For the full working version and detailed configuration of this topology, please visit the
[View Core Lab Documentation](../../lab-01-IPv4-Addressing/)

![Lab Topolojisi](./IPv4-Addressing.png)

---

## 🕵️ Investigation Phase: Connectivity Testing
To isolate the issue, we performed connectivity tests from different points in the network. The results are captured below:

### **1. Observations from Ping Tests:**

![Ping Testi](./ping-test.png)

```text
VPC8 (LAN 1): Can ping VPC10 (Internal LAN 1 is OK), but cannot reach LAN 2.

VPC10 (LAN 1): Received host not reachable errors when trying to reach other networks.

VPC6 (LAN 2): Can reach its gateway but receives Destination host unreachable when trying to reach LAN 1.
```

### **2. Checking Router R1 (The Silent Gateway)**
We check the interface status on R1 to see if the paths are active.
```text
R1# show ip interface brief
Interface              IP-Address      OK? Method Status                Protocol
Ethernet0/0            192.168.1.254   YES manual administratively down down    <-- 🚩 ISSUE FOUND: Interface is Shutdown
Ethernet0/1            192.168.2.254   YES manual up                    up
```

---

## 🛠️ Root Cause Analysis (RCA)
1. **Incorrect Gateway:** VPC10 has an incorrect Default Gateway address (`.253` instead of `.254`), making it unable to leave its local subnet.
2. **Disabled Interface:** R1's interface `Et0/0` is in a `shutdown` state, blocking all traffic from LAN 1 even if the gateway was correct.

---

## ✅ Resolution Steps

### **Fix 1: Correct VPC10 Gateway**
```text
VPC10> ip 192.168.1.1 255.255.255.0 192.168.1.254
VPC10> save
```

### **Fix 2: Enable R1 Interface**
```text
R1# configure terminal
R1(config)# interface Ethernet0/0
R1(config-if)# no shutdown
R1(config-if)# end
R1# write memory
```

---

## 🧪 Final Verification
Once the fixes are applied, we perform an end-to-end connectivity test.

```text
VPC10> ping 192.168.2.5
84 bytes from 192.168.2.5 icmp_seq=1 ttl=63 time=1.124 ms
84 bytes from 192.168.2.5 icmp_seq=2 ttl=63 time=0.985 ms

**Result:** Inter-VLAN routing is successfully restored! 🎉
```
