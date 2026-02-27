# 🖥️ Lab 01: IPv4 Addressing & Basic Routing

## 🎯 Objective
The primary goal of this lab is to understand basic IPv4 addressing, subnetting, and the role of a router in forwarding traffic between two distinct, directly connected Local Area Networks (LANs). 

## 🗺️ Topology Overview
The network consists of a central router (R1) connecting two separate broadcast domains (LAN 1 and LAN 2). 
* **LAN 1:** Operates on the `192.168.1.0/24` subnet.
* **LAN 2:** Operates on the `192.168.2.0/24` subnet.

 `![Topology](IPv4-Addressing.png)`

## 📊 IP Addressing Table

| Device | Interface | IP Address | Subnet Mask | Default Gateway |
| :--- | :--- | :--- | :--- | :--- |
| **R1** | e0/0 | 192.168.1.254 | 255.255.255.0 | N/A |
| **R1** | e0/1 | 192.168.2.254 | 255.255.255.0 | N/A |
| **VPC10** | eth0 | 192.168.1.1 | 255.255.255.0 | 192.168.1.254 |
| **VPC8**  | eth0 | 192.168.1.2 | 255.255.255.0 | 192.168.1.254 |
| **VPC7**  | eth0 | 192.168.1.3 | 255.255.255.0 | 192.168.1.254 |

| **VPC4**  | eth0 | 192.168.2.4 | 255.255.255.0 | 192.168.2.254 |
| **VPC6**  | eth0 | 192.168.2.5 | 255.255.255.0 | 192.168.2.254 |
| **VPC5**  | eth0 | 192.168.2.6 | 255.255.255.0 | 192.168.2.254 |

## 🛠️ Configuration Tasks

1. **VPC Configuration:** * Assign the correct IPv4 addresses and subnet masks to all VPCs in LAN 1 and LAN 2.
   * Configure the correct Default Gateway for each VPC so they can reach the outside network.
2. **Router Configuration:**
   * Access R1 and configure interface `e0/0` with the IP address `192.168.1.254/24`.
   * Configure interface `e0/1` with the IP address `192.168.2.254/24`.
   * Ensure both interfaces are enabled using the `no shutdown` command.
3. **Verification & Testing:**
   * Verify direct connectivity: Ping from VPC10 to its gateway (192.168.1.254).
   * Verify inter-network routing: Ping from VPC10 (LAN 1) to VPC4 (LAN 2). 

## 🔍 Verification Commands
Use the following Cisco IOS commands on R1 to verify your configuration:
* `show ip interface brief`
* `show ip route`
