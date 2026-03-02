# Inter-VLAN Routing & Trunking Topology Lab

This project is a network topology designed to model fundamental switching concepts, VLAN configuration, and Router-on-a-Stick (ROAS) architecture for communication between different networks. It has been built and tested using Cisco IOL images on EVE-NG.

## 📖 Core Networking Concepts

To fully understand this lab, it is important to be familiar with the following key networking terminologies and concepts:

* **VLAN (Virtual Local Area Network):** A VLAN logically segments a single physical network into multiple distinct broadcast domains. We use VLANs to improve network security, enhance network performance by limiting broadcast traffic, and logically group devices or departments (e.g., Office, HR, Home) regardless of their physical connection to the switch.
* **Access Port:** A switch port configured to connect an end device (such as a PC, server, or printer). An access port can only belong to one specific VLAN at a time. The traffic entering or exiting this port is untagged.
* **Trunk Port:** A switch port used to interconnect switches or connect a switch to a router. Unlike an access port, a trunk port is designed to carry traffic for multiple VLANs simultaneously across a single physical link. It uses the **IEEE 802.1Q** encapsulation standard to "tag" Ethernet frames with their respective VLAN IDs, ensuring the receiving device knows which network the traffic belongs to.
* **Inter-VLAN Routing & ROAS (Router-on-a-Stick):** By design, devices in different VLANs cannot communicate with each other at Layer 2. To allow VLAN 10 to talk to VLAN 20 or 30, a Layer 3 device (a router) is required. **ROAS** is an efficient routing method where a single physical interface on a router is logically divided into multiple "sub-interfaces." Each sub-interface is assigned to a specific VLAN, tagged with 802.1Q, and acts as the Default Gateway for that network.

## 📌 Topology Diagram
![Topology Diagram](./topology.png) 


## 🏢 Network Architecture & VLAN Table

The network design involves subnetting a `192.168.1.0/24` address space into `/26` subnets (Subnet Mask: `255.255.255.192`).

| VLAN ID | Department | Network Address (Subnet) | Usable IP Range | Default Gateway |
| :--- | :--- | :--- | :--- | :--- |
| **VLAN 10** | Office | `192.168.1.0/26` | 192.168.1.1 - 192.168.1.62 | 192.168.1.62 |
| **VLAN 30** | HR | `192.168.1.64/26` | 192.168.1.65 - 192.168.1.126 | 192.168.1.126 |
| **VLAN 20** | Home | `192.168.1.128/26` | 192.168.1.129 - 192.168.1.190 | 192.168.1.190 |

## 🛠️ Device Roles & Connections

* **R1 (Router):** The core router configured for Inter-VLAN Routing (Router-on-a-Stick) to enable communication between isolated VLANs. It connects directly to the R2 switch.
* **R2 & R3 (Switches):** Although named R2 and R3 in the topology, these devices operate as Layer 2 Switches.
    * Since VLAN 10 spans across both switches, the link between them (R3 e1/0 <-> R2 e0/3) must be configured as an **802.1Q Trunk**.
    * All interfaces connecting to the end devices (PCs) are configured in **Access** mode.

## 🎯 Lab Objectives

The following objectives were achieved while building and configuring this topology:

1.  Creating and naming the required VLANs (10, 20, 30) on the switches.
2.  Configuring the end-device (PC) interfaces as `switchport mode access` and assigning them to their respective VLANs.
3.  Establishing an 802.1Q Trunk link between R2 and R3 to carry VLAN 10 traffic across the switches.
4.  Configuring the physical interface (e0/0) on router R1 with sub-interfaces, applying `encapsulation dot1Q`, and assigning the respective Default Gateway IP addresses.
5.  Verifying end-to-end connectivity between devices in different VLANs using ICMP (ping).

## 🚀 Technologies & Tools Used
* Cisco IOS (IOL Router & Switch Images)
* EVE-NG Network Emulator
* IPv4 Subnetting & Network Design
