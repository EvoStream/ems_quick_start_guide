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
   
3. Sign in your Microsoft Azure account if not yet signed in. You will be redirected to the EvoStream Media Server page.  Read on the notes and if ready, click on the **Create** button.
   
   ![]({{site.baseurl}}/assets/create_windows.JPG)
   
   ​
   
   ![]({{site.baseurl}}/assets/create_ubuntu.JPG)
   
   ​
   
4. Configure the virtual machine settings based on your preferences
   
5. Review the Settings, Offer Details and Terms of Use then click **Purchase** to start the deployment
   
6. To check if the image has been created, on the Microsoft Azure Dashboard, click on the **Virtual machines**. You will now see the image created once the deployment succeeded.

**Note:** The machine is started after the deployment.



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

**Note:** The license should be placed in `/etc/evostreamms` for Linux and in `./config` in Windows.





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
   
4. Click **Open**
   
5. Click  **Yes** to accept the security key on the PuTTy Security Alert Window
   
6. Enter the username's password, hit **Enter**
   
   ``` 
   Using usernmae "EvoStream".
   EvoStream@111.221.105.202's password: 
   ```
   
7. You are now connected to the machine! You then need to **<u>install the license</u>** to be able to use the EMS capabilities.
   
   **Note:** The license should be placed in `/etc/evostreamms` for Linux and in `./config` in Windows.
   
   ​



#### Connecting via Remote Desktop

**Note:** Remote desktop can only be used for the Windows virtual machine image.

1. Run **Remote Desktop Connection**
   
2. Enter the details of the virtual machine image, click **Connect**
   
   **Computer** -  the IP address of the image
   
   **Username** -  the username set for the image
   
   ![]({{site.baseurl}}/assets/remotedesktop.jpg)
   
   ​
   
3. Enter the password for the user, click **OK**
   
4. The connection will be established. You may now **<u>install the license</u>** to use the EMS capabilities!
   
   **Note:** The EMS is installed in `C:\EvoStream`.
   
   ​





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
