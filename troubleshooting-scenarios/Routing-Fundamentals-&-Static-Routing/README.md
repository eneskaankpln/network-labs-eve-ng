# 🛠️ Troubleshooting Scenario: Multi-Hop Static Routing & Redundancy
### *Lab 02: Core Forwarding & Path Selection*

![EVE-NG](https://img.shields.io/badge/Platform-EVE--NG-orange?style=flat-square)
![Cisco IOL](https://img.shields.io/badge/Image-Cisco%20IOL-blue?style=flat-square)
![Difficulty](https://img.shields.io/badge/Difficulty-Intermediate-orange?style=flat-square)

---

## 📝 Scenario Overview
The organization has deployed a square-topology core network connecting two main sites: **Blue LAN (192.168.1.0/24)** and **Green LAN (192.168.4.0/24)**. The network is designed with redundancy, allowing traffic to flow either through the upper path (R1-R3) or the lower path (R1-R2-R4).

Currently, the junior administrator has applied several static routes, but **VPC7 cannot reach VPC8**, and the redundancy is not working as expected.

---

## 🗺️ Topology Overview
We are using the same infrastructure from the core labs, but with intentional configuration errors.
Note: For the full working version and detailed configuration of this topology, please visit the
[View Core Lab Documentation](../../lab-02-Routing-Fundamentals-&-Static-Routing/)

![Lab Topolojisi](./routing-topology.png)

---

## 🚩 Problem Statements
1.  **Connectivity Failure:** `VPC7` (192.168.1.1) cannot ping `VPC8` (192.168.4.1).
2.  **Partial Reachability:** `Router1` can ping `10.0.1.1` (R3), but cannot reach the interface `10.0.22.1` on the same router.
3.  **Redundancy Issue:** When the link between `R1` and `R3` is manually disabled, the traffic does not automatically switch to the path through `R2`.

---

## 🛠️ Fault Inventory (The "Bugs" to Fix)
* **Next-Hop Mismatch:** On `Router1`, the route to `192.168.4.0/24` points to a non-existent IP in the `10.0.1.0/30` subnet.
* **Missing Return Routes:** `Router4` and `Router3` do not have a route back to the `192.168.1.0/24` network.
* **Subnet Mask Error:** The link between `R3` and `R4` (`10.0.22.0/30`) has an incorrect mask on one side, causing an ARP failure.
* **Floating Static Route:** The backup route through `R2` has the default AD (1), preventing it from acting as a standby.

---

## 🛰️ Topology Details
| Segment | Network | Key IPs |
| :--- | :--- | :--- |
| **Blue LAN** | `192.168.1.0/24` | VPC7: .1, R1-e0/2: .254 |
| **Green LAN** | `192.168.4.0/24` | VPC8: .1, R4-e0/0: .254 |
| **R1 - R3 Link** | `10.0.1.0/30` | R1-e0/1: .2, R3-e0/1: .1 |
| **R1 - R2 Link** | `10.0.34.0/30` | R1-e0/0: .1, R2-e0/0: .2 |
| **R2 - R4 Link** | `10.0.12.0/30` | R2-e0/1: .1, R4-e0/1: .2 |
| **R3 - R4 Link** | `10.0.22.0/30` | R3-e0/2: .2, R4-e0/2: .1 |

---

## 🔍 Troubleshooting Steps
1.  **Check Neighbors:** Use `show cdp neighbors` to verify if all links are physically connected to the correct ports as per the diagram.
2.  **Verify Gateways:** Ensure VPCs have their default gateways set to `.254`.
3.  **Trace the Route:** Run `traceroute 192.168.4.1` from `VPC7` and see where it stops.
4.  **Analyze Routing Table:**
    ```bash
    R1# show ip route static
    R1# show ip route 192.168.4.1
    ```

---

## ✅ Success Criteria
- [ ] Successful ping from `VPC7` to `VPC8`.
- [ ] `traceroute` confirms traffic follows the path: `R1 -> R3 -> R4`.
- [ ] If `R1-e0/1` is shut down, `traceroute` should show the path through `R2`.

---

