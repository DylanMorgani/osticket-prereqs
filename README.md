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
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h2>3. Install osticket, IIS, and Dependecies</h2>

- install this folder in the virtual machine using this link (https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD)  this is a folder containing all dependecies and osticket
- Install/Enable IIS in windows with CGI
  - go to windows settings
  - go to programs
  - select turn windows features on or off
  - turn on Internet Information Services (IIS)
  - expand IIS → expand World Wide Web Services → expand Application development features → enable CGI
  - click ok and wait for installation to complete
- go to web browser and search for (127.0.0.1) to make sure its working
- Go to the osticket folder and download PHP manager
- In the same folder install the rewrite module
- Create the directory C:\PHP
- From the osticket folder Unzip the Php zip into C:\PHP
- From the osticket folder, download the VC_redist exe
- From the osticket folder, Install MySQL
  - Typical Setup
  - Lauch configuration Wizard (after install)
  - Standard Configuration
  - For the username and password :root
- search for IIS in the windows search and run as admin
  - from within IIS open PSP manager
  - register new PHP version (browse to C:\PHP  and select the application)
  - Reload IIS by stoping and restarting the server
- From the Osticket installation folder, extract osticket
  - copy the upload folder into "C:\inetpub\wwwroot" then rename the upload folder to "osTicket"
- Restart IIS Again
- 
</p>
<br />
