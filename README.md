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
In Microsoft Azure search "Resource Group" click on it and click create.
</p>
<br />

<p>
<img src="https://i.imgur.com/pOSnast.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a resource group and name it "os-Ticket". Then click "Review & Create" Then when the "validation passes" click "Create".
</p>
<br />

<p>
<img src="https://i.imgur.com/LeYGT0k.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
1) Click on your VM you named (os-ticket). 2) Make sure the resource group is the same name that you created in the resource group part. 3) Open up remote desktop in your windows machine from the search bar of your computer. 4) then you want to go to your Virtual Machine & find your VM's public IP Address & copy it. 5) Paste the IP address you just copied, to your remote desktop & hit connect. After it connect successfully connect hit "yes".
</p>
<br />

<p>
<img src="https://i.imgur.com/e8YhMId.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on use a different account and log in using the account & pw you used on the "os-ticket" VM. After it connect successfully connect hit "yes". You should have a seperate window pop up loading a windows browser.
</p>
<br />

<p>
<img src="https://i.imgur.com/qQyYNry.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
On your computer (Not the VM) go to the control panel. You can do this by searching control panel in your windows. Click on programs. After that you should see option under programs & features. Select the one with the shield that say "Turn windows features on or off". Here you will find the feature thats in the photo above. 1) find "Internet Information Service" & click it so it drops down. 2) Find "World Wide Web" under the "Internet Information Services" drop down menu & select that to drop down more options. 3) Find CGI under "World Wide Web" and check it to turn the CGI on. Then click "OK". After this you'll need to download the neccessary files for the next steps. Here's a link: https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6
</p>
<br />

<p>
<img src="https://i.imgur.com/vvcRCjy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
1.) You want to download the [PHP Mananger For IIS] & run the installation. Nothing special needs to be added. Just next everything & install. 2.) Download & install the [Rewrite Module]. This one is also straight forward & nothing extra needed to install. Just next and Finish. 4.) Next you need to create PHP in your "C: Drive" just like in the image above. Load your file explorer and click on C: Drive. Then right click, click new then folder & name it PHP. 
</p>
<br />

<p>
<img src="https://i.imgur.com/Pgdl9dS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next were going to download the PHP 7.3.8 file & move all files to the PHP file we created in file explorer (Like in the image above). 
</p>
<br />

<p>
<img src="https://i.imgur.com/c3B7zum.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Download My SQL and run the install & at the end make sure the [lauch] is checked so its launched when done installing.It launch another intall and you want to click nect until then Click on [Standard Configuration]. Once you get to the point where you create a  password. Use Password1 for the password [or create your own]. You want to write this on your note pad to remember. hit next and exucute. should look like photo when done.
</p>
<br />

<p>
<img src="https://i.imgur.com/kMY3Q92.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In your VM go to your windows search bar [not your browser] then type in [IIS] right click and run as administrator.
</p>
<br />

<p>
<img src="https://i.imgur.com/YmmvaOb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once open click on PHP Manager, click register new PHP Version, select the 3 dots[...], find the PHP folder we created in our C: Drive & then select the PHP-cgi file and select ok. After that restart it. The restart is on the right side in the Manager Server.
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
