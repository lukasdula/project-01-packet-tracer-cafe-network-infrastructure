
# Network Infrastructure for a Small Café

## Introduction and Objectives

This project presents the design, configuration, and testing of a small business network for a café.  
The main goal is to create a functional, separated, and secure environment for two operational parts:

- **Internal employee network** – access to the main computer (cash register system) and the café’s internal devices (router, modem, switch), including the ability to manage customer computers.
    
- **Public customer network** – access through three public computers connected to the internet, without the possibility of entering the internal network.
    

The network was manually configured in **Cisco Packet Tracer** using the CLI interface. Traffic is separated using **VLANs**, and the connection between the router and the switch is configured with the **Router-on-a-Stick** method.

For internet connection simulation, **NAT/PAT** was configured towards router R2, which represents the internet service provider. The setup also includes basic server infrastructure (HTTP/DNS) for connectivity tests.

The network is secured using **device access passwords, VLAN separation, and restricted access between segments**, ensuring safe operation and protection against unauthorized access.

## Project Structure (Chapters)

1. [Network topology and used devices](01-network-topology-and-devices.md)
2. [Addressing and VLAN planning](02-addressing-and-vlan-planning.md)
3. [Basic network configuration](03-basic-network-configuration.md)
4. [VLANs and subinterfaces](04-vlans-and-subinterfaces.md)
5. [NAT & PAT](05-nat-and-pat.md)
6. [Internet and DNS](06-internet-and-dns.md)
7. [Network security](07-network-security.md)
   - Local user and password for privileged mode  
   - Login warning (MOTD banner)  
   - Telnet access security (VTY lines)  
   - Port Security on client ports  
   - Administratively shutting down unused ports  
   - Basic ACL to limit traffic between VLANs  
8. [Connectivity testing](08-connectivity-testing.md)
9. [Troubleshooting](09‑troubleshooting.md)
   - 9.1 Incorrect VLAN ID assignment on subinterface  
   - 9.2 NAT/PAT overload misconfigured on wrong interface  
   - 9.3 ACL – wrong rule order blocking communication  
10. [Summary and conclusion](10-summary-and-conclusion.md)

## CLI device access

For lab purposes, the following credentials were configured on the network devices. They allow access to the CLI and, after authentication, to privileged mode:

Username (console + Telnet): `cafeadmin`

User password: `Espresso25`

Enable secret (privileged mode): `Arabickashot25`

For the purpose of this project, simpler thematic passwords are used. In real deployment, stronger and longer passwords would be applied (12+ characters, mix of letters, numbers, and special symbols).

## Tools Used

- Cisco Packet Tracer (version 8.2+) – network simulation environment  
    
- Visual Studio Code / Obsidian – writing and editing documentation  
    
## How to Run the Project

1. Open the `.pkt` file in Cisco Packet Tracer (8.2+).  
2. Follow the project folders `01–10`.  

## Key Project Features

- Static IP addresses and clear VLAN structure
    
- Router-on-a-Stick configuration
    
- NAT/PAT for access to the simulated internet
    
- HTTP and DNS server for testing
    
- Basic network security  
    
- Simulated errors and their solutions in the Troubleshooting section  
    


## Author's Note

This project is part of my **study portfolio** and practical preparation for the **CCNA I** course.  
During its creation, I learned key networking principles, from planning and addressing to configuration, diagnostics, and troubleshooting.  

What I enjoyed the most was building a functional network from scratch into a complete system with clear structure and rules: from working with **VLANs**, where the network began to communicate properly after configuration, up to **complete network security** and the implementation of security policies.  
I believe this work can serve as an inspiration for other networking enthusiasts or anyone interested in this field.  

For me, networking is not just a set of commands, but also a space for creativity and logical thinking.  
The greatest reward is the feeling when, after many hours of configuring and fine-tuning, I see the network running cleanly, securely, and without errors.  

© 2025 - Lukas Dula | Home Networking Lab & Portfolio
