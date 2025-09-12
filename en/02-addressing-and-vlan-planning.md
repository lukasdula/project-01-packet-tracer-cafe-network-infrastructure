# **2 – Addressing and VLAN Planning**


## 2.1 – Introduction

In this section define the logical division of the network, assign static IP addresses and VLANs to each device.  
The goal is to organize the network, split it into separate, secure segments for both employees and customers, and create a WAN connection toward the simulated internet service provider.

## 2.2 –  IP Addressing and Subnet Overview

Every device in the internal network has a statically assigned IP address. Addresses are allocated according to the VLAN each device belongs to. All VLANs use a /24 subnet mask (255.255.255.0), which corresponds to common settings for small and medium-sized businesses.

| Device    | Description                             | IP Address                  | Subnet Mask   | Default Gateway |
| --------- | --------------------------------------- | --------------------------- | ------------- | --------------- |
| PC-1      | Employees                               | 192.168.10.10               | 255.255.255.0 | 192.168.10.1    |
| PC-2      | Customer                                | 192.168.20.10               | 255.255.255.0 | 192.168.20.1    |
| PC-3      | Customer                                | 192.168.30.10               | 255.255.255.0 | 192.168.30.1    |
| PC-4      | Customer                                | 192.168.40.10               | 255.255.255.0 | 192.168.40.1    |
| Router R1 | Gateway to the internal network         | 192.168.10.1 / 192.168.99.2 | 255.255.255.0 | 192.168.99.1    |
| Router R2 | Edge router simulating an ISP           | 192.168.99.1                | 255.255.255.0 | —               |
| Server    | Simulated Internet services (DNS, HTTP) | 10.10.10.100                | 255.255.255.0 | 10.10.10.1      |

**Note:** In this design, we are not yet using a DHCP server. The purpose is to demonstrate correct manual IP assignment.

---

## 2.3 – VLAN Planning

For the purposes of this project, VLANs (Virtual Local Area Networks) are used to separate traffic between different device types and users in the café. VLAN separation increases security, simplifies management, and helps with more efficient traffic routing in the network.

Each VLAN will have its own IP subnet and will be configured on the router interface using the Router-on-a-Stick method (subinterfaces).

|VLAN ID|VLAN Name|Description / Purpose|Assigned Network|Default Gateway|Assigned Devices|
|---|---|---|---|---|---|
|10|Staff-1|Internal employee network (PC-1)|192.168.10.0/24|192.168.10.1|PC-1, Router R1|
|20|Guest-2|Customer (PC-2)|192.168.20.0/24|192.168.20.1|PC-2|
|30|Guest-3|Customer (PC-3)|192.168.30.0/24|192.168.30.1|PC-3|
|40|Guest-4|Customer (PC-4)|192.168.40.0/24|192.168.40.1|PC-4|

**Note:** R1 is connected to the individual VLANs via a trunk port and uses Router-on-a-Stick (subinterfaces).

---

## 2.4 – Explanation of the connection between R2 and R1

In this project, **Router R2 acts as the edge of the network**, representing a simulated Internet connection.  
It is connected to Router R1, which manages communication between the internal VLANs.

R2 forwards traffic from the simulated Internet (e.g. DNS/HTTP server) to the internal VLANs via R1.  
Likewise, R1 sends traffic from VLANs outward through R2 to reach the server.  
R2 **does not use a default gateway**, as the simulation ends at the server.

---

## 2.5 NAT/PAT in the Project

- NAT/PAT is configured **on Router R1**, translating private VLAN IPs to a public IP.
    
- R2 simply forwards packets between R1 and the server without translation.
    
- Static routes (`ip route`) are configured:
    
    - on R1 towards R2 (to the server network),
        
    - on R2 back to the VLAN network (internal side).
---

Continue to the next chapter: [Basic network configuration](03-basic-network-configuration.md)
















