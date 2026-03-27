<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket within a Microsoft Azure virtual machine. The goal is to simulate a real-world IT support enviroment by preparing the system for ticket management adn troubleshooting workflows. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10 or higher</b> (21H2)

<h2>List of Prerequisites</h2>

- Computer with atleast 8GB RAM
- Stable Internet Connection
- Ability to run a virtual machine
- Basic Computer navigation skills
- Access to remote desktop

<h2>Skills Demonstrated</h2>

- Virtual machine deployment (Azure)
- Remote system access(RDP)
- Web server setup (IIS)
- Database integration (MySQL)
- Help desk system installation

<h2>Installation Steps</h2>

<p>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ab304cd8-3b06-4b70-91be-6b894b8b1bac" />

For this part we will use Microsoft Azure to create a virtual machine to use for the osticket installation.
</p>
<p>
<h2>1.Create a Virtual Machine (Azure) </h2>

- Log into Microsoft Azure Portal
- Navigate to Virtual Machines → Create
- Configure:
  - Select you're Subscription
  - Resource Group
  - VM Name
  - Region:Choose Your Region (make sure its the same for everything)
  - Image:windows10 or higher
  - Size:Any size will work (Preferably one with 2vcpus and 8gigs of RAM)
  - Set username and password
- Confirm the licensing 
- Create the VM and Wait for deployment
</p>
<br />

<p>
<img width="1382" height="895" alt="image" src="https://github.com/user-attachments/assets/1669ab64-f8a3-4398-89be-8ad4bea0ed70" />
This image shows the use of remote desktop connection to connection to the Azure Virtual Machine.
</p>
<p>
<h2>2. Connect Using Windows Remote Desktop</h2>
  
- Look for the public Ip address for the virtual machine you created
- Open Remote Desktop Connection on your computer
- Enter the VM's Public IP address
- Log in using the credentials created earlier
- You are now connected to the virtual machine
</p>
<br />

<p>
"/>
</p>
<p>
<h2>3. Install osticket, IIS, and Dependecies</h2>

- install this folder in the virtual machine using this link (https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD)  this is a folder containing all dependecies and osticket web application
<p>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9aec9283-8cc1-43b3-8d47-981a857c739b" />
</p>
This image shows the installing and enabling of IIS to host the osticker.

<h3>4. Installing and enabling Internet Information Services (IIS) to host the osTicket</h3>

- Install/Enable IIS in windows with CGI
  - go to windows settings Control Panel
  - go to programs → Programs and features
  - select "turn windows features on or off"
  - turn on Internet Information Services (IIS)
  - expand IIS → expand World Wide Web Services → expand Application development features → enable CGI
  - click ok and wait for installation to complete
- go to web browser and search for (127.0.0.1) to make sure its working

<h2>Installing dependencies</h2> 

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/834d2622-3dbe-4907-8791-52230531331a" />

<h3>5. Installing PHP manager and rewrite</h3>

- Go to the osticket installation folder and download PHP manager
- In the same folder install the rewrite module
- Create the directory C:\PHP
- From the osticket folder Unzip the Php zip into C:\PHP

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2b067f6b-64f3-40bc-852e-cf2fae547381" />

<h3>6. Installing VC_redist</h3>

- From the osticket folder, download the VC_redist exe

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/47449723-083d-4b69-be2c-aac4759c65da" />

<h3>7. Installing MySQL</h3>
- From the osticket folder, Install MySQL
  - Typical Setup

  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8b961faf-1fba-40f0-8b8d-afcce9a460ef" />

- Lauch configuration Wizard (after install)
  - Standard Configuration
  - click next
  - For the username and password :root

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/689a9e38-6be7-4397-bcec-793bec9e973a" />

<h3>8. IIS configurating PHP</h3>

- search for IIS in the windows search and run as admin
  - from within IIS open PSP manager
  - register new PHP version (browse to C:\PHP  and select the application)
  - Reload IIS by stoping and restarting the server (right click the local host top left)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4c36ea8a-46c6-4766-ba00-42ed957fa104" />

<h2>9. Installing osTicket</h2>

- From the Osticket installation folder, extract osticket
  - copy the upload folder into "C:\inetpub\wwwroot" then rename the upload folder to "osTicket"
- Restart IIS Again

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4153d856-45ac-42f3-89fe-80800f4cbd7f" />

- From IIS go to sites → Default → osTicket
  - Click "Browse *.80' on the right (notice some extensions are not enabled)
- Go back to IIS, sites → Default → osTicket

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fd025e7f-7b89-443a-89cd-841bdf8118f1" />

  - Open PHP Manager
  - Click "Enable or disable and extension"
    - Enable: php_imap.dll
    - Enable: php_intl.dll
    - Enable: php_opcache.dll
- Refresh the osTicket site in your browser, observe the changes

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/44b4e814-0604-4f19-997f-fcc6a1709323" />

- Rename: ost-sampleconfig.php → ost-config.php
  -From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php 
- right click that folder and select properties
  -Security → Advanced
  - Disable inheritance → Remove All
  - New Permissions → Everyone → All (for principal you search for Everyone) then give all permissions then click apply
- Continue setting up osTicket in the browser by clicking continue
  - Name Helpdesk
  - Default email (this email recieves email from customers)
  - admin user info (email must be different from default system email)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/657831e3-fd90-468d-966d-377897735489" />

- From the osTicket Installation folder Install HeidiSQL
  - Open Heidi SQL

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9d6f2ae3-48ae-4153-ab4f-7f40cfc9653b" />

  - Create a new session, username and password "root"
  - Connect to the session
  - right click top left → Create new → Create a database called “osTicket”

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2ee25788-6e58-4b43-a3e2-d9062ab5c09b" />

- Go back to the osTicket browser and continue setup
  - MySQL Database: osTicket
  - MySQL username and password "root"
  - Click install now

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7c96cb3a-a498-4bb1-b750-c2b7ff62f278" />

<h1>CONGRAGULATIONS</h1>

This project successfully demonstrates the initial setup required to deploy a help desk ticketing system. The enviroment is now ready for further configuration, including user roles, departments, and ticket lifecycle management.
<h2>I Hope you enjoyed my guide to intalling osTicket</h2>
- On the bottom of the page you will see the url's for your osTicket!
</p>
<br />
