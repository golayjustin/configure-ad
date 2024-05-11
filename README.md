
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
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

- Set up resources in Azure
- Ensure connectivity between the client and Domain Controller
- Install Active Directory
- Create an admin and normal user account in active directory
- Join client to the domain
- Set up remote desktop for non-administrative users on client
- Create additional users and log into the client

<h2>Deployment and Configuration Steps</h2>

<h3>Set up resources in Azure</h3>

<p>
Create a Domain Controller virtual machine with the name "DC-1".
</p>
<p>
<img height="80%" width="80%" alt="DC-1" src="https://i.imgur.com/KvYGwsA.png">
</p>
<br />

<p>
Set DC-1 NIC Private IP address to be static.
</p>
<p>
<img height="80%" width="80%" alt="Static IP address" src="https://i.imgur.com/FqijpF0.png">
</p>
<br />

<p>
Create the client Windows 10 virtual machine. Name it "Client-1". Ensure that it is located in the same resource group and uses the same Vnet as DC-1.
</p>
<p>
<img height="80%" width="80%" alt="Client-1" src="https://i.imgur.com/jnG7Wdf.png">
</p>
<br />

<h1></h1>

<h3>Ensure connectivity between the client and Domain Controller</h3>

<p>
Login to Client-1 with Remote Desktop and ping DC-1's private IP address with ping -t &lt;ip address&gt
</p>
<p>
<img height="80%" width="80%" alt="Pinging DC-1" src="https://i.imgur.com/qCGqnYO.png">
</p>
<br />

<p>
Login to the Domain Controller and enable ICMPv4 on the local windows Firewall.
</p>
<p>
<img height="80%" width="80%" alt="Enable ICMPv4" src="https://i.imgur.com/f889WOj.png">
</p>
<br />

<p>
Check back at Client-1 to see that ping succeeded.
</p>
<p>
<img height="80%" width="80%" alt="Successful ping" src="https://i.imgur.com/vlFFBHK.png">
</p>
<br />

<h1></h1>

<h3>Install Active Directory</h3>

<p>
Login to DC-1 and install Active Directory Domain Services.
</p>
<p>
<img height="80%" width="80%" alt="Active Directory Domain Services" src="https://i.imgur.com/ZZ7hFDy.png">
</p>
<br />

<p>
Promote as a DC and set up a new forest as mydomain.com
</p>
<p>
<img height="80%" width="80%" alt="Promote as a DC" src="https://i.imgur.com/u3ld8Nu.png">
</p>
<p>
<img height="80%" width="80%" alt="New forest mydomain.com" src="https://i.imgur.com/oS917oV.png">
</p>
<br />

<p>
Restart and log back into DC-1 as a user: mydomain.com\labuser
</p>
<p>
<img height="80%" width="80%" alt="Log into DC-1 as a user" src="https://i.imgur.com/2vCVDmv.png">
</p>
<br />

<h1></h1>

<h3>Create an admin and normal user account in active directory</h3>

<p>
In Active Directory Users and Computers (ADUC), create Organizational Units (OU) called "_EMPLOYEES" and "_ADMINS".
</p>
<p>
<img height="80%" width="80%" alt="_EMPLOYEES and _ADMINS" src="https://i.imgur.com/o4DvRcs.png">
</p>
<br />

<p>
Create a new employee named "Jane Doe" with the username of "jane_admin".
</p>
<p>
<img height="80%" width="80%" alt="Jane Doe" src="https://i.imgur.com/mTqGFu2.png">
</p>
<br />

<p>
Add jane_admin to the "Domain Admins" Security Group.
</p>
<p>
<img height="80%" width="80%" alt="Jane Doe in the Security Group" src="https://i.imgur.com/m0LBzu1.png">
</p>
<br />

<p>
Log out and close the Remote Desktop connection to DC-1. Log back in as mydomain.com\jane_admin". Use jane_admin as the admin account going forward.
</p>
<p>
<img height="80%" width="80%" alt="Logged in as jane_admin" src="https://i.imgur.com/VUDUx6z.png">
</p>
<br />

<h1></h1>

<h3>Join client to the domain</h3>

<p>
From the Azure Portal, set Client-1's DNS settings to the DC's Private IP address. Restart Client-1 from the Azure Portal.
</p>
<p>
<img height="80%" width="80%" alt="Client-1's DNS settings" src="https://i.imgur.com/ACDg4Gt.png">
</p>
<p>
<img height="80%" width="80%" alt="Restart Client-1" src="https://i.imgur.com/N0ycEMG.png">
</p>
<br />

<p>
Login to Client-1 (Remote Desktop) as the original local admin (labuser) and join it to the domain (computer will restart).
</p>
<p>
<img height="80%" width="80%" alt="Join Client-1 to the domain" src="https://i.imgur.com/vQarvRx.png">
</p>
<br />

<p>
Login to the Domain Controller with Remote Desktop and verify Client-1 shows up in Active Directory Users and Computers (ADUC) inside the "Computers" container on the root of the domain.
</p>
<p>
<img height="80%" width="80%" alt="Client-1 is present" src="https://i.imgur.com/8Q3TTkY.png">
</p>
<br />

<h1></h1>

<h3>Set up remote desktop for non-administrative users on client</h3>

<p>
Log into Client-1 as mydomain.com\jane_admin and open system properties. Click "Remote Desktop". Allow "domain users" access to remote desktop. Now Client-1 can be logged into as a normal user.
</p>
<br />

<h1></h1>

<h3>Create additional users and log into the client</h3>

<p>
Login to DC-1 as jane_admin. Open PowerShell_ise as an administrator.
</p>
<p>
<img height="80%" width="80%" alt="PowerShell_ise as an administrator" src="https://i.imgur.com/eArlYC5.png">
</p>
<br />

<p>
Create a new file and paste the user-creation script into it. Run the script to create the accounts.
</p>
<p>
<img height="80%" width="80%" alt="Paste the script" src="https://i.imgur.com/L9f6R9H.png">
</p>
<br />

<p>
Open ADUC and observe the accounts in the appropriate OU.
</p>
<p>
<img height="80%" width="80%" alt="Accounts in ADUC" src="https://i.imgur.com/RChQuhJ.png">
</p>
<br />

<p>
Attempt to log into Client-1 with one of the accounts.
</p>
<p>
<img height="80%" width="80%" alt="Log in with a script-created account" src="https://i.imgur.com/3OT4Pdc.png">
</p>
<p>
<img height="80%" width="80%" alt="Log in with a script-created account" src="https://i.imgur.com/a3VlYFk.png">
</p>
<br />
