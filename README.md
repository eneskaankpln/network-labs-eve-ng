# 🌐 network-labs-eve-ng

Enterprise-style network lab topologies built with EVE-NG. This repository covers essential networking concepts including VLANs, Inter-VLAN Routing, OSPF, ACL, NAT, and troubleshooting scenarios.

---

## 📖 Table of Contents
- [About the Project](#about-the-project)
- [Environment & Requirements](#environment--requirements)
- [Lab Scenarios](#lab-scenarios)
- [How to Use](#how-to-use)
- [Future Additions](#future-additions)

---

## 🎯 About the Project
This repository contains a collection of network topologies designed to simulate real-world enterprise environments. It serves as a practical, hands-on workspace for configuring, testing, and troubleshooting core routing and switching technologies.

## ⚙️ Environment & Requirements
To run these lab topologies successfully, the following setup is recommended:

* **Platform:** EVE-NG (Community or Professional Edition)
* **Recommended Cisco IOL Images:**
  * **Layer 2:** `i86bi_LinuxL2-AdvEnterpriseK9-M_152_May_2018.bin`
  * **Layer 3:** `i86bi_LinuxL3-AdvEnterpriseK9-M2_157_3_May_2018.bin`

## 🛠️ Lab Scenarios
The labs are structured around specific enterprise networking concepts:

* **VLANs & Inter-VLAN Routing:** Layer 2 network segmentation and Layer 3 routing via SVIs and Router-on-a-Stick (ROAS).
* **OSPF:** Single-area and Multi-area Open Shortest Path First implementations, including neighbor adjacencies and route distribution.
* **ACL (Access Control Lists):** Standard and Extended ACLs for secure traffic filtering and network policy enforcement.
* **NAT (Network Address Translation):** Configuration of Static NAT, Dynamic NAT, and PAT (Overload) for internet connectivity.
* **Troubleshooting:** Intentional break-fix scenarios designed to test analytical skills and protocol knowledge.

## 🚀 How to Use
1. Clone this repository to your local machine.
2. Extract and import the provided `.unl` topology files into your EVE-NG web interface.
3. Ensure the required IOL images are installed, licensed (IOL keygen), and mapped correctly in your EVE-NG environment.
4. Start the network nodes and refer to the individual scenario folders for specific configuration tasks and objectives.

## 🐍 Future Additions
* Integration of **Python** network automation scripts (using libraries like Netmiko or NAPALM) for rapid device provisioning and configuration backups.
