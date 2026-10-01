# Windows-11-Help-Desk-Home-Lab
A hands-on Windows 11 Help Desk home lab built with VirtualBox to practice Windows administration, user management, networking, troubleshooting, and common IT support tasks.

## Project Overview

This project is a hands-on Windows 11 Help Desk home lab created to practice common entry-level IT support, Windows administration, and troubleshooting tasks in a safe virtual environment.

Using Oracle VirtualBox, I created a Windows 11 Pro virtual machine named **HELPDESK-PC** to simulate a basic Help Desk environment. The lab allowed me to work with user accounts, networking, Windows administrative tools, system troubleshooting, security settings, and PowerShell without making potentially disruptive changes to my main computer.

The goal of this project was not only to complete the technical tasks, but also to understand why they are used in real IT support environments and develop a repeatable troubleshooting process.

## Skills Practiced

- Windows 11 installation and virtual machine configuration
- Local administrator and standard user account management
- Principle of least privilege and User Account Control (UAC)
- Windows networking and TCP/IP configuration
- Network troubleshooting using `ipconfig`, `ping`, and `nslookup`
- DNS testing and manual DNS configuration
- Windows Event Viewer log investigation
- Windows Services management and Print Spooler troubleshooting
- Device Manager hardware and driver inspection
- Disk Management and storage inspection
- Windows Update and Windows Security review
- System resource monitoring and system information
- Basic PowerShell administration and troubleshooting
- VirtualBox snapshots and virtual machine recovery

## Technologies & Tools

- Windows 11 Pro
- Oracle VirtualBox
- Windows PowerShell
- Command Prompt
- Computer Management
- Local Users and Groups
- Event Viewer
- Device Manager
- Disk Management
- Windows Services
- Windows Security
- Windows Update

## Lab Environment

- **Host Operating System:** Windows 11 Home
- **Virtualization Platform:** Oracle VirtualBox
- **Virtual Machine:** Windows 11 Pro
- **VM Name:** HELPDESK-PC
- **Memory:** Approximately 6 GB RAM
- **Virtual Disk:** 80 GB
- **Network Configuration:** VirtualBox NAT
- **Primary Administrator Account:** ITAdmin
- **Standard User Account:** Sarah Chen (`schen`)

## Project Documentation

This project includes detailed documentation of the lab build, configuration, testing, and troubleshooting process.

The documentation covers the Windows 11 virtual machine setup, user account configuration, networking tests, Windows administrative tools, security checks, PowerShell exercises, troubleshooting scenarios, and project verification.

A complete step-by-step build guide with screenshots will be included in this repository.

## Key Project Activities

1. Built and configured a Windows 11 Pro virtual machine using Oracle VirtualBox.
2. Installed VirtualBox Guest Additions and configured VM integration features.
3. Created separate administrator and standard-user accounts to practice user management and least privilege.
4. Examined the VM's network configuration and practiced TCP/IP and DNS troubleshooting using `ipconfig`, `ping`, and `nslookup`.
5. Investigated Windows logs using Event Viewer.
6. Practiced Windows service management and Print Spooler troubleshooting.
7. Inspected hardware and drivers using Device Manager.
8. Reviewed disks, partitions, and storage using Disk Management.
9. Reviewed Windows Update, Windows Security, system information, and resource usage.
10. Used PowerShell for basic Windows administration and troubleshooting.
11. Created and tested VirtualBox snapshots to practice VM recovery.

## Troubleshooting Approach

Throughout the lab, I practiced approaching technical problems systematically rather than immediately changing settings.

My general troubleshooting process was:

1. Identify the issue and gather information about the current system state.
2. Check the simplest and most likely causes first.
3. Use Windows administrative tools and command-line utilities to gather evidence.
4. Work from the local system outward when troubleshooting network connectivity.
5. Make one controlled change at a time when possible.
6. Test whether the change resolved the issue.
7. Verify that the system returned to the expected working state.
8. Document the issue, actions taken, and result.

This approach helped me focus on understanding the cause of a problem rather than only finding a temporary fix.

## What I Learned

This project strengthened my understanding of how common Windows Help Desk tasks connect together in a real troubleshooting process.

Some of my main takeaways were:

- Standard user accounts and administrator accounts should be separated so users only receive the permissions they need.
- Network troubleshooting is easier when approached systematically, starting with the local configuration and working outward toward the gateway, external connectivity, and DNS.
- Tools such as Event Viewer, Services, Device Manager, and Disk Management provide different types of evidence when diagnosing Windows issues.
- Commands such as `ipconfig`, `ping`, and `nslookup` can help isolate where a network problem is occurring.
- Windows Update and Windows Security are important parts of maintaining a healthy and secure endpoint.
- PowerShell provides another way to inspect and administer Windows systems beyond the graphical interface.
- Virtual machine snapshots provide a useful recovery point when testing configuration changes in a lab environment.

Most importantly, I learned that effective troubleshooting is not about memorizing individual fixes. It is about gathering information, narrowing down possible causes, making controlled changes, and verifying the result.

## Project Walkthrough

### 1. VirtualBox Lab Environment

I created a Windows 11 Pro virtual machine named **HELPDESK-PC** in Oracle VirtualBox to provide an isolated environment for practicing Help Desk administration and troubleshooting. The VM was configured with approximately 6 GB of RAM, an 80 GB virtual disk, and a NAT network adapter.

![VirtualBox HELPDESK-PC Lab Environment](01-VirtualBox-Lab-Environment.png)

### 2. Local User Account Management

I created separate administrator and standard-user accounts to practice user management and the principle of least privilege. The **ITAdmin** account was used for administrative tasks, while **Sarah Chen (schen)** was configured as a standard user for everyday use.

Separating these account types helped demonstrate why users should only receive the permissions necessary for their role, reducing the risk of unauthorized or accidental system changes.

![Local User Accounts](02-Local-User-Accounts.png)

### 3. Network Configuration & TCP/IP

I used `ipconfig` to examine the TCP/IP configuration of the **HELPDESK-PC** virtual machine. The command displayed the VM's IPv4 address, subnet mask, and default gateway, which are important starting points when troubleshooting network connectivity.

The VM received the IPv4 address **10.0.2.15** with a subnet mask of **255.255.255.0** and used **10.0.2.2** as its default gateway. Because the VM was configured with VirtualBox NAT, VirtualBox provided the virtual network that allowed the VM to communicate outside its local environment.

Reviewing these values helped me understand how to begin troubleshooting from the local system outward by first checking the computer's network configuration before testing the gateway, external connectivity, and DNS.

![IPConfig Network Configuration](03-IPConfig-Network-Configuration.png)

### 4. Connectivity Testing

After reviewing the VM's TCP/IP configuration, I tested network connectivity in stages using `ping`.

I first pinged the default gateway at **10.0.2.2** to verify that the HELPDESK-PC virtual machine could communicate with the VirtualBox NAT gateway. The test returned four successful replies with **0% packet loss**, confirming that the VM could reach its gateway.

I then pinged **8.8.8.8** to test connectivity beyond the local virtual network. This test also returned four successful replies with **0% packet loss**, confirming that the VM had external network connectivity.

Testing connectivity in this order helped demonstrate a systematic troubleshooting approach: verify the local network configuration first, test the gateway next, and then test connectivity to an external IP address.

![Ping Connectivity Testing](04-Ping-Connectivity-Testing.png)

### 5. DNS Name Resolution

After confirming that the VM could reach an external IP address, I tested DNS name resolution using `nslookup google.com`.

The lookup successfully returned multiple IP addresses for **google.com**, confirming that the VM could communicate with a DNS server and translate a domain name into IP addresses.

This test helped demonstrate an important distinction in network troubleshooting. A computer may have working network connectivity but still be unable to access websites by name if DNS is not functioning correctly. By testing external IP connectivity first and DNS resolution afterward, I could isolate whether a connectivity problem was related to the network itself or to name resolution.

![DNS Name Resolution](05-DNS-Name-Resolution.png)

### 6. Manual DNS Configuration

To practice making a controlled network configuration change, I manually configured the HELPDESK-PC virtual machine to use Google's public DNS servers.

I set the preferred DNS server to **8.8.8.8** and the alternate DNS server to **8.8.4.4** while leaving the VM's IP address configuration assigned automatically through DHCP.

I then used `ipconfig /all` to verify the configuration. The output confirmed that the VM was using **8.8.8.8** and **8.8.4.4** as its DNS servers while retaining its existing IPv4 address and default gateway.

This exercise helped me understand that DNS settings can be changed independently of the computer's IP address configuration and reinforced the importance of verifying a configuration change after applying it.

![Manual DNS Configuration](06-Manual-DNS-Configuration.png)
