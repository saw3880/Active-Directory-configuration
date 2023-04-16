<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resource group with  Azure VM
- Connectivity between the client and Domain Controller VM
- Install Active Directory
- Create an Admin and Normal User Account in AD

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/hwxsLYr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
I have set up both vm called DC-1 and client-1 in my azure resource group.Making  sure they are both in the same region and network.
</p>
<br />

<p>
<img src="https://i.imgur.com/1ZDJQ5T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now that both vm are created i must then make Connectivity between the client-1 and DC-1. So i must log into dc-1 and turn off windows firewall
by typing in the start menu firewall then enable ICMPv4  on dc-1 windows Firewall.once done you can go to client-1 and ping -t < dc-1 ip address>
to see that its getting traffic from dc-1.
<br />





<p>
<img src="https://i.imgur.com/EyB7pnf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we will be installing A.D domain services on dc-1 and make it a domain controller.In the start menu click on service manager, add roles
and features.




<img src=" " height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />




