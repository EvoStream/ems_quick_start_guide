---
title: Quick Start Guide for Amazon Web Services
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: quick_start_guide_for_amazon
---

## Purpose

This document describes how to install and configure EvoStream Media Server software on Amazon Elastic Compute Cloud (Amazon EC2), an Amazon web service that provides resizable compute capacity in the cloud.

Amazon EC2 is a cloud-computing platform that virtualizes computing resources as virtual machines. A single virtual machine configuration is registered as an Amazon Machine Image (AMI). EvoStream provides an Amazon Linux AMI with a preconfigured version of EvoStream Media Server that is ready to start using the Amazon Web Services (AWS) Management Console. You can use this AMI to launch EMS for EC2 instances, paying for your running instance time and bandwidth consumption only while the instances are running. You can launch EMS instances in specific geographical locations that are closer to your audience to reduce latency and in multiple geographical locations to provide high levels of redundancy.



## Getting Started

### Pre-requisites

- Amazon Web Services Account
- Amazon EC2 Account
- Amazon EC2 Console Account



### Deployment

To get started with the EvoStream Media Server (EMS) on Amazon EC2 you will first need to purchase an EMS instance through the Amazon Web Services website: [*https://aws.amazon.com/marketplace*](https://aws.amazon.com/marketplace)

1. Search for the EvoStream Media Server in the AWS marketplace, or simply follow this link: 
   
   [https://aws.amazon.com/marketplace/pp/B00VTR946Y](https://aws.amazon.com/marketplace/pp/B00VTR946Y)
   
   ![]({{site.baseurl}}/assets/image1.jpeg)
   
2. Click **Continue** and **Sign in** your AWS account
   
   ![]({{site.baseurl}}/assets/image2.png)
   
3. Select what type of EMS instance you will run:
   
   #### 1-Click Launch

![]({{site.baseurl}}/assets/image3.jpeg)

The setup for the instance is made easy by the Amazon 1-click Launch utility and the EMS can be successfully deployed with all of the default settings.

A.	Select the **Version** of the EMS to be used

![]({{site.baseurl}}/assets/image4.jpeg)

B.	Select the **Region** and **EC2 Instance Type** (size of computer) for your deployment

![]({{site.baseurl}}/assets/image5.jpeg)

**Note:** The EMS can be run on very small computers, including Micro EC2 instances. The size of the instance should be a direct reflection of how much sustained traffic you expect to be hosting. In almost all scenarios you will run out of bandwidth prior to exhausting the CPU or memory limits of the virtual machine.

C.	Select or create the **VPC** to be used.

![]({{site.baseurl}}/assets/image6.jpeg)

**Note:** See [*http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC\_Introduction.html*](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Introduction.html) for more information on VPC.

D.	Choose a **Security Group**

![]({{site.baseurl}}/assets/image7.jpeg)

The default security group has been designed to provide outside access to all ports used for streaming. The ports are defined and used as follows:

| **Port** | **Use**                                  |
| -------- | ---------------------------------------- |
| 1935     | RTMP                                     |
| 1112     | Telnet to EMS                            |
| 8080     | HTTP Requests                            |
| 7777     | HTTP for API                             |
| 6666     | Live FLV                                 |
| 22       | SSH                                      |
| 8888     | HTTP - EvoStream Media Server Management |
| 5544     | RTSP                                     |

These Security Settings can be changed but it will impact the accessibility of the streams on your server.

E.	Choose or create a **Key Pair**

![]({{site.baseurl}}/assets/image8.jpeg)

Either choose an existing key pair for instance access or create a new one for your account. If you choose an existing pair you **MUST** have the .pem file already downloaded from that pair. Amazon does not allow you to download key pairs a second time.

F.	Review the settings created, click on **Launch with 1-Click**

![]({{site.baseurl}}/assets/image9.jpeg)



#### Manual Launch

![]({{site.baseurl}}/assets/image10.jpeg)

A.	Select the **EMS version** and click the **Launch with EC2 Console** of the chosen **Region**

![]({{site.baseurl}}/assets/image11.jpeg)

​

### Free Trial

EMS offers a 30-day free trial use for first-time customers.

![]({{site.baseurl}}/assets/image12.png)

**Note:** There will be no software changes but the AWS infrastructure charges still apply.



## EMS Web UI

While most work with the EMS happens at the command line or through the HTTP based API calls, the EMS does have a Web UI that can be used. To access the UI simply point your browser at the proper URL: `http://<DomainOrPublicIP>:8888/EMS_Web_UI/index.php`

< DomainOrPublicIP > will need to be replaced with the Public Domain or Public IP of your new EC2 Instance.



### Determining Public IP:

1. In the Navigation pane of the EC2 Management Console, under Instances, click **Instances**.
   
2. Select the running instance.
   
3. In the lower pane, click the **Description tab**. The Public DNS value is the public domain name of your running instance and the Instance ID is the instances instance ID.
   
   ![]({{site.baseurl}}/assets/image13.jpeg)



### Login for Web UI

The Web UI is protected by default when using the EMS on AWS.  When accessing the Web UI you will be prompted for a username and password.

* Username: evostream
* Password: "Amazon Instance ID" - this will need to be obtained via your Amazon account.



Getting the Amazon Instance ID

1. Sign in to [*https://aws.amazon.com/*](https://aws.amazon.com/)
   
2. Click on the **EC2** under compute
   
   ![]({{site.baseurl}}/assets/image23.jpeg)
   
3. Click on **Running Instances** under Resources
   
   ![]({{site.baseurl}}/assets/image24.jpeg)
   
4. Click on the **Instance Name** provided for the EMS, and look for the **Instance ID** given.  This will be your password.

![]({{site.baseurl}}/assets/image25.jpeg)



## Advanced Connection to the EMS

Connecting to the EMS via the command line unlocks a world of functionality not accessible through the UI.  You can read much more about the EMS API and its capabilities here:  [EMS User's Guide](http://docs.evostream.com/ems_user_guide/table_of_contents)

The following instructions will help you get connected via the command line to your new Amazon Marketplace instance.



### Connecting via SSH from Linux Terminal

Connecting to your new instance via SSH is exactly the same as connecting to any Linux EC2 computer. You will access it using the “ubuntu” user and use the .pem key you chose during Instance setup.

1. Locate the .pem (key file)
   
2. Send command: ssh –i ./&lt;evostream-keys.pem&gt; ubuntu@&lt;public\_IP&gt;
   
   **Note:** Public IP can be found on the Amazon instances
   
   ![]({{site.baseurl}}/assets/image13.jpeg)
   
   **Command:** 
   
   ``` 
   ssh -i ./evostream-keys.pem ubuntu@11.22.33.44.55
   ```
   
   **Output:**
   
   ``` 
   Welcome to Ubuntu 14.04.2 LTS (GNU/Linux 3.13.0-46-generic x86_64)
   
   	Documentation:  https://help.ubuntu.com/
    System information as of Wed Jan 20 09:11:53 UTC 2016
    System load:  0.0               Processes:           106
    Usage of /:   13.9% of 7.74GB   Users logged in:     1
    Memory usage: 2%                IP address for eth0: 11.22.33.44.55
    Swap usage:   0%
    Graph this data and manage this system at:
      https://landscape.canonical.com/
    Get cloud support with Ubuntu Advantage Cloud Guest:
      http://www.ubuntu.com/business/services/cloud
   ```
   
   ​

### Connecting via SSH from Windows (Putty)

#### Pre-requisites

- PuTTY Generator
- PuTTY Secure Shell Client



#### Key File Conversion

EvoStream Media Server configuration can be accomplished using SSH and a client. Public AMI instances use a public/private key pair to log in instead of a password. The public key half of this pair is embedded in your instance, allowing you to use the private key half to log in securely without a password.

On Windows® operating systems, you can open a secure session to your Amazon EC2 instance by using the PuTTY Secure Shell client, which you can download from:

[*http://www.chiark.greenend.org.uk/*](http://www.chiark.greenend.org.uk/)~sgtatham/putty/download.html

The first thing you’ll need to do is convert the private key. The PuTTY Secure Shell client doesn't natively support the private key format generated by Amazon EC2. Fortunately, PuTTY has a tool called PuTTYgen that you can use to convert your private key to the required PuTTY Private Key File (\*.ppk) format. To convert the \[key-pairname\].pem file that you created to a \[key-pair-name\].ppk file, do the following:

1. Run **PuTTY Key Generator**
   
2. Click **Load** button
   
   ![]({{site.baseurl}}/assets/image14.jpg)
   
3. Select and open the **.pem file** that you want to convert in the Load private key window.
   
   **Note:** You'll need to select the All Files option in the File filter drop-down list to see PEM files in the file list.
   
4. Click **OK** in the PuTTYgen Notice window
   
   ![]({{site.baseurl}}/assets/image15.png)
   
5. Click **Save private key** and save the file with the name **\[key-pair-name\].ppk**.

####  

#### To connect via SSH:

1. Run PuTTY
   
2. Select **Session** under the category tree
   
   ![]({{site.baseurl}}/assets/image16.png)
   
3. Specify the destination you want to connect to:
   
   ![]({{site.baseurl}}/assets/image17.png)
   
   **Host Name** – the public IP address in Amazon EC2 instance running EvoStream Media Server
   
   **Port** – 22 (default)
   
   **Connection type** – SSH
   
4. Select **Auth** under **Connection &gt; SSH** in category tree
   
5. Click the **Browse** button to find and open the **\[key-pair-name\].ppk** file
   
   ![]({{site.baseurl}}/assets/image18.jpg)

**Note:** If you will be opening this same session later, you can save it for future use.

***To save the session information:***

On the Basic options for your PuTTY Session page, enter a name for the session in Saved Sessions, and then click the **Save** button

![]({{site.baseurl}}/assets/image19.jpg)

1. Click on **SSH** under the Connection category
   
2. Click the **Open** button to open the secure SSH session. The first time you connect to your instance, you'll get a PuTTY Security Alert that references the first use of **\[key-pair-name\].pem**
   
3. Click **Yes** to accept the security key.
   
   ![]({{site.baseurl}}/assets/image20.png)

If you previously saved the SSH session information for this Amazon EC2 instance, do the following:

1. Run PuTTY
   
2. Select **Session** in the category tree
   
3. Select the Saved Session and then click the **Load** button
   
   ![]({{site.baseurl}}/assets/image21.jpg)
   
4. Click the **Open** button to open the secure SSH session.
   
   ![]({{site.baseurl}}/assets/image22.png)

**Note:** You should see the login as: prompt in the SSH client window. Enter the Username and to login to your Amazon EC2 instance.

To end your SSH session, enter the exit command or press **CTRL+D**. You may have to do this twice if you're logged-in as the root user.





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
http://evostream:i-48293048@52.91.237.115:8888/apiproxy/version
```

**Note:** username is “**evostream**” and password is the “**instance ID**”

See <http://docs.evostream.com/ems_user_guide/runtimeapi#http> for more details.





## EC2 Instance Termination

When you terminate an instance, you'll lose all changes or files that you have on the server. If you have anything that you don't want to lose, be sure to save it to Amazon Simple Storage Service (Amazon S3) before terminating the instance or you'll lose your data.

After you've saved your data, do the following to terminate an instance:

1. In the Navigation pane, under Instances, click **Instances**.
2. Select the running instance(s) that you want to terminate.
3. Click the **Actions** button, and then click **Terminate**. The Instance State column for the selected instance(s) will show shutting-down and then terminated.

**Note:** Amazon recommends that you confirm the machine reaches the terminated state before signing out. Charges will continue to accrue for instances that fail to shut down.