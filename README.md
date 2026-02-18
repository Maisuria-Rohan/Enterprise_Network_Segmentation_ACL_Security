## Enterprise Network Segmentation with ACL-Based Access Control
**Overview**
This project demonstrates the design and security hardening of a segmented enterprise network. The implementation includes VLAN separation, router-on-a-stick inter-VLAN routing, centralized DHCP configuration, and policy-based traffic filtering using standard ACLs.

The objective was to simulate a structured corporate network with controlled inter-department communication and guest network isolation.


<img width="438" height="260" alt="Picture1" src="https://github.com/user-attachments/assets/f4055d5a-9bd3-4910-bc71-7dffde39d125" />


**Network Architecture**
**Components:**
 - Central Switch
 - Accounting Switch
 - HR Switch
 - Router with subinterfaces
 - Web Server
 - Internal Wi-Fi
 - Guest Wi-Fi

**VLAN Design**
VLAN 10 – Accounting Staff – 192.168.10.0/24
VLAN 20 – Accounting Manager – 192.168.20.0/24
VLAN 30 – HR – 192.168.30.0/24
VLAN 40 – Guest Wi-Fi – 192.168.40.0/24
Internal Network – 192.168.1.0/24

**Inter-VLAN Routing**
Configured router-on-a-stick using:
 - Gig0/0/0.10
 - Gig0/0/0.20
 - Gig0/0/0.30
 - Gig0/0/0.40

Each subinterface configured with 802.1Q encapsulation and gateway IP.

# DHCP Configuration
**Router configured with five DHCP pools:**
 - AStaff
 - AManager
 - HR
 - Guest
 - Internal

**Each VLAN dynamically receives:**
 - IP address
 - Default gateway
 - Subnet mask

# ACL-Based Security Policies
Policy 1 – Restrict Compromised Host
Blocked specific Accounting Staff device from communicating with Accounting Manager VLAN.

Policy 2 – HR Protection
Restricted internal Wi-Fi from accessing HR VLAN except for web server access.

Policy 3 – Guest Isolation
Blocked Guest Wi-Fi users from accessing all internal VLANs while still allowing website access.

**ACLs applied outbound on subinterfaces:**
 - VLAN 20 → ACL 1
 - VLAN 30 → ACL 2
 - VLAN 40 → ACL 3


# Testing and Validation
- show vlan brief & show interfaces trunk
<img width="800" height="500" alt="Screenshot 2026-02-17 at 10 19 01 PM" src="https://github.com/user-attachments/assets/f35241ec-6b64-46a2-b7af-915b310a75f2" />
<img width="800" height="500" alt="Screenshot 2026-02-17 at 10 17 57 PM" src="https://github.com/user-attachments/assets/ffe02e3d-649d-4efc-ad31-c2727c7a5e1f" />
<img width="800" height="500" alt="Screenshot 2026-02-17 at 10 16 53 PM" src="https://github.com/user-attachments/assets/186830f1-f003-4cff-9eef-0d33cf4fdbbf" />



- show ip interface brief
<img width="800" height="300" alt="Screenshot 2026-02-17 at 10 21 26 PM" src="https://github.com/user-attachments/assets/17f50aa3-8fd7-45d3-ae13-261e8a64eec3" />



- show ip dhcp pool
<img width="800" height="600" alt="Screenshot 2026-02-17 at 10 22 21 PM" src="https://github.com/user-attachments/assets/1dc96343-d725-440e-a610-81c022ff1cef" />



- show ip dhcp binding
<img width="800" height="200" alt="Screenshot 2026-02-17 at 10 23 04 PM" src="https://github.com/user-attachments/assets/58f69231-cb83-493e-afaa-e86c94351d44" />



- show access-lists 
<img width="800" height="500" alt="Screenshot 2026-02-17 at 10 37 56 PM" src="https://github.com/user-attachments/assets/02687823-7141-479b-b8b2-956280b56777" />



- show running-config
<img width="800" height="600" alt="Screenshot 2026-02-17 at 10 44 34 PM" src="https://github.com/user-attachments/assets/efb4d8a5-f26e-4cf1-9f91-1b0c4ebde8ac" />
<img width="800" height="600" alt="Screenshot 2026-02-17 at 10 44 24 PM" src="https://github.com/user-attachments/assets/c444ae35-2c46-4316-8778-c3e53b747e58" />
<img width="800" height="600" alt="Screenshot 2026-02-17 at 10 44 15 PM" src="https://github.com/user-attachments/assets/59407103-a229-446e-9f61-1c3e657c45ca" />



Tested inter-VLAN communication before and after ACL enforcement.


# Skills Demonstrated
- Network segmentation
- Layer 2 and Layer 3 design
- Router-on-a-stick configuration
- DHCP implementation
- Standard ACL configuration
- Access control policy enforcement
- Traffic filtering and troubleshooting

# What I Learned
- How to enforce business security policies using ACL logic
- Difference between segmentation and access restriction
- Proper placement of ACLs on router interfaces
- How DHCP interacts with VLAN subinterfaces
- How to test and validate network security controls


