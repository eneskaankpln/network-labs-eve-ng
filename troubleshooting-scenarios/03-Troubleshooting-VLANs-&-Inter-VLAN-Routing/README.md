# 🛠️ 🔎 Lab 03: VLANs & Inter-VLAN Routing – Troubleshooting Scenario
![EVE-NG](https://img.shields.io/badge/Platform-EVE--NG-orange?style=flat-square)
![Cisco IOL](https://img.shields.io/badge/Image-Cisco%20IOL-blue?style=flat-square)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange?style=flat-square)

---

* Unlike the original lab, this scenario introduces multiple simultaneous failures, asymmetric behavior, trunk inconsistencies, and Layer 3 misconfigurations.

* You are no longer configuring the network.

* You are operating as a Network Engineer during an outage window.

## 🏢 Enterprise Scenario Context
* The company operates a segmented VLAN architecture:

| VLAN | Department | Subnet           | Default Gateway |
| ---- | ---------- | ---------------- | --------------- |
| 10   | Office     | 192.168.1.0/26   | 192.168.1.62    |
| 20   | Home       | 192.168.1.128/26 | 192.168.1.190   |
| 30   | HR         | 192.168.1.64/26  | 192.168.1.126   |


### The network uses:

* IEEE 802.1Q trunking

* Router-on-a-Stick (ROAS)

* Cisco IOL images on EVE-NG

* After a weekend maintenance window, multiple tickets were opened.
## 🎫 Active Enterprise Incident Tickets
| Ticket ID | Severity | Description                                                                         |
| --------- | -------- | ----------------------------------------------------------------------------------- |
| INC-101   | High     | Office users on SW1 cannot communicate with Office users on SW2. Gateway reachable. |
| INC-102   | Critical | HR department completely isolated. Cannot ping gateway.                             |
| INC-103   | Medium   | Intermittent packet loss between VLAN 10 and VLAN 20.                               |
| INC-104   | Low      | Console flooded with CDP Native VLAN mismatch warnings.                             |
| INC-105   | High     | Home VLAN can reach Office, but Office cannot reach Home.                           |


## 🚨 Scenario Background

* The physical topology remains exactly the same as the original lab. The IP subnetting scheme (`192.168.1.0/24` divided into `/26` subnets) and the intended VLAN assignments are unchanged. 
* However, users are reporting several connectivity issues this morning.

### 🎫 Active Helpdesk Tickets

| Ticket ID | Department | Reported Issue |
| :--- | :--- | :--- |
| **INC-001** | Office (VLAN 10) | "PCs connected to SW1 cannot ping the Office PCs connected to SW2. However, they can reach their Default Gateway." |
| **INC-002** | HR (VLAN 30) | "HR computers cannot access the internet or communicate with the Office and Home departments. Pings to the Default Gateway (`192.168.1.126`) are failing." |
| **INC-003** | Network Admin | "The console lines on SW1 and SW2 are being flooded with CDP (Cisco Discovery Protocol) warning messages every minute, making it hard to type commands." |

---
## 🎯 Objective

### Restore full:

* Layer 2 connectivity

* Inter-VLAN routing

* Trunk consistency

* Bidirectional communication

* Without changing topology.

## 🛠️ Troubleshooting Tasks & Methodology

To solve these tickets, you will need to verify Layer 2 and Layer 3 configurations. Follow this structured approach:

1.  **Verify Layer 2 Connectivity (Switches):**
    * Check if the access ports are assigned to the correct VLANs using `show vlan brief`.
    * Verify the status of the trunk links between switches using `show interfaces trunk`. Look closely at allowed VLANs and Native VLANs.
2.  **Verify Layer 3 Connectivity (Router):**
    * Check the interface status on R1 using `show ip interface brief`.
    * Verify the 802.1Q encapsulation and VLAN mapping using `show run interface e0/0.X`.
    * Ensure the subnet masks and IP addresses match your design table.

---
## 🧩 Hidden Misconfigurations (Multi-Failure Design)
* This lab intentionally includes five simultaneous configuration errors.


