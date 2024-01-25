# How to setup a Home Lab Running Active Directory with Powershell
![Home Lab](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/ADtopology.jpg?raw=true)

## Introduction

I created a small active directory home lab using Oracle VirtualBox.  I used a PowerShell script to auto create roughly 1000 users and created one VM as an end-user PC using a Windows 10 Pro ISO and added it to the domain.  The goal was to get hands on experience with an environment running active directory and the process of creating users from a text file and automating the process.  In addition, I wanted the Windows 10 PC to be able to reach the internet both ways and be able to resolve DNS queries internally and externally.  I used:

- Oracle VirtualBox (VMWare Network)
- Server 2019 ISO (domain controller)
- Windows 10 Pro ISO (Client1 VM)
- PowerShell script (creates 1000 users)


## Creation of the domain controller and end-user PC
![DC](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/VMManager.png?raw=true)
![PC](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/Screen%20Shot%202024-01-24%20at%202.03.43%20PM.png?raw=true)

First, I created the domain controller using Windows Server 2019 and added 2 NIC cards (1 external / 1 internal).  External NIC gets its IP automatically via my home routers DHCP. I then hard-coded the internal NIC with a private IP 172.16.0.1.  I used 1 scope of an IP address block 172.16.0.100-200.  While in the DC, I enabled Remote Access Service (RAS) and Network Address Translation (NAT) and DHCP.  This will allow the internal PC to get an IP assigned automatically and get its default gateway and DNS settings automatically.  

The client1 PC was created using the Windows 10 pro ISO.


## PowerShell script creating 1000 users in AD
![PowerShell creating users](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/PScreating.png?raw=true)<br>
![PowerShell running / updating AD](https://github.com/alfonsonyc2005/Active_DirectoryLab/blob/main/powershellrunnin.png?raw=true)<br>
![Windows RDP/SMB Auth Failures](https://imgur.com/kPuWG6i.png)<br>

## Metrics Before Hardening / Security Controls

The following table shows the metrics we measured in our insecure environment for 24 hours:
Start Time 2024-01-14 3:15:56 PM
Stop Time 2023-03-15 3:15:56 PM

![Screen Shot 2024-01-21 at 11 19 31 PM](https://github.com/alfonsonyc2005/Azure-SOC/assets/141835414/ac205dda-ee70-4cc3-90cd-46d1b35859a4)

## Attack Maps Before Hardening / Security Controls

```All map queries actually returned no results due to no instances of malicious activity for the 24 hour period after hardening.```

## Metrics After Hardening / Security Controls

The following table shows the metrics we measured in our environment for another 24 hours, but after we have applied security controls:
Start Time 2024-01-18 10:17:06 PM
Stop Time	2024-01-19 10:17:06 PM

![Screen Shot 2024-01-21 at 11 20 24 PM](https://github.com/alfonsonyc2005/Azure-SOC/assets/141835414/3a4f9caa-2bb9-4119-8cee-f902a406a63a)

## Conclusion

In this project, a miniature honeynet was established within Microsoft Azure, and various log sources were seamlessly integrated into a Log Analytics workspace. The deployment of Microsoft Sentinel played a crucial role in initiating alerts and generating incidents based on the assimilated logs. Furthermore, metrics were assessed in the insecure environment both before the implementation of security controls and after their application. It is noteworthy that the implementation of security measures resulted in a significant reduction in the number of security events and incidents, highlighting the efficacy of these controls.

Importantly, if the network resources had been extensively utilized by regular users, it is plausible that a higher volume of security events and alerts might have been produced in the 24-hour period following the implementation of the security controls.
