# 🌐 network-labs-eve-ng

Enterprise-style network lab topologies built with EVE-NG. This repository covers essential networking concepts including VLANs, Inter-VLAN Routing, OSPF, ACL, NAT, and troubleshooting scenarios.

---

## 📖 Table of Contents
- [About the Project](#about-the-project)
- [Environment & Requirements](#environment-requirements)
- [Lab Scenarios](#lab-scenarios)
- [How to Use](#how-to-use)
- [Future Additions](#future-additions)

---

<a id="about-the-project"></a>
## 🎯 About the Project
This repository contains a collection of network topologies designed to simulate real-world enterprise environments. It serves as a practical, hands-on workspace for configuring, testing, and troubleshooting core routing and switching technologies.

<a id="environment-requirements"></a>
## ⚙️ Environment & Requirements
To run these lab topologies successfully, the following setup is recommended:

* **Platform:** EVE-NG (Community or Professional Edition)
* **Recommended Cisco IOL Images:**
  * **Layer 2:** `i86bi_LinuxL2-AdvEnterpriseK9-M_152_May_2018.bin`
  * **Layer 3:** `i86bi_LinuxL3-AdvEnterpriseK9-M2_157_3_May_2018.bin`

<a id="lab-scenarios"></a>
<a id="lab-scenarios"></a>
## 🛠️ Lab Scenarios

### ✅ Currently Available
* **IPv4 Addressing:** Subnetting, VLSM, and core IP addressing concepts.
* **Routing Fundamentals:** Static routing, default routes, and basic routing table operations.
* **VLANs & Inter-VLAN Routing:** Layer 2 network segmentation and Layer 3 routing via SVIs and Router-on-a-Stick (ROAS).

### 🚀 Coming Soon!
* **DTP & VTP:** Dynamic Trunking Protocol and VLAN Trunking Protocol configurations.
* **STP (Spanning Tree Protocol) & Features:**
* **Rapid Spanning Tree Protocol (RSTP)**
* **EtherChannel:** Link aggregation for Layer 2 and Layer 3.
* **Dynamic Routing Fundamentals**
* **RIP & EIGRP:** Distance vector and advanced distance vector routing protocols.
* **OSPF (Open Shortest Path First):**
* **First Hop Redundancy Protocols (FHRP):** HSRP, VRRP, and GLBP concepts.

<a id="how-to-use"></a>
## 🚀 How to Use
1. Clone this repository to your local machine.
2. Extract and import the provided `.unl` topology files into your EVE-NG web interface.
3. Ensure the required IOL images are installed, licensed (IOL keygen), and mapped correctly in your EVE-NG environment.
4. Start the network nodes and refer to the individual scenario folders for specific configuration tasks and objectives.

<a id="future-additions"></a>
## 🐍 Future Additions
* Integration of **Python** network automation scripts (using libraries like Netmiko or NAPALM) for rapid device provisioning and configuration backups.
