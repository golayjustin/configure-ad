
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
<img height="80%" width="80%" alt="DC-1" src="">
</p>
<br />

<p>
Set DC-1 NIC Private IP address to be static.
</p>
<p>
<img height="80%" width="80%" alt="Static IP address" src="">
</p>
<br />

<p>
Create the client Windows 10 virtual machine. Name it "Client-1". Ensure that it is located in the same resource group and uses the same Vnet as DC-1.
</p>
<p>
<img height="80%" width="80%" alt="Client-1" src="">
</p>
<br />

<p>
Use Network Watcher to confirm that both virtual machines are using the same Vnet.
</p>
<p>
<img height="80%" width="80%" alt="Network Watcher" src="">
</p>
<br />









<h3>Ensure connectivity between the client and Domain Controller</h3>
<h3>Install Active Directory</h3>
<h3>Create an admin and normal user account in active directory</h3>
<h3>Join client to the domain</h3>
<h3>Set up remote desktop for non-administrative users on client</h3>
<h3>Create additional users and log into the client</h3>


<p>
Log into osTicket to view the tickets.
</p>
<p>
<img height="80%" width="80%" alt="Tickets from agent login" src="">
</p>
<br />








<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
