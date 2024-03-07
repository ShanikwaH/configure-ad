# configure-ad
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

<h2>Operating Systems Used</h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setting Up Resources in Microsoft Azure
- Ensuring Connectivity between the Client and Domain Controller
- Installing Active Directory
- Creating an Admin and Normal User Account in Active Directory
- Joining Client-1 to your Domain(mydomain.com)
- Create a bunch of additional users and attempt to log into Client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/mEyxaVS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/GQ4Dyyd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/jr8ZDmO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://i.imgur.com/ppQFC3L.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To begin this lab, I first created a Domain Controller Virtual Machine using (Windows Server 2022) and named it "DC-1". Next, I set up the Domain Controllers NIC Private IP Address as "static." After that, I created a Client Virtual Machine using (Windows 10) and named it "Client-1". I used the same Resource Group and VNET that I used while creating "DC-1". Lastly, I checked the topology using Network Watcher inside Microsoft Azure.
</p>
<br />

<p>
<img src="https://i.imgur.com/89k4dbA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/Nw4cPBR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Next, I wanted to ensure connectivity between DC-1 and Client-1. I did that by using Remote Desktop and logging into Client-1 first. Then while in Client-1's Remote Desktop, I pinged DC-1's Private IP Address with the command "ping -t<ip address> (perpetual ping). After confirming that there was no connection between the 2, I logged into DC-1, also using Remote Desktop and enabled ICMPv4 on the local windows firewall. The final step was for me to go back into Client-1's Remote Desktop and attempt to ping DC-1 again, and once I did that this time, it showed that it had succeeded.
</p>
<br />

<p>
<img src="https://i.imgur.com/6QWlZ51.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/Uzz0Cf1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/i0YDu2u.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

In this part of the lab, I installed Active Directory.  I did that by logging back into DC-1 Remote Desktop and installed Active Directory Domain Services. Moving forward, I had to promote as a DC by setting up a new forest and naming it "mydomain.com." My last step was to log out of DC-1's Remote Desktop and log back into it as "mydomain.com\labuser".
</p>
<br />

<p>
<img src="https://i.imgur.com/Bw1Ap1I.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/KpwDuy5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/2FHPkCF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/D56jr6N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/qdHEE58.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

At this point in the lab, I had to create an Admin and Normal User account in AD. First, I went to Active Directory Users and Computers(ADUC), and while there I made an Organizational Unit(OU) called "_EMPLOYEES." After that, I made another OU and named this one "_ADMINS." Next, I created a new employee named "Jane Doe" with the username "jane_admin" and added that employee to the "Domain Admins" security group. Moving on, the last step I did was log back out of DC-1's Remote Desktop and log back into it as "mydomain.com\jane_admin".
</p>
<br />

<p>
<img src="https://i.imgur.com/F0toGxO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/8w7RuWj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/cCyTKg1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/IcfdEss.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

In part 5 of this lab, I joined Client-1 to my domain(mydomain.com). I had to first set Client-1's DNS settings to the DC Private IP Address inside of Microsoft Azure. Once I did that, I logged out of Client-1's Remote Desktop, logged back into as the original local admin (labuser), and joined it to the domain. Next, I went back into DC-1's Remote Desktop and verified that Client-1 now appeared in the Active Directory Users and Computers (ADUC) "Computers" container on the root of the domain.
</p>
<br />

<p>
<img src="https://i.imgur.com/611McfA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/5pwBbw0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/r8MOwpK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/VlUyx4S.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

In the final part of this lab, I created thousands of additional users and attempted to log into Client-1's Remote Desktop with one of the new users I had made. I did this by logging back into DC-1's Remote Desktop as jane_admin and opening "Powershell_ise" as an administrator. After doing that, I made a "New File" and pasted the contents of a "script" into Powershell_ise. Inside Powershell_ise, I ran the script and observed the thousands of accounts being created. Lastly, I opened ADUC and observed all of the new accounts in the appropriate OU. Next, I took one of the random new accounts' information, logged into Client-1's Remote Desktop, and successfully logged in with the random accounts credentials. 
</p>
<br />
