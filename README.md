Goal: To build a robust, hands-on portfolio demonstrating core IT Support skills, making you job-ready for entry-level roles in Sydney.
Your Primary Lab Environment: A single host machine running VirtualBox, hosting multiple interconnected Virtual Machines (VMs).

Phase 1: Foundation & Core OS Skills (Build Your Workbench)
Objective: Master basic VM management, OS installation, and fundamental operating system administration for both Windows and Linux.
VMs Required:
DC01: Windows Server 2022 Evaluation (or 2019)
W10-Client01: Windows 10/11
Ubuntu-Client01: Ubuntu Desktop (latest LTS)
Network Setup (VirtualBox Settings for VMs):
DC01:
Adapter 1: NAT (for internet access, updates, downloads)
Adapter 2: Internal Network (IT_Lab_Network)
W10-Client01:
Adapter 1: Internal Network (IT_Lab_Network)
Ubuntu-Client01:
Adapter 1: Internal Network (IT_Lab_Network)

Lab Activities:
1. Virtualization Environment Setup & VM Deployment: * Install VirtualBox on your host machine. * Create DC01(Windows Server) VM: Allocate 4GB RAM, 2 CPUs, 80GB HDD. Install Windows Server 2022 Desktop Experience. * Create W10-Client01 (Windows 10/11) VM: Allocate 4GB RAM, 2 CPUs, 60GB HDD. Install Windows 10/11. * Create Ubuntu-Client01 (Ubuntu Desktop) VM: Allocate 2GB RAM, 1 CPU, 40GB HDD. Install Ubuntu Desktop. * Crucial: Ensure all client VMs are connected to the IT_Lab_Network (Internal Network adapter), and the server has both NAT and Internal Network adapters. * Portfolio Item: Document VM creation steps, network configuration, and screenshots of running VMs.
2. Basic OS Administration (Windows & Linux): * Windows (W10-Client01): * User/Group Management:Create local users and groups (lusrmgr.msc). Assign users to groups. Test permissions by logging in as different users. * Disk Management: Open Disk Management, create new partitions, format drives (NTFS, FAT32). * Task Scheduler: Create a scheduled task (e.g., run notepad.exe at a specific time). * Event Viewer: Explore critical, error, warning logs. Filter by event ID/source. Practice identifying system issues. * System Updates: Perform a full Windows Update cycle. * Command Line Basics: Practice ipconfig, dir, cd, mkdir, del in cmd and PowerShell. * Linux (Ubuntu-Client01): * User/Group Management: Use sudo useradd, sudo passwd, sudo userdel, sudo groupadd, sudo usermod -aG to manage users and groups. Test su command. * File System Navigation: Practice ls, cd, pwd, mkdir, rm, mv, cp. * Permissions: Use chmod and chown to change file/folder permissions and ownership. * Cron Jobs:Schedule a simple cron job (e.g., write "Hello World" to a file every minute). * Log Files: View system logs (/var/log/syslog, auth.log). * Package Management: Use sudo apt update, sudo apt upgrade, sudo apt install <package>, sudo apt remove <package>. * Portfolio Item: Screenshots of user/group management, disk partitions, task/cron jobs, event/log viewer. Document key commands and outcomes for both OS.

Phase 2: Core Infrastructure & Networking (Build Your Backbone)
Objective: Establish central identity management (Active Directory), foundational network services (DHCP, DNS), and practice essential networking troubleshooting.
VMs Involved: DC01, W10-Client01, Ubuntu-Client01

Lab Activities:
1. Active Directory Domain Services (AD DS) Deployment (DC01): * Static IP Configuration: Set DC01's IT_Lab_Network adapter to a static IP (e.g., 192.168.1.1, Subnet Mask 255.255.255.0, Preferred DNS 127.0.0.1). * Install AD DS Role: Add the Active Directory Domain Services role in Server Manager. * Promote to Domain Controller: Create a new forest (e.g., yourdomain.local). Set DSRM password. * Portfolio Item: Screenshots of static IP, AD DS role installation, domain promotion wizard, successful domain creation.
2. DHCP & DNS Configuration (DC01): * Install DHCP Role: Add the DHCP Server role in Server Manager. * Configure DHCP Scope: Create a new DHCP scope (e.g., 192.168.1.100 to 192.168.1.200). Include DNS server option pointing to 192.168.1.1. Activate the scope. * DNS Basics: Verify DNS Forward Lookup Zones for your domain (yourdomain.local) and ensure DC01 has its own A record. * Portfolio Item: Screenshots of DHCP scope creation, DNS configuration.
3. Client Domain Join & Network Configuration: * W10-Client01: * Set W10-Client01's IT_Lab_Network adapter to "Obtain an IP address automatically" (DHCP) and "Obtain DNS server address automatically". Verify it receives an IP from DC01 and DNS points to DC01. * Join to Domain: Join W10-Client01 to yourdomain.localusing the domain Administrator credentials. Restart. * Log in as a local user for now. * Ubuntu-Client01: * Configure Ubuntu-Client01's network adapter to obtain IP via DHCP and confirm it receives IP from DC01. * (Optional/Advanced) Research and attempt to join Ubuntu to the Active Directory domain using realmd or Samba. This is an excellent stretch goal. * Portfolio Item: ipconfig /all output from W10-Client01 showing DHCP details, screenshots of successful domain join.
4. Core Networking Troubleshooting: * Tools Practice: On both W10-Client01 and Ubuntu-Client01, extensively use: * ipconfig/ifconfig (check IP, subnet, gateway, DNS) * ping (test connectivity to DC01, gateway, external websites like google.com) * tracert/traceroute (trace network path) * nslookup (query DNS for internal and external names) * netstat (show active network connections) * Scenario: Simulate "no internet access" on W10-Client01. * Change IP to static with incorrect gateway/DNS. * Disable network adapter. * Introduce a firewall rule blocking all outbound traffic. * Troubleshoot & Document: Use the tools above to diagnose and fix each scenario. * Subnetting Practice: Use an online subnet calculator (like subnettingpractice.com) to calculate network addresses, broadcast addresses, and host ranges for given CIDR notations (e.g., /24, /27). Understand the concept. * Portfolio Item: Screenshots of command outputs demonstrating troubleshooting steps. Explain your systematic approach to diagnosing network issues.
