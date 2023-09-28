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
<h3>Part 1 (Create Virtual Machines in Azure)</h3>
<p>
  
- Create a Resource Group
- Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs
- When creating the VM, allow it to create a new Virtual Network (Vnet)
- I named this one vm1
  
</p>
  
<p>
  
- Create another Windows 10 VM with 2-4 vCPUs
- Name: vm-osticket
- Username: labuser (for example/whatever you choose)
- Password: osTicketPassword1! (for example/whatever you choose)
  
</p>
<p>
  
![image](https://github.com/n8som/osticket-prereqs/assets/110139109/8c10ba06-2102-41d9-a48c-fa124fa4b316)

</p>
<br />

<p>
Using Remote Desktop, access vm-osticket. This is the VM that we will be installing the files on, linked below. 

- Open this:  <a href="https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Installation Files</a>

- We will use these files to install osTicket and some of the dependencies.

</p>
<p>
  
![image](https://github.com/n8som/osticket-prereqs/assets/110139109/99a97a2b-007d-4be5-a4c4-cc525600ec87)

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

  ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/701925e1-7a77-40bb-85c4-63cb0fe236ab)


- From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP

- From the Installation Files, download and install VC_redist.x86.exe.

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

![image](https://github.com/n8som/osticket-prereqs/assets/110139109/e8c33480-fc33-4c1c-aa28-2e4a6f5713ff)

</p>
<br />

<p>

- Open IIS as an Admin

  ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/e8efd946-3997-43df-8beb-3cc54e8caee1)

- Register PHP from within IIS by double clicking PHP Manager

  ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/0bf89c7d-4cda-4fb5-b32b-dddb72dbf4fb)

  ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/284cc8fa-b9d4-43e9-8d6c-84bf6527bc9c)

  ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/f53ca950-a659-4e2e-8f0a-1c723661ba7c)

- Reload IIS (Open IIS, Stop and Start the server)

  ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/30774620-f4ad-4f6f-ac48-7d07cbd6d40b)

</p>
<br />

<p>
  
- Install osTicket v1.15.8
- Download osTicket from the Installation Files Folder
- Extract and copy “upload” folder to c:\inetpub\wwwroot

  ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/82856964-c24c-453f-a8be-0eb6304bf9d1)

- Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

  ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/a01feef4-2172-48cb-b35e-a32a5715e0d8)

- Reload IIS again (Open IIS, Stop and Start the server)
</p>
<br />

<p>
  
- Go to sites -> Default -> osTicket
  1. On the right, click “Browse *:80”

     ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/d016a2a5-d6fc-4d2c-905d-e29ecdbc0541)

(Note that some extensions are not enabled)

![image](https://github.com/n8som/osticket-prereqs/assets/110139109/fa5dba09-8791-4ec2-bf94-f87d61975646)


- Go back to IIS, sites -> Default -> osTicket
  1. Double-click PHP Manager
  2. Click “Enable or disable an extension”

![image](https://github.com/n8som/osticket-prereqs/assets/110139109/1eafcac2-e8f2-4025-a82c-75db8fca6d9d)

   - Enable: php_imap.dll
   - Enable: php_intl.dll
   - Enable: php_opcache.dll

     ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/8ad28fd6-1efa-44c1-a945-e72359e4e804)

   - Refresh the osTicket site in your browse, observe the changes

     ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/0790c42d-a11c-4fb7-ae3f-afd47e1b21da)

</p>
<br />

<p>
  
- Rename: ost-config.php
   - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
   - To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

     ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/55e52d8f-3269-4b1b-8fbb-b9e9647f8c8e)

- Assign Permissions: ost-config.php

  ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/05eba6b2-8497-49e5-b593-2f9d9d1fecd6)

   - Disable inheritance -> Remove All

     ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/83c55f51-e40c-42e4-afff-2d5d56186b05)

   - New Permissions -> Everyone -> All

     ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/7aa2427d-fa8b-4a1e-8473-cefb0ab3ab69)

     ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/53bb040a-4045-45a4-921a-840e3e260588)

</p>
<br />

<p> 

Continue Setting up osTicket in the browser (click Continue)
- Name Helpdesk
- Default email (receives email from customers)

  ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/d76524a9-a99d-4c2c-8bba-dcd8bd42c634)

</p>

<p>

From the Installation Files, download and install HeidiSQL.
- Open Heidi SQL
   - Create a new session, root/Password1
   - Connect to the session

![image](https://github.com/n8som/osticket-prereqs/assets/110139109/28c3cf7a-9891-4474-bcc2-61b38290a8db)

   - Create a database called “osTicket”

     ![image](https://github.com/n8som/osticket-prereqs/assets/110139109/582f3edf-88fe-42df-a807-8e2a02568219)

- Continue Setting up osticket in the browser
   - MySQL Database: osTicket
   - MySQL Username: root
   - MySQL Password: Password1
   - Click “Install Now!”

</p>
<p>

![image](https://github.com/n8som/osticket-prereqs/assets/110139109/d2dad58a-c499-44ff-becc-a3fd6243868f)

</p>
<br />

<p>
Congratulations, hopefully it is installed with no errors!

  - Browse to your help desk login page: http://localhost/osTicket/scp/login.php
  - End Users osTicket URL: http://localhost/osTicket/


</p>
<p>

![image](https://github.com/n8som/osticket-prereqs/assets/110139109/38ae217c-2b1d-4505-82b9-725aaead9849)

</p>
<br />
