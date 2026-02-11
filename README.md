# Enterprise Network Planning and Configuration

![Network](https://img.shields.io/badge/Network-Architecture-blue.svg?style=for-the-badge)
![Cisco](https://img.shields.io/badge/Cisco-IOS-049fd9.svg?style=for-the-badge&logo=cisco&logoColor=white)
![GNS3](https://img.shields.io/badge/Lab-GNS3-60a5df.svg?style=for-the-badge)

**Course:** Data Routing (Encaminhamento de Dados)  
**Institution:** ISEC - Instituto Superior de Engenharia de Coimbra  
**Year:** 2023/2024  
**Author:** [Fábio Oliveira](https://github.com/fabiooliv3ira)

## Project Overview

This project involves the complete planning, addressing, and configuration of a large-scale enterprise network. The infrastructure consists of a main **Headquarters (Coimbra)** and **six regional branches** (Aveiro, Braga, Funchal, Lisboa, Porto, and Ponta Delgada), all interconnected via 100 Mbps links.

The simulation was performed using **GNS3 v2.2.46** with **Cisco IOU (IOS on Unix)** images to provide a high-fidelity routing environment.

## Technical Implementation

### 1. Multi-Protocol Routing Environment
The network uses a combination of different routing protocols to simulate a complex corporate merger or heterogeneous environment:
*   **Coimbra (HQ):** Uses **OSPF Multi-area** as the core protocol. **Virtual Links** were implemented to bridge areas that were not physically connected to Area 0.
*   **Braga Branch:** Dual-stack **EIGRP (IPv4 & IPv6)**. It includes advanced features like **Policy-Based Routing (PBR)** and **Prefix-lists** to control routing updates.
*   **Lisboa, Porto, & Aveiro:** Configured with **RIPv2** featuring MD5 authentication and optimized auto-summary.
*   **Ponta Delgada:** Implements **OSPF** with area-specific authentication.
*   **Funchal:** Configured with **EIGRP** for IPv4 with custom metrics.

### 2. ISP Connectivity & High Availability (Failover)
*   **Primary ISP Link:** A 1 Gbps connection directly from the Headquarters (Coimbra).
*   **Secondary ISP Link:** A 100 Mbps backup link via the **Braga** branch.
*   **Failover Logic:** The network is configured to use the Braga link only when the primary Coimbra ISP connection fails, ensuring business continuity.

### 3. IPv6 Transition Strategy
In the Braga branch, **Dynamic Tunneling** was implemented to allow IPv6 traffic to traverse the existing IPv4 infrastructure, demonstrating a real-world transition strategy.

### 4. Network Security & Management
*   **Hardening:** All devices feature encrypted passwords, customized login banners (MOTD), and restricted remote management.
*   **Telnet Security:** Access is restricted to a single session per router, secured via a mandatory password policy.
*   **Addressing:** A comprehensive **VLSM (Variable Length Subnet Masking)** plan was developed to efficiently allocate the 194.65.AC.0/21 public range and private segments.

## Topology Metrics
*   **HQ Infrastructure:** 10 Routers.
*   **Branch Infrastructure:** Minimum of 5 Routers and 10 subnets per location.
*   **Simulation Size:** 40+ active nodes.
