# Inter-City Tech Organizational Network

A comprehensive corporate enterprise network design simulated in Cisco Packet Tracer. This project models a secure, high-availability multi-city network infrastructure connecting corporate branch offices across Islamabad and Rawalpindi.

## 👥 Authors & Credits
* **Nawal Fateh** 
---

## 🗺️ Network Overview & Architecture

The architecture simulates a modern enterprise environment connecting two major geographic locations (Islamabad Office & Rawalpindi Office) using a robust Wide Area Network (WAN) core backbone.

### Core Core Technologies & Technical Features:
1. **Variable Length Subnet Masking (VLSM):** Customized IP allocation using `/30` subnets for router-to-router point-to-point links alongside localized subnets to optimize IPv4 address spacing.
2. **Virtual LANs (VLANs) & Inter-VLAN Routing:** Localized local networks are segmented logically (e.g., VLAN 10 for Islamabad, VLAN 20 for Rawalpindi) to limit broadcast domains and handle multi-floor technical environments.
3. **OSPF Dynamic Routing (Open Shortest Path First):** Configured multi-area OSPF (including Core Area 0 and localized Inter-VLAN Area 3) to ensure dynamic topology updates, fast failover routing, and efficient packet delivery across the WAN.
4. **Network Services Architecture:**
   * **DHCP Server:** Centralized pools mapped to distinct VLANs alongside `ip helper-address` configurations on router gateways for dynamic end-user IP provisioning.
   * **DNS Server:** Domain resolution routing traffic to local web services via custom domain maps (`growhm_tech`).
   * **Web Server (HTTP/HTTPS):** Corporate intranet host accessible seamlessly by end-user machines across cities using domain names.
5. **Advanced Network Security:**
   * **Access Control Lists (ACLs):** Structured to isolate sensitive managerial devices (allowing managers outward visibility but blocking unauthorized incoming access) and strictly blocking specific host ranges from accessing corporate web servers.
   * **Layer 2 Port Security:** Configured directly on host-facing switch interfaces. Set to dynamic MAC learning with violation alerts; tests prove any unknown hardware replacement automatically transitions the target interface to an administrative `err-disabled` (shutdown) state.
6. **Site-to-Site VPN (IPsec):** An encrypted tunneling layer leveraging ISAKMP policies, tailored access-lists, pre-shared keys, and crypto-map injections to guarantee secure corporate transit over untrusted simulated internet spaces.

---

## 🛠️ Step-by-Step Simulation Topology

The simulation project guide outlines 10 core execution phases:
1. **Device Placement & Layer 1 Connectivity:** Wiring physical network switches, central routers, wireless access points, network printers, servers, and corporate endpoints.
2. **Wireless Network Configurations:** Attaching functional wireless modules to PCs/printers and setting secure passwords/SSIDs on Local Access Points.
3. **Visual Mapping & Subnet Plan Definition:** Designing visual network clusters, setting up target boundaries, and computing VLSM matrixes.
4. **IP Addressing Deployment:** Assigning standard interfaces across core routers, localized gateways, and edge printing blocks.
5. **VLAN Segmentation & Sub-Interface Routing:** Restructuring physical trunk links, defining localized access ports, and initiating "Router-on-a-Stick" virtual sub-interfaces.
6. **OSPF Routing Topology Injection:** Activating wildcard network matrices on cross-city routing tables and verifying connectivity via Protocol Data Unit (PDU) trace routing.
7. **Network Server Initialization:** Constructing automated DHCP address scopes and matching web properties against central DNS servers.
8. **Layer 2/Layer 3 Security Protocols Implementation:** Restricting organizational access models through precise standard/extended IP ACL configurations and switchboard port-security.
9. **Site-to-Site VPN Tunnels Activation:** Encrypting high-value multi-city routing data across insecure geographical corridors.
10. **Cross-City Verification & Auditing:** Running end-to-end multi-site network communication health checks (ICMP/Ping audits, web domain access verifications).

---

## 🚀 Deployment & How to Run the Simulation

### Prerequisites
* **Cisco Packet Tracer** (v8.0 or higher recommended to support all implemented VPN and ACL structures).

### Instructions
1. Clone this repository or download the project `.pkt` topology file alongside the `Project_Report_CN.docx` reference guide.
2. Open the network topology file in **Cisco Packet Tracer**.
3. Allow the simulation environment a few moments to converge (indicated when all connection links transition from amber to green).
4. **Test Routing & VPN:** Select any workstation (e.g., a PC on the Islamabad Technical Floor) and attempt to `ping` a target device or router interface inside Rawalpindi. The initial ping might drop due to ARP, but subsequent packets will succeed across the secure IPsec VPN tunnel.
5. **Test Web Services:** Open the Web Browser on any endpoint and navigate to `growhm_tech` to verify DNS resolution and Web Server connectivity.
6. **Verify Port Security:** Unplug an authorized PC from a configured secure switch interface, attach a new Laptop to that exact port, and notice the link immediately shut down upon attempting traffic transmission due to security violation parameters.
