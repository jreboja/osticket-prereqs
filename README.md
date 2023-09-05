<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
In this tutorial, we'll be installing osTicket from scratch on a Windows 10 Pro Virtual Machine created on Azure. Before we can proceed with the installation of the ticketing system, there are a few important preliminary steps to follow. You'll also need to access and utilize the required installation files, which are available <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">here!</a><br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Internet Information Services (IIS)
- MySQL

<h2>Operating Systems Used </h2>

- Windows 10 Pro</b>


<h2>Installation Steps</h2>

<p>
<img src="https://imgur.com/IASqI53.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Before you start installing any files, you'll need to enable Internet Information Services (IIS). This is necessary because we're setting up osTicket on your local system, and it relies on IIS to work properly.

To activate IIS, follow these steps:

1. Open the Control Panel.

2. In the Control Panel, locate the "Programs" section and click on "Turn Windows Features On or Off."

3. In the window that appears, find "Internet Information Services" and expand it.

4. Next, expand "Web Management Tools" and make sure to enable "IIS Management Console."

5. Now, click to expand "World Wide Web Services" and then expand "Application Development Features."

6. Inside the "Application Development Features" section, make sure to enable "CGI."

7. Finally, click "OK" to confirm your selections.

By following these steps, you'll have IIS up and running, allowing you to proceed with the installation of osTicket.
</p>
<br />

<p>
<img src="https://imgur.com/04Uasfc.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Once you've activated IIS, the next steps involve downloading and installing a couple of components:

1. **PHP Manager for IIS**: Head to the installation files folder and download and install "PHPManagerforIIS_V1.5.0.msi."

2. **Rewrite Module**: After you've installed PHP Manager for IIS, proceed to download and install the "rewrite_amd64_en-US.msi."

These two components are essential for configuring and enhancing your IIS setup.
</p>
<br />

<p>
<img src="https://imgur.com/lH8zFgj.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Once you've successfully installed the Rewrite Module, follow these steps to set up a new folder on your C: drive and extract the contents from the PHP 7.3.8 zip folder:

1. **Create a New Folder**: On your C: drive (Windows (C:)), create a new folder or directory named "C:\PHP." This folder will serve as the destination for the PHP files.

2. **Unzip PHP Contents**: Locate the PHP 7.3.8 zip folder (named "php-7.3.8-nts-Win32-VC15-x86.zip") that you downloaded from the installation files. Extract all the files and folders from this zip folder and place them into the newly created "C:\PHP" folder.

By completing these steps, you'll have set up a dedicated folder for PHP and extracted its contents into that directory, which is essential for configuring PHP to work with your IIS setup.
</p>
<br />

<p>
<img src="https://imgur.com/N4aJttU.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
After completing the previous steps, proceed to download and install "VC_redist.x86.exe" from the installation files. This is an important component for ensuring compatibility and functionality within your setup.
</p>
<br />

<p>
<img src="https://imgur.com/4yfyXxK.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Next, follow these steps to download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the installation files:

1. **Download MySQL**: Locate and download the MySQL 5.5.62 installer, which is named "mysql-5.5.62-win32.msi."

2. **Installation Wizard**:
   - Run the installer to launch the MySQL setup wizard.
   - Accept the license agreement by clicking "I agree."

3. **Select Installation Type**:
   - Choose "Typical" as the installation type.

4. **Install**:
   - Click the "Install" button to begin the installation process.

5. **Launch Configuration Wizard**:
   - After the installation is complete, launch the MySQL Configuration Wizard.

6. **Configuration Settings**:
   - In the Configuration Wizard, select "Standard Configuration."

7. **Windows Service**:
   - Make sure to select "Install As Windows Service."

8. **Automatic Launch**:
   - Ensure that the option "Launch the MySQL Server automatically" is checked.

9. **Credentials**:
   - For the purpose of this lab, the standard credentials will be used: Username: "root" and Password: "Password1." Please note that in a real-world scenario, it's crucial to use strong, unique passwords. The use of basic credentials like these is not recommended outside of a controlled lab environment.

10. **Complete Setup**:
    - Follow any remaining prompts in the Configuration Wizard to complete the MySQL installation and configuration.

By following these steps, you will have successfully installed MySQL 5.5.62 with the specified settings. Remember to use secure credentials in production environments to enhance security.
</p>
<br />

<p>
Before installing osTicket, configurations need to be made within IIS. Open IIS as an admin and select PHP Manager. Within PHP Manager, select Register new PHP version. Select Browse and select the PHP CGI executable file (php-cgi.exe) within the PHP folder created earlier in the lab. After registering the PHP version, reload the IIS server within the management console.
</p>
<br />

<p>
<img src="https://i.imgur.com/dEvHz6n.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Certainly, here are the steps to download, extract, and configure osTicket v1.15.8 on your Windows server:

1. **Download osTicket**:
   - Locate and download osTicket version 1.15.8 from the installation files.

2. **Extract the "upload" Folder**:
   - After downloading, extract the contents of the osTicket package.
   - You will find an "upload" folder within the extracted files.

3. **Copy to wwwroot**:
   - Copy the entire "upload" folder.

4. **Paste to c:\inetpub\wwwroot**:
   - Navigate to the `c:\inetpub\wwwroot` directory.

5. **Rename "upload" Folder**:
   - Paste the copied "upload" folder into the `c:\inetpub\wwwroot` directory.
   - Rename the "upload" folder to "osTicket" (without quotes).

6. **Reload IIS**:
   - After renaming the folder, you should reload or restart the Internet Information Services (IIS) server to apply the changes and make osTicket accessible via a web browser.
</p>
<br />

<p>
<img src="https://i.imgur.com/ECTaxS8.png" height="80%" width="80%" alt="Installation Steps"/>
To verify if osTicket has been correctly placed in the directory and is accessible through IIS using the "Browse *:80 (http)" option, follow these steps:

1. **Open IIS Manager**:
   - Press the **Windows key** on your keyboard, type "IIS" or "Internet Information Services," and select the "Internet Information Services (IIS) Manager" from the search results. Alternatively, you can open IIS Manager from the Administrative Tools in the Control Panel.

2. **Navigate to Sites**:
   - In IIS Manager, expand the node for your server in the left-hand Connections pane.
   - Click on the "Sites" node to reveal the list of websites hosted on your server.

3. **Locate Your Website**:
   - In the Sites list, you should see your default website or the website you have configured to host osTicket. The site name should be "osTicket" or the name you gave during configuration.

4. **Right-Click and Choose "Manage Website"**:
   - Right-click on the website name (e.g., "osTicket") and select "Manage Website" from the context menu.

5. **Choose "Browse" Option**:
   - In the "Manage Website" submenu, hover over "Browse" to reveal additional options, and then select "Browse *:80 (http)."

6. **Verify osTicket**:
   - Your default web browser should open, and it should navigate to the osTicket website. You should see the osTicket login page or the initial setup page, indicating that osTicket has been correctly placed in the directory and is accessible through IIS using the "Browse *:80 (http)" option.
<img src="https://i.imgur.com/pNkLVo6.png" height="80%" width="80%" alt="Installation Steps"/>

Checking through "Browse *:80 (http)" in IIS Manager allows you to test the website's accessibility directly within the IIS Manager interface. If you can access osTicket using this method, it indicates that the installation is correct and accessible through your web server.
</p>
<img src="https://i.imgur.com/Mpq7ybU.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Within the IIS console, browse to Sites -> Default -> osTicket. Click "Browse *:80" and the installation page for osTicket will now show up. Some extensions are not enabled and they will be enabled with the IIS console before installing osTicket. To do so, click on PHP Manager while in the osTicket menu in IIS. Click on "Enable or disable an extension." Enable the following extentions: php_imap.dll, php_intl.dll, php_opcache.dll.
</p>
<br />

<p>
<img src="https://i.imgur.com/CdkPTsv.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/5ggnkk9.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Before continuing to install osTicket, a file needs to be renamed as well as have its permissions changed. From C:\inetpub\wwwroot\osTicket\include, rename ost-sampleconfig.php to ost-config.php. The newly named ost-config.php will have its permissions changed. Open its Properties and change the following permissions: Disable inheritence -> Remove All and New Permissions -> Everyone -> All.
</p>
<br />

<p>
<img src="https://i.imgur.com/zExrqYG.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/PiJMYZ6.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
From the installation files, download and install HeidiSQL. Create a new session with HeidiSQL and enter the password used in the installation of MySQL earlier. Within the new session, right-click on Unnamed and create a new database named osTicket. 
</p>
<br />

<p>
<img src="https://i.imgur.com/gOqjR1k.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Within osTicket browser window, enter the necessary details to set up osTicket. For the MySQL database, use the credentials used for MySQL and HeidiSQL.
</p>
<br />

<p>
<img src="https://i.imgur.com/3nczMAD.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/7V2YmH6.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
After everything is done, osTicket should now be installed! Before continuing to use osTicket, some clean up has to be done. First, delete the setup folder found in C:\inetpub\wwwroot\osTicket. Next, return to C:\inetpub\wwwroot\osTicket\include and change the permissions of the ost-config.php file. The file should no longer have full access to Everyone. Revert the permissions to "Read" only. 
</p>
<br />

<h2>osTicket Installed!</h2>

osTicket is now installed and ready to be used. I used osTicket to understand how ticketing systems work amd how to resolve tickets. In IT Support, I have to work with a team to solve a person's IT related issues through the use of a ticketing system. I used this lab as a means to set up a ticketing system from the ground up and lay the grounds for what I will do in the future.
