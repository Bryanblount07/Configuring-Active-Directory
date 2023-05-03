<p align="center">
<img src="https://imgur.com/6Jj8Fd0.png" alt="Active Directory logo"/>
</p>

<h1>Configuring Active Directory On Premises</h1>
This tutorial outlines Active Directory from start to finish. From installing to making security groups & also DNS settings & private IP Addresses.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory
- DNS

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- VM (Windows Server 2002)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- Install Active Directory
- Topology with Network Watcher

<h2>Installation Steps</h2>

<p>
<img src="https://imgur.com/8YRlzfs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Microsoft Azure search "Virtual Machine" & click create. Create a resource group named AD-Lab. Name the VM DC-1 & Choose your region. Find and select windows server 2022. scroll down and create user name, password & Click Create.
</p>
<br />

<p>
<img src="https://imgur.com/8YRlzfs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Microsoft Azure search "Virtual Machine" & click create. Click resource group and click on AD-Lab. Name the VM client 1 & Choose same region. Find and select windows 10. scroll down and create same user name, same password & Click next until you get to network. Make sure its in AD-Lab v-net. Create.
</p>
<br />

<p>
<img src="https://imgur.com/Q6iOtJE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to DC-1 Virtual Machine. Click networking & find Networking interface. Then click IP configurations, IP dynamic & change to static & save. Make sure they are in the same network. Go back to Virrtual Machines, ctl+click both and make sure they are in the same network. 
</p>
<br />

<p>
<img src="https://imgur.com/p5YDyeh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now enable ICMPv4 in DC-1 (Domain Controller). Go to client 1 & copy the public IP Address. Then open up remote desktop & paste the IP Address. Hit connect & yes.
</p>
<br />

<p>
<img src="https://imgur.com/Cp0EUel.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we're going to ping DC-1 private IP Address. Go back to virtual machines, click DC-1 & copy the Private IP Address. 
</p>
<br />

<p>
<img src="https://imgur.com/UWNaoto.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to client-1 remote desktop, go to start & search Command line. type ping -t and paste the ip address we copied. it should time out because the firewall should be blocking it.
</p>
<br />

<p>
<img src="https://imgur.com/W6UwAOv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open up another remote desktop. Go to your virtual machine and click DC-1 & copy public IP Address and paste DC-1 address in and connect. Put in the username & password you created when you made the VM & log in. 
</p>
<br />

<p>
<img src="https://imgur.com/undefined.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now we're going to install Active Directory Domain Serves. Open DC-1 VM. Go to start and click on service manager. click on add roles & features, Click next unti you get to server roles & add Active Directory Domain Services. Next through everything and install.
</p>
<br />

<p>
<img src="https://imgur.com/NbB6CO7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In your DC-1 you will see an Flag with a caution triangle on it at the top right of the screen. Click it and add domain. Click on add new forest and name your domain anything you want. Give a password and click next. Next through everything and install. It should restart. 
</p>
<br />

<p>
<img src="https://imgur.com/DbRivFS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
When you log back in you'll need to use your domain controller name. ex: i use mydomain.com. So my user name will be mydomain.comLabuser then the password.
</p>
<br />

<p>
<img src="https://i.imgur.com/0YSEVv0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
So now you want to go back to the google drive files and downlaod the os-ticet file. Open the os-ticket file & also open another file explorer to transfer the [upload] file from the os-Ticket folder into your c:\inetpub\wwwroot. Then rename the upload folder to "osTicket" [with no spaces] . Then go back to the IIS manager and hit restart again.
</p>
<br />

<p>
<img src="https://i.imgur.com/upbZ4yi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Inside ISS Manager go to sites -> Default -> os-Ticket, Dobuble click PHP Manger, Click [Enable or disable an extension]. Enable : php_imap.dll, php_intl.dll, php_opcache.dll. Then refresh osTicket in your browser. The red X's should turn green & the bottom 2 should still be red.
</p>
<br />

<p>
<img src="https://i.imgur.com/SgrNirI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open your file explorer, go to your C: Drive, inetpub, wwwroot, include & find file ost-sampleconfig.php & change to ost-config.php. Then right click on that same file and go to properties, security, advance then disable inheritence. Click remove all inherited permissions from this project. Then click add permissions, click select principal. type everyone and click check names. Then give everyone full control. click ok, apply & then ok.
</p>
<br />

<p>
<img src="https://i.imgur.com/WpO640F.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Move to your osTicket "in the browser" & click continue & fillout the fields and write them in notepad we'll need them later. Then install HeidiSQL in the install files in google drive. Click on everything and click launch. In Heidi click new and put Password1 for the password then click open.
</p>
<br />

<p>
<img src="https://imgur.com/HulKBrW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In osTicket in the MySQL username put "root" and password is "Password1" or what ever you set yours to. Now we have to create a new database in HeidiSQL called osTicket. 1.) Right click Unammed 2.) Create new 3.) database. 4.) Name it osTicket and click ok
</p>
<br />

<p>
<img src="https://i.imgur.com/WpO640F.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 Go back to osTicket browser & go to the MYSQL Database & type in [osticket] put [root] for username & [Password1] or the password you created. Then click install.
</p>
<br />

<p>
<img src="https://i.imgur.com/jDUyOni.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
 Your osTicket should look like image above. Then go into your c:\inetpub\wwwroot\osticket\setup. delete the setup folder ONLY.
</p>
<br />

<p>
<img src="https://i.imgur.com/5xrKcma.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to your c:\inetpub\wwwroot\osticket & delete setup folder. Then go to c:\inetpub\wwwroot\osticket\include\ost-config.php right click on file and got to properties, security, advance then go to everyone edit it and only check read and exucute & read. Click ok, then apply, then ok like the image.
</p>
<br />

<p>
<img src="https://i.imgur.com/qA2gvJu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now log in with the username and password. You should see this screen when successfully logged in.
</p>
<br />
