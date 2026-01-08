#  Home IT Support Lab – Virtualized Enterprise Environment

This repository documents a complete home lab environment built to simulate real-world IT Support, System Administration, and Service Desk workflows.  
The project includes virtualization, Windows Server administration, Active Directory deployment, DNS/DHCP configuration, Linux integration, Group Policy management, and automation with PowerShell.

---

##  Project Overview

This lab was designed to replicate a small enterprise network using VirtualBox and multiple operating systems.  
It includes:

- A Windows Server 2022 Domain Controller (DC01)
- A Windows 10/11 domain-joined client (W10-Client01)
- An Ubuntu Desktop client (Ubuntu-Client01)
- Core infrastructure services (AD DS, DNS, DHCP)
- User, group, and GPO management
- PowerShell automation for user provisioning

---

#  Phase 1 – Foundation & Core OS Skills

##  Goal
Build the virtualization environment and deploy all operating systems with proper networking.

##  Tasks Completed
- Installed **VirtualBox** and downloaded OS ISOs.
- Created VMs: DC01, W10-Client01, Ubuntu-Client01.
- Configured VirtualBox networking:
  - DC01: NAT + Internal Network (IT_Lab_Network)
  - Clients: Internal Network only
- Installed:
  - Windows Server 2022 (Desktop Experience)
  - Windows 10/11
  - Ubuntu Desktop
- Installed **VirtualBox Guest Additions** on all VMs.
- Renamed hosts and configured static IPs.
- Temporarily disabled firewalls for testing.
- Verified connectivity using:
  - `ping`
  - `nslookup`
  - Windows CMD & Linux Terminal

---

#  Phase 2 – Core Infrastructure & Networking

##  Goal
Deploy Active Directory, DNS, DHCP, and integrate client machines into the domain.

##  Tasks Completed
### **Active Directory**
- Assigned DC01 static IP: `192.168.1.1`
- Installed **AD DS** role
- Promoted DC01 to a domain controller
- Created forest: **testlab.local**

### **DNS & DHCP**
- Installed **DHCP Server** role
- Created DHCP scope:
  - Range: `192.168.1.100 – 192.168.1.200`
  - DNS: `192.168.1.1`
- Verified DNS Forward Lookup Zone and A records

### **Client Integration**
- W10-Client01:
  - Configured for DHCP
  - Successfully joined the domain
- Ubuntu-Client01:
  - Configured for DHCP
  - Successfully received IP & DNS settings
  - (Optional) Explored domain join via realmd/Samba

### **Troubleshooting Practice**
Used:
- `ipconfig` / `ifconfig`
- `ping`
- `tracert` / `traceroute`
- `nslookup`
- `netstat`

---

#  Phase 3 – Service Desk Simulations & Management

##  Goal
Simulate real-world IT support tasks involving user management, security policies, and automation.

##  Tasks Completed

### **Active Directory User & Group Management**
- Created OUs:
  - Sales  
  - Marketing  
  - IT  
  - Managers  
- Created 5+ user accounts and assigned them to OUs
- Created security groups:
  - Sales_Dept  
  - Marketing_Dept  
  - IT_Team  
  - Managers_Group  
- Verified user logins on W10-Client01

### **PowerShell Automation**
- Built a PowerShell script to automate user creation from a CSV file
- Script uses:
  - `Import-Csv`
  - `New-ADUser`
- Uploaded script to GitHub for version control

### **Group Policy Management**
- Modified **Default Domain Policy**:
  - Password length: 10 characters
  - Password history: 24
  - Complexity: Enabled
- Created **Sales_Desktop_Policy**:
  - Set desktop wallpaper via UNC path
  - Disabled Control Panel & PC Settings
- Verified GPO application on W10-Client01

---

#  Skills Gained

##  **Virtualization & OS Deployment**
- VirtualBox VM creation, networking, and resource allocation  
- Installing and configuring Windows Server, Windows Client, and Ubuntu Desktop  
- Guest Additions installation and optimization  

##  **Windows Server Administration**
- Active Directory Domain Services (AD DS) deployment  
- DNS and DHCP configuration  
- Domain controller promotion and forest creation  

##  **Identity & Access Management**
- Creating and managing OUs, users, and security groups  
- Domain join procedures for Windows clients  
- Understanding authentication and directory structure  

##  **Group Policy Administration**
- Editing Default Domain Policy  
- Creating and linking custom GPOs  
- Enforcing desktop restrictions and security settings  

##  **Networking & Troubleshooting**
- IP addressing, DHCP, DNS fundamentals  
- Using ping, tracert, nslookup, netstat  
- Diagnosing connectivity and name resolution issues  

##  **Linux Client Administration**
- Basic Ubuntu networking configuration  
- DHCP integration  
- Exploring AD integration options  

##  **Automation & Scripting**
- PowerShell scripting for user provisioning  
- CSV-driven automation workflows  
