---
title: Quick Start Guide for Amazon Web Services - Windows
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: quick_start_guide_for_amazon_windows
---

## Purpose

This document describes how to install and configure EvoStream Media Server software for Windows on Amazon Elastic Compute Cloud (Amazon EC2), an Amazon web service that provides resizable compute capacity in the cloud.

Amazon EC2 is a cloud-computing platform that virtualizes computing resources as virtual machines. A single virtual machine configuration is registered as an Amazon Machine Image (AMI). EvoStream provides an Amazon Linux AMI with a preconfigured version of EvoStream Media Server that is ready to start using the Amazon Web Services (AWS) Management Console. You can use this AMI to launch EMS for EC2 instances, paying for your running instance time and bandwidth consumption only while the instances are running. You can launch EMS instances in specific geographical locations that are closer to your audience to reduce latency and in multiple geographical locations to provide high levels of redundancy.



## Getting Started

### Pre-requisites

- Amazon Web Services Account
- Amazon EC2 Console Account



### Free Trial

EMS offers a 30-day free trial use for first-time customers.

![]({{site.baseurl}}/assets/image12.png)

**Note:** There will be no software changes but the AWS infrastructure charges still apply.



### Deployment

To get started with the EvoStream Media Server (EMS) on Amazon EC2 you will first need to purchase an EMS instance through the Amazon Web Services website: [*https://aws.amazon.com/marketplace*](https://aws.amazon.com/marketplace)

1. Search for the EvoStream Media Server in the AWS marketplace, or simply follow this link: 
   
   [https://aws.amazon.com/marketplace/pp/B00VTR946Y](https://aws.amazon.com/marketplace/pp/B00VTR946Y)
   
   ![]({{site.baseurl}}/assets/image1.JPG)
   
2. Click **Continue** and **Sign in** your AWS account
   
   ![]({{site.baseurl}}/assets/image2.png)
   
3. Select what type of EMS instance you will run: *(1-Click Launch or Manual Launch)*


- **1-Click Launch**

![]({{site.baseurl}}/assets/image3.jpeg)

The setup for the instance is made easy by the Amazon 1-click Launch utility and the EMS can be successfully deployed with all of the default settings.

A.	Select the **Version** of the EMS to be used

![]({{site.baseurl}}/assets/image4.JPG)

B.	Select the **Region** and **EC2 Instance Type** (size of computer) for your deployment

![]({{site.baseurl}}/assets/region.jpg)

![]({{site.baseurl}}/assets/image5.JPG)



**Note:** The EMS can be run on very small computers, including Micro EC2 instances. The size of the instance should be a direct reflection of how much sustained traffic you expect to be hosting. In almost all scenarios you will run out of bandwidth prior to exhausting the CPU or memory limits of the virtual machine.

C.	Select or create the **VPC** and **Subnet** to be used.

![]({{site.baseurl}}/assets/image6.JPG)



**Note:** See [http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Introduction.html](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Introduction.html) for more information on VPC.

D.	Choose a **Security Group**

![]({{site.baseurl}}/assets/image7.JPG)

The default security group has been designed to provide outside access to all ports used for streaming. The ports are defined and used as follows:

| **Port** | **Use**                                  |
| -------- | ---------------------------------------- |
| 1112     | Telnet for API (JSON)                    |
| 1113     | (Internal use only)                      |
| 1222     | Telnet for API (ASCII)                   |
| 1935     | RTMP                                     |
| 1936     | (Internal use only)                      |
| 22       | SSH                                      |
| 3389     | RDP                                      |
| 4443     | RTMP                                     |
| 5000     | (Reserved)                               |
| 5544     | RTSP                                     |
| 5985     | (Reserved)                               |
| 6666     | Live FLV                                 |
| 7777     | HTTP for API                             |
| 8080     | HTTP Requests                            |
| 8100     | JSON META                                |
| 8210     | WS JSON META                             |
| 8410     | WS FMP4                                  |
| 8888     | HTTP for EWS (EvoStream Web Server)      |
| 9999     | MPEG TS                                  |


These Security Settings can be changed but it will impact the accessibility of the streams on your server.

E.	Choose or create a **Key Pair**

![]({{site.baseurl}}/assets/image8.JPG)

Either choose an existing key pair for instance access or create a new one for your account. If you choose an existing pair you **MUST** have the .pem file already downloaded from that pair. Amazon does not allow you to download key pairs a second time.

F.	Review the settings created, click on **Launch with 1-Click**

![]({{site.baseurl}}/assets/image9.jpeg)




* **Manual Launch**

![]({{site.baseurl}}/assets/image10.jpeg)

**Step 1: Choose AMI**

A.	Select the **EMS version** to be used

![]({{site.baseurl}}/assets/image11.JPG)

B.	Click the **Launch with EC2 Console** of the chosen **Region**

![]({{site.baseurl}}/assets/region_man.JPG)



**Step 2: Choose Instance Type**

You will now be redirected to the **Launch Instance Wizard in Step 2**. You may launch or with continue the configuration of the image.

C.	Select the **Instance Type** to be used. You may **Review and Launch** the AMI or click **Next** to continue with the configuration

![]({{site.baseurl}}/assets/instancetype.JPG)



**Step 3: Configure Instance Details**

D.	Configure the instance to suit your requirements. You may **Review and Launch** the AMI or click **Next** to continue with the configuration

![]({{site.baseurl}}/assets/instance.JPG)



**Step 4: Add Storage**

E.	**Add New Volume** or you may **Review and Launch** the AMI or click **Next** to continue with the configuration

![]({{site.baseurl}}/assets/volume.JPG)



F.	Add a tag for the instance or you may **Review and Launch** the AMI or click **Next** to continue with the configuration

![]({{site.baseurl}}/assets/tag.JPG)



G.	**Create** or **select** the **security group** to be used then click **Review and Launch**

![]({{site.baseurl}}/assets/securitygroup.JPG)



**Step 7: Review and Launch**

H.	Review the configuration made, click **Launch** or go back to modify the changes

![]({{site.baseurl}}/assets/review.JPG)



I.	A window for the keys will prompt. Select an existing key pair or create or proceed without the key pair to be used. Click **Launch instances**

![]({{site.baseurl}}/assets/keypair.jpg)



Note: You will find the instance created in Instances under Instances Menu




## Connecting to EMS using Windows

### A.	Remote Desktop Connection

1. Run the **Remote Desktop Application**
   
2. Enter the details of the virtual machine image, click **Connect**
   
   **Computer** - the IP address of the image
   
   **Username** -Administrator
   
   **Password**- *see below*
   
   2.1.	How to obtain the password?
   
   To get the password, right click on the instance under the Instances list. Click **Connect** and you will be prompted with this:
   
   ![]({{site.baseurl}}/assets/password.jpg)
   
   
   Click on **Get Password**. Choose the **[key-pair-name\].pem** then click **Decrypt Password**. 
   
   A **password** will be shown on the window.
   
   ![]({{site.baseurl}}/assets/decrypt.JPG)
   

   
3. Enter the **password** for the user, click **OK**
   
4. The connection will be established.Run EMS by double clicking the desktop shortcut icon or running the `run_console_ems.bat`. You can now use the EMS capabilities!

**Note:** The EMS is installed in `C:\EvoStream`.



### B.	EMS Web UI

While most work with the EMS happens at the command line or through the HTTP based API calls, the EMS does have a Web UI that can be used. To access the UI simply point your browser at the proper URL: `http://<DomainOrPublicIP>:8888/EMS_Web_UI/index.php`

**< DomainOrPublicIP >** will need to be replaced with the Public Domain or Public IP of your new EC2 Instance.

**Note:** EMS should be running to be able to access the EMS Web UI.



#### B.1.	Determining Public IP

1. Sign in to *https://console.aws.amazon.com*
   
2. Click on the **EC2** under compute
   
   ![]({{site.baseurl}}/assets/image23.jpeg)
   
3. In the Navigation pane of the EC2 Management Console, under Instances, click **Instances**.
   
4. Select the running instance.
   
5. In the lower pane, click the **Description tab**. The Public DNS value is the public domain name of your running instance and the Instance ID is the instances instance ID.
   
   ![]({{site.baseurl}}/assets/image13.jpeg)



#### B.2.	Login for Web UI

The Web UI is protected by default when using the EMS on AWS.  When accessing the Web UI you will be prompted for a username and password.

![]({{site.baseurl}}/assets/authentication.JPG)

* Username: evostream
* Password: "Amazon Instance ID" - this will need to be obtained via your Amazon account.



**Getting the Amazon Instance ID**

- **From Amazon Console**


1. Sign in to *https://console.aws.amazon.com*
   
2. Click on the **EC2** under compute
   
   ![]({{site.baseurl}}/assets/image23.jpeg)
   
3. Click on **Running Instances** under Resources
   
   ![]({{site.baseurl}}/assets/image24.jpeg)
   
4. Click on the **Instance Name** provided for the EMS, and look for the **Instance ID** given.  This will be your password.

![]({{site.baseurl}}/assets/image25.jpeg)



## HTTP Based API

The above instructions gave you access to the EMS via the command line.  For integration with the EMS at the software level, using the HTTP Based API is often much more useful.  The full set of API's available to you are found here: [API Definition](http://docs.evostream.com/ems_api_definition/table_of_contents)

For the EMS on AWS, the HTTP based API is exposed, but it requires authentication to be used.  We call this **Proxy Authentication**. Basic Authentication is used and so just a username and password are required:

* Username: evostream
* Password: "Amazon Instance ID" - this will need to be obtained via your Amazon account as explained above.

Command will take this general format:

``` 
http://Username:Password@IPAddress:Port/apiproxy/CommandName?params=<base64EncodedString>
```

**Sample Command:** 

``` 
http://evostream:i-013c03dc9bab9d69f@52.91.237.115:8888/apiproxy/version
```

**Note:** username is “**evostream**” and password is the “**instance ID**”

See [http://docs.evostream.com/ems_user_guide/runtimeapi#http](http://docs.evostream.com/ems_user_guide/runtimeapi#http) for more details.





## EC2 Instance Termination

When you terminate an instance, you'll lose all changes or files that you have on the server. If you have anything that you don't want to lose, be sure to save it to Amazon Simple Storage Service (Amazon S3) before terminating the instance or you'll lose your data.

After you've saved your data, do the following to terminate an instance:

1. In the Navigation pane, under Instances, click **Instances**.
2. Select the running instance(s) that you want to terminate.
3. Click the **Actions** button, and then click **Terminate**. The Instance State column for the selected instance(s) will show shutting-down and then terminated.

**Note:** Amazon recommends that you confirm the machine reaches the terminated state before signing out. Charges will continue to accrue for instances that fail to shut down.
