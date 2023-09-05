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
Before you proceed with installing osTicket, you need to configure PHP within IIS using the PHP Manager. Here are the steps:

1. **Open IIS as an Admin**:
   - Ensure that you are logged in as an administrator on your Windows server.
   - Press the **Windows key**, type "IIS," and right-click on "Internet Information Services (IIS) Manager."
   - Select "Run as administrator" to open IIS with administrative privileges.

2. **Access PHP Manager**:
   - In IIS Manager, select your server in the left-hand Connections pane.

3. **Double-Click "PHP Manager"**:
   - Double-click on the "PHP Manager" icon in the center pane. This will open the PHP Manager interface.

4. **Register New PHP Version**:
   - In PHP Manager, click on the "Register new PHP version" option.

5. **Browse for PHP CGI Executable**:
   - Click on the "Browse" button to locate the PHP CGI executable file (php-cgi.exe) within the PHP folder you created earlier during the lab setup.

6. **Select php-cgi.exe**:
   - Navigate to the PHP folder you created (e.g., "C:\PHP") and select the "php-cgi.exe" file.

7. **Register PHP Version**:
   - After selecting "php-cgi.exe," click "OK" or "Open" to register this PHP version with IIS.

8. **Reload IIS Server**:
   - Finally, in the IIS Manager, you can reload the IIS server to apply the changes. You can do this by selecting your server in the Connections pane and clicking on the "Restart" option in the right-hand Actions pane.

By following these steps, you will have configured PHP within IIS using PHP Manager, ensuring that PHP is properly registered and can be used for osTicket and other web applications hosted on your server.</p>
<br />

<p>
<img src="https://i.imgur.com/dEvHz6n.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>

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
</p>
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

<br />

<p>
<img src="https://i.imgur.com/CdkPTsv.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
1. **Open IIS Manager**:
   - Launch the Internet Information Services (IIS) Manager on your Windows server.

2. **Navigate to PHP Manager**:
   - In IIS Manager, select your server in the Connections pane on the left-hand side.

3. **Click on "PHP Manager"**:
   - In the center pane, under "IIS," you should see an icon labeled "PHP Manager" if PHP is installed correctly. Click on it.

4. **Enable or Disable an Extension**:
   - In the PHP Manager menu, under the "PHP Extensions" section, click on "Enable or disable an extension."

5. **Enable Extensions**:
   - In the "Enable or Disable an Extension" window, you'll see a list of available PHP extensions.
   - Find and enable the following extensions by checking the corresponding checkboxes:
     - `php_imap.dll`
     - `php_intl.dll`
     - `php_opcache.dll`

6. **Apply Changes**:
   - After selecting these extensions, click the "Apply Changes" button to enable them.

7. **Restart IIS**:
   - To ensure that the changes take effect, it's a good practice to restart the IIS server. You can do this by selecting your server in the Connections pane, and in the Actions pane on the right-hand side, click on "Restart."
<img src="https://i.imgur.com/5ggnkk9.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
Before proceeding with the osTicket installation, you need to rename a file and change its permissions as follows:

1. **Rename the File**:

   - Navigate to the directory: `C:\inetpub\wwwroot\osTicket\include`.
   - In this directory, you should find a file named `ost-sampleconfig.php`.
   - Rename `ost-sampleconfig.php` to `ost-config.php`. You can do this by right-clicking the file, selecting "Rename," and then entering the new name.

2. **Change File Permissions**:

   - Right-click on the newly renamed `ost-config.php` file and select "Properties."

3. **Disable Inheritance**:

   - In the Properties window, go to the "Security" tab.
   - Click on the "Advanced" button to access advanced security settings.

4. **Remove All Inherited Permissions**:

   - In the "Advanced Security Settings for ost-config.php" window, click on the "Disable inheritance" button.
   - A prompt will appear asking if you want to remove all inherited permissions. Confirm by selecting "Remove all inherited permissions from this object."

5. **Add New Permissions**:

   - Back in the "Advanced Security Settings" window, click the "Add" button to add new permissions.

6. **Set Permissions for "Everyone"**:

   - In the "Select a principal" dialog box, type "Everyone" into the object name field, and then click "Check Names" to validate it.
   - Click "OK" to confirm "Everyone" as the principal.

7. **Set Permissions for "Everyone" to "All"**:

   - In the "Permission Entry" dialog box, under the "Basic Permissions" section, check the box for "Full control" to grant full permissions to everyone.
   - Click "OK" to apply the changes.

8. **Apply and Close**:

   - Back in the "Advanced Security Settings" window, you should now see "Everyone" listed with "Full control" permissions.
   - Click "OK" to close the "Advanced Security Settings" window.

By following these steps, you have renamed the file to `ost-config.php` and adjusted its permissions to grant full control to everyone. This should ensure that osTicket can access and modify this configuration file as needed during the installation and operation of the ticketing system.
</p>
<br />

<p>
<img src="https://i.imgur.com/zExrqYG.png" height="80%" width="80%" alt="Installation Steps"/>
<img src="https://i.imgur.com/PiJMYZ6.png" height="80%" width="80%" alt="Installation Steps"/>
</p>
<p>
1. **Download and Install HeidiSQL**:

   - Download the HeidiSQL installer from the installation files and run it.
   - Follow the on-screen instructions to install HeidiSQL on your Windows machine.

2. **Launch HeidiSQL**:

   - After the installation is complete, launch HeidiSQL from your computer.

3. **Create a New Session**:

   - In HeidiSQL, click on "File" in the top-left corner.
   - Select "New Session" from the dropdown menu.

4. **Configure the Connection**:

   - In the "Session manager" window:
     - Enter a session name (e.g., "osTicket Database").
     - In the "Settings" tab, configure the following:
       - **Network Type**: MySQL (TCP/IP).
       - **Hostname / IP**: Enter the IP address or hostname of your MySQL server.
       - **User**: Enter the username (usually "root" by default).
       - **Password**: Enter the password you used during the MySQL installation earlier.
     - Leave other settings at their defaults unless you have specific requirements.

5. **Connect to the MySQL Server**:

   - Click the "Open" button to connect to the MySQL server using the provided credentials.

6. **Create a New Database**:

   - In the left-hand panel of HeidiSQL, you'll see a tree structure with your MySQL server connection.
   - Right-click on "Unnamed" (or your server name) and select "Create New" > "Database."

7. **Enter Database Details**:

   - In the "Create New Database" dialog:
     - Enter "osTicket" as the "Database name."
     - Choose the default character set and collation unless you have specific requirements.
     - Click "OK" to create the new database.

8. **Confirm Database Creation**:

   - You should now see the "osTicket" database listed under your MySQL server connection in the left-hand panel of HeidiSQL.

You have successfully installed HeidiSQL, created a new session, and created a new database named "osTicket" within that session. This database will be used for your osTicket installation and configuration.
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
To complete the cleanup process after installing osTicket, follow these steps:

1. **Delete the Setup Folder**:
   - Navigate to the `C:\inetpub\wwwroot\osTicket` directory.
   - Locate and delete the "setup" folder. This folder was used during the initial osTicket setup but is no longer needed.

2. **Change Permissions for ost-config.php**:
   - Navigate to the `C:\inetpub\wwwroot\osTicket\include` directory.
   - Locate the `ost-config.php` file.

3. **Open File Properties**:
   - Right-click on `ost-config.php` and select "Properties."

4. **Modify Permissions**:
   - In the "Properties" window, go to the "Security" tab.

5. **Change Permissions to "Read" Only**:
   - In the "Group or user names" section, select "Everyone."
   - In the "Permissions for Everyone" section, click on "Full Control" to deselect all permissions.
   - Now, select "Read" to grant read-only permissions to the file for everyone.
   
6. **Apply Changes**:
   - Click "OK" to apply the new permissions.

By following these steps, you have deleted the unnecessary "setup" folder and adjusted the permissions for the `ost-config.php` file to make it read-only for everyone. These clean-up steps ensure that your osTicket installation is secure and ready for use.
</p>
<br />

<h2>osTicket Installed!</h2>
