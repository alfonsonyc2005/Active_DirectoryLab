# Active Directory Home Lab with PowerShell Automation

## Overview
This project demonstrates the setup of a **local Active Directory (AD) lab environment** and the use of **PowerShell automation** to manage identity objects at scale.

The lab simulates a small enterprise domain by deploying a domain controller, a domain-joined client machine, and automating the creation of approximately **1,000 user accounts** using PowerShell.

---

## Architecture
![Active Directory Lab Topology](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/ADtopology.jpg?raw=true)

---

## Technologies Used
- Windows Server 2019 (Active Directory Domain Services)
- Windows 10 Pro (Domain-joined client)
- Oracle VirtualBox
- PowerShell
- Active Directory Users and Computers (ADUC)

---

## Active Directory Environment
### Domain Controller and Client Setup

- Deployed a Windows Server 2019 domain controller
- Configured Active Directory Domain Services (AD DS)
- Enabled DNS and DHCP services for domain clients
- Joined a Windows 10 client machine to the domain

**Outcome:** Established a functional enterprise-style Active Directory environment capable of managing users and devices.

<details>
<summary><strong>Implementation details</strong></summary>

- Configured separate internal and external network interfaces
- Enabled NAT and DHCP to support internal client connectivity
- Verified domain join and DNS name resolution
- Confirmed client authentication against the domain controller

</details>

---

## Identity Automation with PowerShell
### Bulk User Creation

- Developed a PowerShell script to automate user creation
- Imported usernames from a `names.txt` file
- Created approximately 1,000 users in a dedicated Organizational Unit (OU)
- Automatically assigned account attributes and credentials

**Outcome:** Demonstrated scalable identity lifecycle management using scripting and automation.

![PowerShell User Creation](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/PScreating.png?raw=true)

<details>
<summary><strong>Implementation details</strong></summary>

- Parsed user data from a text file
- Used Active Directory PowerShell modules
- Programmatically created users in a custom `_USERS` OU
- Verified user creation via ADUC

</details>

---

## Domain Validation
### User and Device Verification

- Logged into the domain-joined client using a domain user account
- Verified domain membership using `whoami`
- Confirmed correct OU placement for both users and computers

**Outcome:** Validated proper authentication, authorization, and directory structure.

![User in Domain](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/userDomain.png?raw=true)
![PC in Computers OU](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/PCinDomain.png?raw=true)

---

## What This Project Demonstrates
- Active Directory fundamentals
- Organizational Unit (OU) design
- User and device lifecycle management
- PowerShell automation for identity operations
- Foundational skills used in IAM, SOC, and enterprise IT roles

---

## Summary
This project provided hands-on experience with **Active Directory administration and automation**, reinforcing core identity concepts such as user provisioning, domain authentication, and directory organization.

By automating bulk user creation with PowerShell, the lab mirrors real-world scenarios where efficiency, consistency, and scalability are critical to identity management operations.

