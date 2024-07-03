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

<h2>List of Prerequisites</h2>

- PHP
- HeidiSQL
- mysql
- osTicket
- PHPManager
- rewrite_amd64
- VC_redist.x86

<h2>Installation Steps</h2>

<p>
Create a Windows virtual machine in Microsoft Azure with a minimum of 2 vcpus (virtual cpus).
</p>
<p>
<img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/c2f5f222-19c6-4edf-99df-e55e7743bedf"/>
</p>
<br />

<p>
After you create the VM, the public IP address will be displayed. Use that address to connnect to the machine with the RDP utility on Windows.
</p>
<p>
<img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/c8c056a2-ea35-49d4-a28c-4cb58c11d737"/>
</p>

<br />

<p>
<img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/d006bf10-9eae-4fcc-87c1-d2c94d3d11df"/>
</p>

<br />

<h2>After the VM is up and running</h2>
<p>
The very first thing your gonna do is enable Internet Information Services. To enable the service you can use the run utility and type "control", or just type "control panel" in the search box at the bottom of the screen. Once in the panel click "Programs"
</p>
<p>
<img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/8c70c305-0ada-45bd-8035-a33fa1d6a560"/>
</p>

<br />

<p>
The very next window underneath Programs and Features click "Turn Windows feature on or off"
</p>
<p>
<img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/f7fe93b2-2055-4266-aa26-0309a89d0c24"/>
</p>

<br />

<p>
A small window will pop up. Navigate to Internet Information Services and check the box. Open the tab with the + and under Web Management Tools make sure the IIS Management Console is checked.<br><br>
Open World Wide Web Services -> Application Development Features and check "CGI"<br>
Open Common HTTP Features, make sure everything is check in this folder.<br>
Hit Ok so that it will install IIS (web server)
</p>
<p>
<img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/50246038-24a3-4fde-897c-06cbbe861aa3"/>
</p>

<br />

<p>
You can check to see if everything is up and running by opening a web browser and type 127.0.0.1 or "localhost". You should see a similar page to this.
</p>
<p>
<img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/d423e9a7-b1d7-4010-943b-1426a0b6cbc7"/>
</p>

<br />






<h2>Now lets install the Prerequisites for osTicket</h2>
<p>First Create a directory called "PHP" on the C drive. Then install the Prereqs.</p><br>
<p>
<img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/e1b43c31-e9c1-4c48-a1bd-3bdf9e06cb8a"/>
</p>

<p>
The order I installed them in are as follows:
</p>

<ol>
  <li>PHPMangerforIIS_V1.5.0</li>
  <li>Rewrite_amd64</li>
  <li>Extract php-7.3.8-nts-Win32-VC15-x86 and put it in the PHP folder we created on the C drive.</li>
  <li>VC_redist.x86</li>
  <li>mysql-5.5.62-win32 (typical install)</li>
  <li>Next mysql will launch a Configuration Wizard. Do a Standard Configuration, keep the defaults and REMEMBER YOUR CREDENTIALS! What this does is install an actual database on your computer for osTicket to keep 
   the tickets, users and any other app data stored.</li><br>
  
  <li>Now type "IIS" in the search box and open Internet Information Services Manager as an admin</li><br>
  <img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/12ddc388-e18d-4227-ba08-15e9d2b146aa"/><br></br>

  
  <li>Inside IIS double click PHP manager then under PHP setup you should see and click Register New PHP version.</li>
  <li>Browse to the PHP folder we created on the C drive. Open it and select "php-cgi"</li>
  <li>Go back to the original screen by clicking osTicket (top-left), Then restart the server (top-right)</li>

  <h2>Now its time to install osTicket</h2>
  <li>From the zipfile osTicket-v1.15.8 copy the "upload" folder to `C:\inetpub\wwwroot`. This is the web server's main folder </li>
  <li>Inside `C:\inetpub\wwwroot` rename the newly added upload folder to "osTicket" </li>
  <li>Go back to IIS and Restart it</li>
  <li>Open the sites folder (top-left) -> Default Web Site -> osTicket. Make sure its Higlighted then then click Browse *:80(http) on the right.</li><br>
  <img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/58e2e0a4-1d76-444b-912e-ceb0e07b2abe"/><br></br>
  
  <li>You can also type "localhost" in your web browser and you should see.</li><br></br>
  <img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/2c85894e-76de-4904-a0d3-1d4490920bf6"/><br></br>

  <p>Note that some extensions are not enabled. But we can enable the ones that are necessary for this lab back in IIS.</p>
  <li>Back in IIS navigate to sites -> Default -> osTicket</li>
  <li>Select PHP Manager</li>
  <li>Under PHP Extensions click "Enable or disable and Extension"</li>
  <li>Enable (right-click): php_imap.dll, php_intl.dll, and php_opache.dll</li><br>
  <li>Refresh your web browser and all but the last two items should have a green check.</li>
  <img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/da8e2db7-bec3-44a7-a1d5-4f3f0330e579"/><br></br>

  <h2>Finishing up</h2>
  <li>Open File Explorer and navigate to `C:\inetpub\wwwroot\osTicket\include`. Inside this directory there is a file called "ost-sampleconfig.php" rename it to just "ost-config.php" (just take the sample out)</li>
  <li>Now we're going to set some permissions. Right-click the file, go to properties, select the security tab, click Advanced</li>
  <li>Disable Inheritence (Remove all inherited permissions for this object)</li>
  <li>Click Add, then for selcet a principal type Everyone and give full control (for now), Apply, then Ok</li>
  
  <li>Go back to your Browser and click continue on the osTicket page to setup osTicket in the Browser. Make up your own HelpDesk Name and Admin User. After this theres is one more thing we have to do in order to 
   fill in the information at the end of the page and thats install and configure HeidiSQL.</li>

  <h3>Last prereq HeidiSQL</h3>
  <li>Install HeidiSQL_12.3.0.6589_Setup (nothing special, just go through the setup wizard and install the defaults)</li>
  <li>Create a new connection to the database by clicking "New" (bottom-left)</li><br>
  <img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/199916e9-6f9d-4244-bbd6-f1984b7fcaae"/><br></br>
  
  <li>Here is where you'll enter the password you made when we installed mysql earlier.</li><br>
  <img src="https://github.com/SpyderSec30/osticket-prereqs/assets/174487140/ecdda1a6-0b99-42d7-b75e-044a63675494"/><br></br>
  
  <li></li>
  <li></li>
</ol>  
</br>









<p>
here.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>


<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
