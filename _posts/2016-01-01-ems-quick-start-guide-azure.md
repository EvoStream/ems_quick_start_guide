---
title: Quick Start Guide for Microsoft Azure
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: quick_start_guide_for_azure
---


## Purpose

This document describes how to set up a virtual machine with EvoStream Media Server software on Microsoft Azure, an open, flexible, enterprise-grade cloud computing platform.

Microsoft Azure is a cloud-computing platform that virtualizes computing resources as virtual machines. EvoStream provides a Linux and Windows machine with a preconfigured version of EvoStream Media Server that is ready to start using Azure services. You can use this machine to launch EMS, paying for your running instance time and bandwidth consumption only while the instances are running. You can launch EMS instances in specific geographical locations that are closer to your audience to reduce latency and in multiple geographical locations to provide high levels of redundancy.





## Getting Started

### Pre-requisites

- Microsoft Account
  
  ​

### Setup Virtual Machine Environment

To get started with the EvoStream Media Server (EMS) on Azure, the first thing to do is to setup the virtual machine by simply following these steps:

- _Quick-Deploy: Steps 1 and 2 below can be skipped by clicking one of the following buttons:_  
  - _Quick-Deploy EvoStream Media Server 1.7.1 for Windows Server 2012 R2_  
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FEvoStream%2Fevostream_addons%2Fmaster%2Fazure_templates%2Fems171_windows2012%2Fazuredeploy.json" target="_blank"><img src="http://azuredeploy.net/deploybutton.png"/></a>
  - _Quick-Deploy EvoStream Media Server 1.7.1 for Ubuntu 14.04 64-bit_  
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FEvoStream%2Fevostream_addons%2Fmaster%2Fazure_templates%2Fems171_ubuntu1404%2Fazuredeploy.json" target="_blank"><img src="http://azuredeploy.net/deploybutton.png"/></a>

1. Search for the EvoStream Media Server in the Azure marketplace, or simply follow this link: 
   
   https://azure.microsoft.com/en-us/marketplace/partners/evostream-inc/evostream-media-server/
   
   ![]({{site.baseurl}}/assets/homepage.JPG)
   
   ​
   
2. Select the operating system for the virtual machine to be created. Click on **Create Virtual Machine** button.
   
   ![]({{site.baseurl}}/assets/OSselect.jpg)
   
   ​
   
   **Images available:**
   
   - EvoStream Media Server for Windows - Windows Server 2012 R2
   - EvoStream Media Server for Ubuntu - Ubuntu 14.04 64-bit
   
   ​
   
3. **Sign in** your Microsoft Azure account if not yet signed in. You will be redirected to the EvoStream Media Server page.  Read on the notes and if ready, click on the **Create** button.
   
   ![]({{site.baseurl}}/assets/create_windows.JPG)
   
   ​
   
4. Configure the virtual machine settings based on your preferences
   
5. Review the Settings, Offer Details and Terms of Use then click **Purchase** to start the deployment
   
6. To check if the image has been created, on the Microsoft Azure Dashboard, click on the **Virtual machines**. You will now see the image created once the deployment succeeded.

**Note:** The machine is started after the deployment



### Connecting to EMS machine

All the virtual machines in your account is seen under the Virtual machines in the left-side menu bar. 

Click on the Virtual Machine name. Click on **Start**.

![]({{site.baseurl}}/assets/startVM.JPG)





#### Connecting via SSH from Linux Terminal

1. Send command: 
   
   ``` 
   ssh <username>@<IP_address>
   ```
   
   The username and password is set in step 4 above.
   
   ``` 
   user@ubuntu:~/Desktop$ ssh user@11.221.105.202
   
   The authenticity of host '111.221.105.202 (111.221.105.202)' can't be established.
   RSA key fingerprint is ae:02:ee:41:ff:38:96:ab:78:7b:3a:e6:09:ed:1f:4c.
   Are you sure you want to continue connecting (yes/no)? 
   ```
   
2. Input “**yes**”, press **Enter**
   
   ``` 
   Warning: Permanently added '111.221.105.202' (RSA) to the list of known hosts.
   user@111.221.105.202's password:
   ```
   
3. Enter password, press **Enter**. A welcome note will open. You then need to **<u>install the license</u>** to be able to use the EMS capabilities.

**Note:** The license should be placed in `/etc/evostreamms` for Linux and in `./config` in Windows





#### Connecting  via SSH from Windows (PuTTy)

**Pre-requisites:**

- PuTTY Secure Shell Client



1. Run **PuTTY**
   
2. Select **Session** under the category tree
   
   ![]({{site.baseurl}}/assets/image16.png)
   
   ​
   
3. Specify the destination you want to connect to:
   
   ![]({{site.baseurl}}/assets/putty.JPG)
   
   ​
   
   **Host Name** – the username and public IP address in Azure virtual machine running EvoStream Media Server
   
   **Port** – 22 (default)
   
   **Connection type** – SSH
   
   ​
   
4. Click **Open**
   
5. Click  **Yes** to accept the security key on the PuTTy Security Alert Window
   
6. Enter the username's password, hit **Enter**
   
   ``` 
   Using username "EvoStream".
   EvoStream@111.221.105.202's password: 
   ```
   
7. You are now connected to the machine! You then need to **<u>install the license</u>** to be able to use the EMS capabilities.
   
   **Note:** The license should be placed in `/etc/evostreamms` for Linux and in `./config` in Windows
   
   ​



#### Connecting via Remote Desktop

1. Run the **Remote Desktop Application** to be used
   
   **Note:** The remote desktop application will depend on the OS you will use.
   
2. Enter the details of the virtual machine image, click **Connect**
   
   **Computer** -  the IP address of the image
   
   **Username** -  the username set for the image
   
   ![]({{site.baseurl}}/assets/remotedesktop.jpg)
   
   ​
   
3. Enter the **password** for the user, click **OK**
   
4. The connection will be established. You may now **<u>install the license</u>** to use the EMS capabilities!
   
   **Note:** The EMS is installed in `C:\EvoStream`
   
   ​



## EMS Web UI

While most work with the EMS happens at the command line or through the HTTP based API calls, the EMS does have a Web UI that can be used. To access the UI simply point your browser at the proper URL: `http://<DomainOrPublicIP>:8888/EMS_Web_UI/index.php`

< DomainOrPublicIP > will need to be replaced with the Public Domain or Public IP of your new EC2 Instance.



### Determining Public IP

1. Sign in to *http://portal.azure.com/*
   
2. Click on virtual machine created under Virtual Machines menu
   
3. Start the virtual machine
   
4. In the Essentials pane, the Public IP address/DNS name label is displayed
   
   **Note:** The IP address is changing everytime the virtual machine is restarted
   
   ![]({{site.baseurl}}/assets/IPinAzure.jpg)





## Authentication

The authentication is only enabled starting the 1.7.1 version of EMS. The Authentication is enabled by default in EMS Web UI and HTTP Based API.

### Login for Web UI

The Web UI is protected by default when using the EMS on Azure.  When accessing the Web UI you will be prompted for a username and password.

![]({{site.baseurl}}/assets/authentication.JPG)

- Username: evostream
- Password: "UID" - the unique identifier of the virtual machine, this will be seen in webconfig.lua



### HTTP Based API

For the EMS on Azure, the HTTP based API is exposed, but it requires authentication to be used.  We call this **Proxy Authentication**. Basic Authentication is used and so just a username and password are required:

- Username: evostream
- Password: "UID" - the unique identifier of the virtual machine, this will be seen in webconfig.lua

Command will take this general format:

``` 
http://Username:Password@IPAddress:Port/apiproxy/CommandName?params=<base64EncodedString>
```

**Sample Command:** 

``` 
http://evostream:i-D817E76F-B6F2-CC4F-ACAC-EAE9D84CEE3F@52.91.237.115:8888/apiproxy/version
```

**Note:** username is “**evostream**” and password is the “**UID**”

See [Proxy Authentication](http://docs.evostream.com/ems_user_guide/runtimeapi#http) for more details.



### Getting the Unique ID

The UID will serves as the password for the Proxy and Web UI authentication. The UID is obtained once a virtual machine is made. It can only be checked in the EMS webconfig.lua.

**in webconfig.lua:**

``` 
apiProxy=
{
   authentication="basic",
   pseudoDomain="apiproxy",
   address="127.0.0.1",
   port=7777,
   userName="evostream",
   password="D817E76F-B6F2-CC4F-ACAC-EAE9D84CEE3F",   --> sample UID
}
```





## Terminating EMS machine

### Stopping EMS machine

When you want to stop the virtual machine, fret not, all the changes remains in the server. The machine is only in suspended.

1. Click on the Virtual machine menu
2. Right click on the virtual machine name, click on **Stop**
3. or, simply click **Stop** on the virtual machine window
4. Confirm stopping the virtual machine by clicking **Yes**

![]({{site.baseurl}}/assets/stopVM.JPG)



### Deleting EMS machine

Deleting the EMS virtual machine will remove all the changes and the virtual machine itself in the Azure Virtual Machine list. 

1. Click on the Virtual machine menu
2. Right click on the virtual machine name, click on **Delete**
3. or, simply click **Delete** on the virtual machine window
4. Choose if you want to delete or keep the attached disk

![]({{site.baseurl}}/assets/deleteVM.jpg)
