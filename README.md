<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6
  
<h2>Installation Steps</h2>

<p>
<h3>Part 1 (Create Virtual Machine in Azure)</h3>
<p>
  
- Create a Resource Group
- Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs
- When creating the VM, allow it to create a new Virtual Network (Vnet)
  
</p>
  
<p>
  
- Create another Windows 10 VM with 2-4 vCPUs
- Name: vm-osticket
- Username: labuser (for example/whatever you choose)
- Password: osTicketPassword1! (for example/whatever you choose)
  
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Using Remote Desktop, access vm-osticket. This is the VM we will be installing the files linked below. 

- Open this:  <a href="https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Installation Files</a>

- We will use these files to install osTicket and some of the dependencies.

</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>

- Install / Enable IIS in Windows WITH
- IIS Management Console
- Internet Information Services -> Web Management Tools -> IIS Management Console
- [X] IIS Management Console

- and CGI and Common HTTP Features
- World Wide Web Services -> Application Development Features ->
- [X] CGI
- [X] Common HTTP Features

</p>
<p>
  
![image](https://github.com/n8som/osticket-prereqs/assets/110139109/ef7adb9c-2185-4ad8-ab31-0bd456e0f644)

</p>
<br />

<p>
  
- From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

- From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)

- Create the directory C:\PHP

- From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP

- From the Installation Files, download and install VC_redist.x86.exe.

</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>

- From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
  1. Typical Setup 
  2. Launch Configuration Wizard (after install) 
  3. Standard Configuration 
  4. Use Password1 for password

</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>

- Open IIS as an Admin

- Register PHP from within IIS

- Reload IIS (Open IIS, Stop and Start the server)

</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
  
- Install osTicket v1.15.8
- Download osTicket from the Installation Files Folder
- Extract and copy “upload” folder to c:\inetpub\wwwroot
- Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
- Reload IIS again (Open IIS, Stop and Start the server)
  
</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
  
- Go to sites -> Default -> osTicket
  1. On the right, click “Browse *:80”

(Note that some extensions are not enabled)

- Go back to IIS, sites -> Default -> osTicket
  1. Double-click PHP Manager
  2. Click “Enable or disable an extension”
   - Enable: php_imap.dll
   - Enable: php_intl.dll
   - Enable: php_opcache.dll
   - Refresh the osTicket site in your browse, observe the changes

</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
  
- Rename: ost-config.php
   - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
   - To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
- Assign Permissions: ost-config.php
   - Disable inheritance -> Remove All
   - New Permissions -> Everyone -> All

</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p> 

Continue Setting up osTicket in the browser (click Continue)
- Name Helpdesk
- Default email (receives email from customers)
  
</p>

<p>

From the Installation Files, download and install HeidiSQL.
- Open Heidi SQL
   - Create a new session, root/Password1
   - Connect to the session
   - Create a database called “osTicket”

- Continue Setting up osticket in the browser
   - MySQL Database: osTicket
   - MySQL Username: root
   - MySQL Password: Password1
   - Click “Install Now!”

</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Congratulations, hopefully it is installed with no errors!

  - Browse to your help desk login page: http://localhost/osTicket/scp/login.php
  - End Users osTicket URL: http://localhost/osTicket/


</p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
