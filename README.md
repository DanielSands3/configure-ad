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

- Install Active Directory
- Create a Domain Admin User within the Domain
- Setup Remote Desktop for non-administrative users on Client-1
- Create many additional users and attempt to login into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="356" alt="image" src="https://github.com/user-attachments/assets/0ed579b2-375a-4d97-8da8-d55db8f9d587" />
</p>
<p>
First we log into our Azure Virtual Machine aptly name DC-1 (Domain Controller) and install Active Directory services. Once installed we promote the server to Domain Controller. After, we create a new forest called mydomain.com, restart the computer, and log in with the prefix mydomain.com\username.  
</p>
<br />

<p>
<img width="455" alt="image" src="https://github.com/user-attachments/assets/04062709-8a11-467c-9e86-4d57081db467" />
</p>
<p>
Now we create a Domain Admin User within the domain. First, open Active Directory Users and Computers and create 2 new Organizational Units, one for "_EMPLOYEES," and one for "_ADMINS." Create a new employee called Jane Doe with username jane_admin and add Jane to the Domain Admins Security Group. From now on we use jane_admin as our administrator account.
</p>
<br />

<p>
<img width="170" alt="image" src="https://github.com/user-attachments/assets/2c2049e8-f7c0-4882-aa9c-8be45dea0734" />
</p>
<p>
Next, we setup Remote Desktop for non-administrative users on Client-1. We start by logging into Client-1 as mydomain.com\jane-admin. Open system properties, click "Remote Desktop," allow "domain users" access to remote desktop. You can now log into Client-1 as a normal, non-administrative user. 
</p>
<br />

<p>
<img width="271" alt="image" src="https://github.com/user-attachments/assets/60b2011e-4cce-4a25-b711-18086afbbd01" />
</p>
<p>
Lastly, we create additional users utilizing a Powershell_ISE script. In order to do so we first login into DC-1 as jane-admin, open Powershell_ISE as an administrator, create a new file and paste the script into the window. Now we can observe the accounts being created in ADUC(Active Directory Users and Computers) within the appropriate OU(Organizational Unit) "_EMPLOYEES." 
We can now log into Client-1 with any of the generated usernames. 
</p>
<br />
