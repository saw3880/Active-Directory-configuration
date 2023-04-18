<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Azure cloud</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


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
</p>
</p>



<img src="https://i.imgur.com/ToZZRxc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Once it as downloaded we wil then make dc-1 as the domain controller in the service manager hub where it says Promote the server as a DC
once finish i must name it as a root domain name called  mydomain.com / or anything you want with a password.Then it will automatically restart.
</p>
</p>





<img src="https://i.imgur.com/Lnq6qbD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After logging back in to dc-1 as mydomain.com/ ur name which was made to make when creating your dc-1 vm and password.In the service manager hub
go to tools then Active Directory Users and Computers then create an Organizational Unit which is  a folder we will then name 
_EMPLOYEES and another OU called _ADMINS we will add jane doe as a user in the _ADMINS folder so when logging it will be mydomain/jane.doe.finally
we must make jane a domain admin after resatart and log in as mydomain.com/jane.doe.
</p>
</p>


<img src="https://i.imgur.com/I6ZPrfj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
</p>

<img src="https://i.imgur.com/2dOT846.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

Once logged back in as jane.doe we must now Join Client-1 to your domain (mydomain.com/jane.doe by changing its dns to dc-1 Private IP address.In client-1
vm go to system then rename this pc to mydomain.once you will get a error so  from the azure portal i will need dc-1 private ip. copy it then paste its private ip address
to client-1. 
</p>
</p>




<img src="https://i.imgur.com/HMNQZCl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
After  restarting client-1 log back in and go to system and rename this pc again, this time it will work now its conneced to domain controller.
Jane.doe can log in to any pcs under the same domain.Now logging in client-1 as jane.doe we will create users so they all can log into client-1 vm.
so from system then remote desktop then ad users and add “domain users” check names.
</p>
</p>


<img src="https://i.imgur.com/LmRPtcC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Now we will create the users that will be able to log in to dc-1 and open powershell ise run as an administrator.
Create a new File and paste the contents of the script into it Run the script and instead of making 10000 i will make 1000. what this will do its 
going to make a bunch of random user acoounts.once done going back to the employess folder u will find all the made up user accounts
they all wil use the same password1 made earlier so mydomain.com/bud.rai password1. :)

