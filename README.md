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

- Windows 10</b> (21H2)

<h2>Requirements</h2>

You will require the following programs/files in order to install and run osTicket
- HeidiSQL                                                https://www.heidisql.com/download.php
- MySQL                                                   https://dev.mysql.com/downloads/installer/
- osTicket core files                                     https://osticket.com/download/
- php files + php manager for IIS                         https://windows.php.net/download/    https://www.iis.net/downloads/community/2018/05/php-manager-150-for-iis-10
- iis url rewrite module 2 + Visual C++ 2015-2022 redist  https://www.iis.net/downloads/microsoft/url-rewrite https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#latest-microsoft-visual-c-redistributable-version

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/FnphtDQ.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/KdW2nzu.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
To start off, we first have to create a Virtual Machine within Azure. Preferrably set up a new resource group, name the VM, select your region of choice, and for the disk image choose Win10 Pro. For the size/computing power just make sure you have enough power, otherwise the experience will be slow. Choose your account username and password and you will be able to choose review and create, and then create after validation. The deployment will take some time and Azure should notify you when complete. When ready, in the seach bar find "Virtual Machines" and you will see it listed there. There you can find the public IP, simply copy it.
<p>
<img src="https://i.imgur.com/drNpQHi.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/7MnmxpE.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open "Remote Desktop Connection" on your Windows PC, if you are a Mac user, you need to install the corresponding app first. Insert the IP and username. Now, it will prompt you to enter the password. If the program asks you to confirm something, just click accept/yes. After a successful connection is established, we will need to install the programs and files mentioned before, however first we will enable IIS with CGI on as well, which can be accessed through searching "turn Windows features on or off" in the Start menu. Upon opening, select "Internet Information Services", and then expand the selection, expand "World Wide Web Services", and "Application Development Features". There, you will find CGI, tick the box and press OK and the features will be applied after a few minutes. To test the Webserver, you may enter the loopback address 127.0.0.1 into a browser and you will be greeted with the default IIS landing page.
<p>
<img src="https://i.imgur.com/DhJS6hZ.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/YUjG5yh.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now it is time to install our programs, as well as implement PHP. First, install PHP Manager and the Rewrite Module. If there are any neccessary installation adjustments, I will mention it here. Afterwards, preate a folder labeled "PHP" on the main directory of the PC/VM Hard Drive, usually, the C: drive. Extract the contents of the PHP folder into the empty PHP folder you have created. To do this, right-click the downloaded PHP folder and select "Extract all" you can now select the empty folder to extract into, as seen on my screenshot above. Now, install Visual C++, and MySQL. In the installation wizard, choose typical installation, and upon completion, lauch the config wizard. Choose standard config and click next until you are asked to enter a root password. This is Very Important. Only enter a password that you can remember later. I suggest writing it down in some way. Click "next" and "execute". You now have installed MySQL.
</p>
<br />
<p>
<img src="https://i.imgur.com/RMseTg0.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this step, we are registering PHP inside the IIS manager. Type IIS in the windows Start menu and you will be able to open it. CLick "Register new PHP version" and you can select the PHP executable (php-cgi.exe) that is located in the PHP folder we have created (C:\PHP\). Hit OK and it is finished.
<p>
<img src="https://i.imgur.com/r0shrtS.png" height="30%" width="30%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/mS8mOMx.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now you only need to restart the webserver. Right-click on the Server name and select "stop", wait for a moment and select "start". Now the time has come to install osTicket itself. Simply extract the osTicket folder in the same folder that it is in, (e.g. the downloads folder), with the same method you used with the PHP folder. You will have two folders now, we will focus on the "upload" folder now. I suggest to open a second instance of the file browser. Navigate to C:\inetpub\wwwroot and move the contents of "uplaod" into that folder. Now simply rename "upload" into osTicket. Restart the webserver, as before. Now, you'll be able to expand "Sites">"Default Web Site">"osTicket". You will see a browse option pop up on the right-hand side of the window, through the HTTP protocol (port 80). 
<p>
<img src="https://i.imgur.com/OMuOUBg.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/XeixhER.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now you will be greeted with a window in your browser, which is the osTicket installer. It will list out Requirements, as well as Recommendations for the installation. Leave the page open and go back to IIS manager. Click on the osTicket folder and double-click PHP manager. Click on "Enable or Disable an Extension" on the bottom. Now find and enable three items in the disabled section: php_imap.dll; php_intl.dll; php_opcache.dll. Simply right-click those elements and click enable. Once that is finished, you can click on the osTicket folder to return to the main page in ISS manager. Click Continue in the osTicket installer and it will show you what is left to set up. 
<p>
<img src="https://i.imgur.com/rTL7BMs.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/b7IQ7uu.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
Navigate to C:\inetpub\wwwroot\osTicket\include\ and you can search for ost-sampleconfig.php within the folder. rename it to ost-config.php make sure there are no typos and a dash is included as shown. Right-click that file, select properties>security>advanced. Select "disable inheritance". In the dialogue window, select "remove all...". Now click "Add" and click on "Select a principal". A new Window opens and you can simply type "everyone" into the name field. Click Ok and now make sure you tick the "write" access box. Click OK two more times on the corresponding windows. This is not the preferrable way to do it in a real setting, however for the sake of this tutorial, it is an easy way to make osTicket function. Now click "Continue" on the osTicket intaller window.
<p>
<img src="https://i.imgur.com/kILSA5i.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/aALytrp.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/RlrXF8f.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
For the sake of this tutorial, I have used made-up email adresses. Fill out the information as you see fit, however amke sure you remember the password later when we sign in. Before proceeding, please install HeidiSQL, which you have downloaded in the beginning. After installation, launch it and hit "skip". Now, click on "New" and it will show the setup that we have created with MySQL. You only need to enter the password you have created during the MySQL installation. Once you click on "open", you arre connected to the SQL database. Right-click on "Unnamed" and select create new>database. Name it "osTicket". Make sure it is spelled correctly. Now that the database it established, you will be able to enter that information into the database section of the osTicket installer. For MySQL database, enter "osTicket", and for username and password, enter your MySQL credentials. Now click "Install Now"
<p>
<img src="https://i.imgur.com/CBomh8o.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
That's all! osTicket will congratulate you for successfully installing their program. Now make sure you save the osTicket URL, as well as the Staff Control Panel URL in the browser or in a text  document. They are usually http://localhost/osTicket/ and http://localhost/osTicket/scp/login.php. You will be able to jus tlogin with the admin credentials you entered on the osTicket signup/install. It will ask you to delete the setup folder in C:\inetpub\wwwroot\osTicket, as well as remove the write access in the config file, which we had enabled earlier (ost-config.php).
<p>
<img src="https://i.imgur.com/TJ9Jgcu.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/6jc4PZQ.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
Make sure you stop or delete the Virtual Machine after using osTicket this way to make sure there is no cost incurred through Azure. If you stop it, you will be able to use it at a later time.
