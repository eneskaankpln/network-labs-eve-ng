# 🛠️ Network Troubleshooting Scenarios

Welcome to the Network Troubleshooting Scenarios repository. 

Building a network from scratch is only half the job of a Network Engineer; the real challenge lies in identifying, isolating, and resolving issues when things go wrong. This repository is dedicated to intentional "break-fix" scenarios, designed to simulate real-world network outages and misconfigurations in an enterprise environment.

## 🎯 Objective
The primary goal of this repository is to demonstrate a systematic approach to network troubleshooting. Rather than relying on guesswork, each lab focuses on utilizing proper verification commands, packet analysis, and logical deduction to find the root cause of an issue.

## 🧠 Troubleshooting Methodology
For every scenario in this repository, the following structured approach is applied:
1. **Define the Problem:** Understand the reported issue (e.g., "Host A cannot ping Host B").
2. **Gather Information:** Use `show` commands (`show ip route`, `show ip interface brief`, `show mac address-table`) and ICMP tools (`ping`, `traceroute`).
3. **Analyze & Isolate:** Trace the path layer by layer (Layer 1 to Layer 3) and analyze packet captures (Wireshark) to pinpoint where the traffic drops.
4. **Resolve the Issue:** Apply the specific configuration or fix to restore connectivity.
5. **Verify:** Confirm the initial problem is solved and no new issues were created.

## ⚙️ Environment
All broken lab scenarios are built and tested using **EVE-NG** with standard Cisco IOL images. 
* To practice these scenarios, download the provided `.unl` files, import them into your EVE-NG environment, and start troubleshooting!

## 📂 Scenario Index
*(Click on a scenario to view the topology, the reported issue, and the step-by-step resolution.)*

* 🖧 **[Lab 01: IPv4 Addressing Issues](./troubleshooting-scenarios/01-IPv4-Addressing-Issues/)** - *Loaded !*
* 🔄 **[Lab 02: VLAN & Trunking Misconfigurations](./troubleshooting-scenarios/Routing-Fundamentals-&-Static-Routing/)** - *Loaded*
* 🛣️ **[VLANs & Inter VLAN Routing](./troubleshooting-scenarios/)** - *Planned*
* 🛡️ **[Lab 04: ACL Traffic Blocking Analysis](./troubleshooting-scenarios/)** - *Planned*

---
*"A good engineer knows how to configure a protocol. A great engineer knows how to fix it when it breaks."*
