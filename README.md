<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


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

<h2>Installation Steps</h2>

<p>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ab304cd8-3b06-4b70-91be-6b894b8b1bac" />

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

- install this folder in the virtual machine using this link (https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD)  this is a folder containing all dependecies and osticket
<p>
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9aec9283-8cc1-43b3-8d47-981a857c739b" />
</p>


<h3>Installing IIS</h3>

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

<h3>Installing PHP manager and rewrite</h3>

- Go to the osticket installation folder and download PHP manager
- In the same folder install the rewrite module
- Create the directory C:\PHP
- From the osticket folder Unzip the Php zip into C:\PHP

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2b067f6b-64f3-40bc-852e-cf2fae547381" />

<h3>Installing VC_redist</h3>

- From the osticket folder, download the VC_redist exe

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/47449723-083d-4b69-be2c-aac4759c65da" />

<h3>Installing MySQL</h3>
- From the osticket folder, Install MySQL
  - Typical Setup

  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8b961faf-1fba-40f0-8b8d-afcce9a460ef" />

- Lauch configuration Wizard (after install)
  - Standard Configuration
  - click next
  - For the username and password :root

-PICTURE
<h3>IIS configurating PHP</h3>

- search for IIS in the windows search and run as admin
  - from within IIS open PSP manager
  - register new PHP version (browse to C:\PHP  and select the application)
  - Reload IIS by stoping and restarting the server

-PICTURE
<h2>Downloading osTicket</h2>

- From the Osticket installation folder, extract osticket
  - copy the upload folder into "C:\inetpub\wwwroot" then rename the upload folder to "osTicket"
- Restart IIS Again
- From IIS go to sites → Default → osTicket
  - Click "Browse *.80' on the right (notice some extensions are not enabled)
- Go back to IIS, sites → Default → osTicket
  - Open PHP Manager
  - Click "Enable or disable and extension"
    - Enable: php_imap.dll
    - Enable: php_intl.dll
    - Enable: php_opcache.dll
    
-PICTURE
- Refresh the osTicket site in your browser, observe the changes
- Rename: ost-sampleconfig.php → ost-config.php
  -From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php 
- right click that folder and select properties
  - Disable inheritance → Remove All
  - New Permissions → Everyone → All
- Continue setting up osTicket in the browser by clicking continue
  - Name Helpdesk
  - Default email (this email recieves email from customers)

-Picture
- From the osTicket Installation folder Install HeidiSQL
  - Open Heidi SQL
  - Create a new session, root/root
  - Connect to the session
  - Create a database called “osTicket”

-Picture
- Go back to the osTicket browser and continue setup
  - MySQL Database: osTicket\
  - MySQL username and password "root"
  - Click install now
<h1>CONGRAGULATIONS</h1>
<h2>I Hope you enjoyed my guide to intalling osTicket</h2>

</p>
<br />
