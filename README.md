# How to setup a Home Lab Running Active Directory with Powershell
![Home Lab](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/ADtopology.jpg?raw=true)

## Introduction

I created a small active directory home lab using Oracle VirtualBox.  The goal was to get hands on experience with an environment running active directory.  I used a PowerShell script to automatically create roughly 1000 users from a names.txt file. In addition, I created one Virtual machine (VM) as an end-user PC using a Windows 10 Pro ISO with internet access.  

I used:

- Oracle VirtualBox (VMWare Network)
- Server 2019 ISO (domain controller)
- Windows 10 Pro ISO (Client1 VM)
- PowerShell script (creates 1000 users)
- names.txt file (list of users)


## Creation of the domain controller and end-user PC


![DC](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/VMManager.png?raw=true)
![PC](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/Screen%20Shot%202024-01-24%20at%202.03.43%20PM.png?raw=true)

First, I created the domain controller using Windows Server 2019 and added 2 NIC cards (1 external / 1 internal).  External NIC gets its IP automatically via my home routers DHCP. I then hard-coded the internal NIC with a private IP 172.16.0.1.  I used 1 scope of an IP address block 172.16.0.100-200.  While in the DC, I enabled Remote Access Service (RAS) and Network Address Translation (NAT) and DHCP.  This will allow the internal PC to get an IP, default gateway, and DNS settings automatically.  

The client1 PC was created using the Windows 10 pro ISO.


## PowerShell script creating 1000 users in AD


![PowerShell creating users](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/PScreating.png?raw=true)<br>
![PowerShell running / updating AD](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/powershellrunnin.png?raw=true)<br>
![Users in AD / user's OU](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/UsersAD.png?raw=true)<br>

In the above images, you can see the PowerShell script running and adding users into the "_USERS" organizational unit (OU) from a "names.txt" file saved on my desktop.  As it creates all of the users, you can see it being added in the OU.



## User and PC showing they are in the correct OU in the "mydomain.com" domain.



![user in domain](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/userDomain.png?raw=true)
![pc in the computer OU](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/PCinDomain.png?raw=true)

Here you can see I logged into the windows PC and ran "whoami" which confirms I am in the "mydomain" domain.  You can also see the windows PC in the correct "Computers" OU in AD.




## Summary

With this particular project, I was able to set-up a decent live home lab environment running active directory.  The environment has remote access, able to resolve Fully Qualified Domain Name (FQDN) using the DNS service enabled on the DC and have internet connectivity.  Internal "Client1" PC was able to get its configurations (default gateway, DNS, and IP address from the DHCP server running inside of the domain controller (DC) as well.  The PowerShell script gave me first-hand experience in how one can automate adding a batch of users automatically into AD, including having their logins/passwords created.
