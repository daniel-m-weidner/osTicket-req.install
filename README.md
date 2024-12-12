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
<img src="https://i.imgur.com/wDvE1cl.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>

<p>
<img src="https://i.imgur.com/ggMfN3Q.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.

<p>
<img src="https://i.imgur.com/drNpQHi.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/7MnmxpE.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
</p>
<p>
After a successful connection is established, we will need to install the programs and files mentioned before, however first we will enable IIS with CGI on as well, which can be accessed through searching "turn Windows features on or off" in the Start menu. Upon opening, select "Internet Information Services", and then expand the selection, expand "World Wide Web Services", and "Application Development Features". There, you will find CGI, tick the box and press OK and the features will be applied after a few minutes. To test the Webserver, you may enter the loopback address 127.0.0.1 into a browser and you will be greeted with the default IIS landing page.
<p>
<img src="https://i.imgur.com/DhJS6hZ.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now it is time to install our programs, as well as implement PHP. First, install PHP Manager and the Rewrite Module. If there are any neccessary installation adjustments, I will mention it. 
</p>
<br />
