---
title: Quick Start Guide for Microsoft Azure
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: quick_start_guide_for_azureloadbalancer
---


## Purpose

This document describes how to set up the EvoStream HTML5 Low-Latency Broadcast Template on Microsoft Azure.

This template will provide you with a flexible an scalable Origin-Edge distribution platform for low-latent HTML5 video streaming.  An Azure Scale Set is used to scale your Edge Virtual Machines and an Azure Load Balancer handles the distribution of load accross the active Edge VM's.  An Origin Server is provided to source the streams.  

A Stream Manager virtual machine is used to manage the distributions of streams between origin and edge.

![]({{site.baseURL}}/assets/azure.png)



For more information with Azure Load Balancer, see documentation [here](https://docs.microsoft.com/en-us/azure/load-balancer/load-balancer-overview).



## Getting Started

### Pre-requisites

- Microsoft Account
- Working knowledge of Azure virtual machines
- Working knowledge of OTT Video Streaming

  ​

### Setup Virtual Machine Environment

To get started with the EvoStream Media Server (EMS) on Azure, the first thing to do is to setup the virtual machine by simply following these steps:

1. Search for the EvoStream Media Server in the Azure marketplace, or simply follow this link: 

   https://azure.microsoft.com/en-us/marketplace/partners/evostream-inc/evostream-media-server/

   ​

2. Select the operating system for the virtual machine to be created. Click on **Create Virtual Machine** button.

   ![]({{site.baseURL}}/assets/createVM.JPG)

   ​

   **Image available:**

   - EvoStream Media Server for Ubuntu - Ubuntu 16.04 64-bit

   ​

3. Configure the virtual machine settings based on your preferences:

   A. Basics - configure basic settings

   - Unique Suffix
   - Username
   - Subscription
   - Resource Group
   - Location

   B. VM Configuration - configure the VMs

   - VM Size 
   - Admin password
   - Confirm password
   - HTTP password
   - Confirm password

   ​

4. Review the Settings, Offer Details and Terms of Use then click **Purchase** to start the deployment

5. To check if the image has been created, on the Microsoft Azure Dashboard, click on the **Virtual machines**. You will now see the image created once the deployment succeeded.

   You should have these machines after creation:

   1 Stream Manager

   1 Origin

   1 Edge (with two instances)

    **SM, Origin, Edge VM:**
    ![]({{site.baseurl}}/assets/albset.JPG)

    **Edge instances:**
    ![]({{site.baseurl}}/assets/albedge.JPG)


**Note:** The machines are started after the deployment



### EMS Machine Components

When creating a machine with load balancer, three machines are actualy created. These are all included in the EMS template. The machines functions as follows:

**A. Stream Manager**

​	- Maintains a map of active Origin and Edges

​	- Detects ingest events at Origin to trigger stream replication at Edges

​		- Pulls streams to Edges when Origin ingests new streams

​		- Updates configuration when VM creation event detected

​		- Updates configuration when Server Started event detected

​		- Pings Origin & Edges regularly to update configuration

**B. Origin Server**

​	- Ingests streams from Source Clients

​	- Requests SM to replicate ingested streams to Edges

​	- Registers to NLM on VM creation

**C. Edge Server**

​	- Replicate (pull) streams ingested by Origin

​	- Register to NLM on VM creation

**D. Load Balancer**

​	- Distributes load among Edges

**E. Auto-Scaler**

​	- Automatically scales Edges based on bandwidth usage





### Connecting to EMS machine

All the virtual machines in your account is seen under the Virtual machines in the left-side menu bar. 

**Note:** All VMs are started after creation.

If your machine is turned off, manually start the set of VMs; SM, Origin, Edge in your resource group.

![]({{site.baseurl}}/assets/albstart.JPG)



To start anything for your project, what you need to access is the <u>Origin Server</u>. An EMS is installed in this server. From here, you can pull your streams and the Stream Manager will do the replication of the streams to the Edge Servers. The Edge Servers will be accessed by clients when a request is sent for streaming.



#### Connecting via SSH from Linux Terminal

1. Send command: 

   ``` 
   ssh <username>@<OriginServer_IPaddress>
   ```

   **Note:** The username and password is set in step 3 on the setup above.

   ``` 
   user@ubuntu:~/Desktop$ ssh user@11.221.105.202

   The authenticity of host '111.221.105.202 (111.221.105.202)' can't be established.
   RSA key fingerprint is ae:02:ee:41:ff:38:96:ab:78:7b:3a:e6:09:ed:1f:4c.
   Are you sure you want to continue connecting (yes/no)? 
   ```

2. Input “**yes**”, press **Enter**

   ``` 
   Warning: Permanently added '111.221.105.202' (RSA) to the list of known hosts.
   user@111.221.105.202's password:
   ```

3. Enter password, press **Enter**. A welcome note will open.

​	![]({{site.baseurl}}/assets/loggedin.JPG)

**Note:** The license is already installed and is placed in `/etc/evostreamms` for Linux.





#### Connecting  via SSH from Windows (PuTTy)

**Pre-requisites:**

- PuTTY Secure Shell Client



1. Run **PuTTY**

2. Select **Session** under the category tree

   ![]({{site.baseurl}}/assets/image16.png)

   ​

3. Specify the destination you want to connect to:

   ![]({{site.baseurl}}/assets/putty.JPG)

   ​

   **Host Name** – the username and public IP address of the <u>Origin Server</u>

   **Port** – 22 (default)

   **Connection type** – SSH

   ​

4. Click **Open**

5. Click  **Yes** to accept the security key on the PuTTy Security Alert Window

6. Enter the username's password, hit **Enter**

   ``` 
   Using username "EvoStream".
   EvoStream@111.221.105.202's password: 
   ```

7. You are now connected to the machine! 

   **Note:** The license is already installed and is placed in `/etc/evostreamms` for Linux.


## Load Balancing

Azure Load Balancer delivers high availability and network performance to EMS Edge servers. It distributes outbound traffic among healthy instances of Edge servers defined in a load-balanced scale set.


## Terminating EMS machine

### Stopping EMS machine

When you want to stop the virtual machine, fret not, all the changes remains in the server. The machine is only in suspended.

1. Click on the Virtual Machine Server menu
2. Right click on the virtual machine name, click on **Stop**
3. or, simply click **Stop** on the virtual machine window
4. Confirm stopping the virtual machine by clicking **Yes**

​	![]({{site.baseurl}}/assets/albstop.JPG)	



**Notes:** 

- There is no Stop function for Edge Server and its instances. 
- If the machine is stopped, the IP address of the machine will change on start.



### Deleting EMS machine

Deleting the EMS virtual machine will remove all the changes and the virtual machine itself in the Azure Virtual Machine list. 

1. Click on the Virtual machine menu
2. Right click on the virtual machine name, click on **Delete**
3. or, simply click **Delete** on the virtual machine window
4. Choose if you want to delete or keep the attached disk

​	![]({{site.baseurl}}/assets/albdelete.jpg)



**Notes:** 

- For Edge, you need to stop the instances. Just go under the Instances menu and you will find all the running instances in your Edge Server.

​		![]({{site.baseurl}}/assets/albdeleteedge.JPG)	

- Another edge instance will be created when one is deleted. For the two initial edge only.
