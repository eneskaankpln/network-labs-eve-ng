# 🛠️ 🔎 Lab 03: VLANs & Inter-VLAN Routing – Troubleshooting Scenario
![EVE-NG](https://img.shields.io/badge/Platform-EVE--NG-orange?style=flat-square)
![Cisco IOL](https://img.shields.io/badge/Image-Cisco%20IOL-blue?style=flat-square)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange?style=flat-square)

---

* This document provides a structured troubleshooting scenario for the VLANs & Inter-VLAN Routing (ROAS) lab.
* The goal is to simulate real-world misconfigurations and methodically identify, isolate, and resolve them using Cisco IOS verification commands.

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

## 🛑 Spoiler Alert: The Misconfigurations (Answer Key)

*If you want to solve the lab yourself, stop reading here! If you are ready to check your answers or need a hint, expand the sections below.*

### Resolving INC-001 (Office PC to Office PC Failure)
**The Problem:** The junior admin accidentally removed VLAN 10 from the allowed VLAN list on the trunk link of SW1.
**Diagnosis:** Running `show interfaces trunk` on SW1 reveals that only VLANs 20 and 30 are allowed on the trunk.
**The Fix on SW1:**
```text
SW1# configure terminal
SW1(config)# interface e1/0
SW1(config-if)# switchport trunk allowed vlan add 10
```
