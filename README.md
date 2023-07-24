# Microsoft-IIS
Running OSSN on IIS (We still don't official support IIS) but OSSN works well with it. 

## Server creation / Pre-requisites

- Making sure Windows Server 2019 or newer
- Making sure IIS 10 or larger is setup
- Making sure to install CGI for IIS (IIS -> Applications -> CGI when Adding new ROLE), remember to find it you need to click small arrow in the list of IIS.

  ![image](https://github.com/opensource-socialnetwork/Microsoft-IIS/assets/805066/bab9ef3d-7d1e-4efb-86d3-0fd0ee30527b)

- Installation of PHP 8.1 C:\PHP\
- Installation of ioncube loader 12 if using premium social network
- Once installed PHP add it into environment variable C:\PHP\
- Verify environment variable by restarting CMD and run `php -version`
- Now add FastCGIModule for IIS Under `Handler Mapping`

  ![image](https://github.com/opensource-socialnetwork/Microsoft-IIS/assets/805066/a7cf8e4a-d2a9-4bc7-95c2-930072912201)
  
  Request path: *.php
  Module: FastCgiModule
  Executable: "C:\PHP\php-cgi.exe"
  Name: PHP via FastCGI  

  ![image](https://github.com/opensource-socialnetwork/Microsoft-IIS/assets/805066/d5a0393e-1b8c-4f3a-9de3-741c3b6f9fc2)

- Now put index.php with content
   ```    
   <?php 
   phpinfo();
   ```
- RUN http://127.0.0.1/index.php and see if you see php information if so that means php works.
- Now install MySQL with MySQL workbench to manage database.  If you wanted to use MariaDB then install that.
- Create database for OSSN

## OSSN installation
 - Download latest version
 - Put it under C:\inetpub\wwwroot\
 - Extrat the content of this repository in C:\inetpub\wwwroot\
 - Now create a folder C:\inetpub\ossn_data\

## ADDING WRITEABLE PERMISSIONS
 - Right click on C:\inetpub\ossn_data\ `ossn_data` folder and go to security tab -> Add
   ![image](https://github.com/opensource-socialnetwork/Microsoft-IIS/assets/805066/fc42054f-d254-40f4-9788-6221843bf538)
- After adding select the `IIS_IUSRS`user with making sure in bottom you select Full control.
- Same with C:\inetpub\wwwroot\ in this step you only need to select `IIS_IUSRS` 
![image](https://github.com/opensource-socialnetwork/Microsoft-IIS/assets/805066/d6da43d0-a643-48ce-8fea-c5f3b72797bc)

# Access installer

Now access the installer by http://127.0.0.1/

