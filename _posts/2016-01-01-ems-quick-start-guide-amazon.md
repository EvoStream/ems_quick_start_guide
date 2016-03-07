---
title: Quick Start Guide for Amazon Marketplace
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: quick_start_guide_for_amazon
---

## Purpose

This document describes how to install and configure EvoStream Media Server™ software on Amazon Elastic Compute Cloud (Amazon EC2), an Amazon web service that provides resizable compute capacity in the cloud.

Amazon EC2 is a cloud-computing platform that virtualizes computing resources as virtual machines. A single virtual machine configuration is registered as an Amazon Machine Image (AMI). EvoStream provides an Amazon Linux AMI with a preconfigured version of EvoStream Media Server that is ready to start using the Amazon Web Services (AWS) Management Console. You can use this AMI to launch EMS for EC2 instances, paying for your running instance time and bandwidth consumption only while the instances are running. You can launch EMS instances in specific geographical locations that are closer to your audience to reduce latency and in multiple geographical locations to provide high levels of redundancy.





## What is EMS

EvoStream is an enterprise-strength media server capable of delivering your live and on-demand content to any screen with an unbeatable cost of ownership. With EvoStream, you can expand your audio/video/data delivery to all popular media platforms including HTML5, Adobe® Flash®, Apple® iOS devices, Android, VLC, QuickTime, IPTV, Microsoft® Silverlight®, and other 3GPP devices into a single workflow.



## How Does the EMS Work?

EvoStream Media Server runs as a separate application which you can send video and audio streams to. You can then connect to the EMS with a variety of players or other servers and use the Runtime API to push streams out or pull new streams in.



- **Stream Routing**
  
  EvoStream’s rich set of APIs includes **pull/push streaming**, which allows users to easily publish or consume RTMP/RTSP/HLS/MPEG-TS/etc streams to and from other locations such as a CDN or a service provider.

![](http://docs.evostream.com/ems_quick_start_guide/assets/intro2.png)

- **Stream Transformation**
  
  ![](http://docs.evostream.com/ems_quick_start_guide/assets/stream_transition.jpg)

Whether you want to publish RTMP from RTSP, HLS from MPEG-TS, or any other possible combination of streaming protocols, EvoStream truly unifies all streaming technologies into a single workflow.



## What can be connected to EMS?

EMS can be connected to anything that puts out a standard media stream. The EMS can ingest RTMP, RTSP/RTP, MPEG-TS, LiveFLV. The EMS can also be configured to ingest a feed directly from a hardware encoder chip (for embedded applications).

------

## Getting Started

### Deployment

To get started with the EvoStream Media Server (EMS) on Amazon EC2 you will first need to purchase an EMS instance through the Amazon Web Services website: https://aws.amazon.com/. 

1. Search for the EvoStream Media Server in the AWS marketplace, or simply follow this link: https://aws.amazon.com/marketplace/pp/B00VTR946Y
   
   ![](http://docs.evostream.com/ems_quick_start_guide/assets/amazon.jpg)
   
2. Click **Continue** and **Sign in** your AWS account
   
3. Select what type of EMS instance you will run:
   
   **1-Click Launch**
   
   ![](http://docs.evostream.com/ems_quick_start_guide/assets/aws_instance_1click.jpg)
   
   The setup for the instance is made easy by the Amazon 1-click Launch utility and the EMS can be successfully deployed with all of the default settings.
   
   A. Select the **Version** of the EMS to be used
   
   ![](http://docs.evostream.com/ems_quick_start_guide/assets/1click_version.jpg)
   
   ​
   
   B. Select the **Region** and **EC2 Instance Type** (size of computer) for your deployment
   
   ![](http://docs.evostream.com/ems_quick_start_guide/assets/1click_region_instance.jpg)
   
   ​
   
   **Note:** The EMS can be run on very small computers, including Micro EC2 instances. The size of the instance should be a direct reflection of how much sustained traffic you expect to be hosting. In almost all scenarios you will run out of bandwidth prior to exhausting the CPU or memory limits of the virtual machine.
   
   ​
   
   C. Select or create the **VPC** to be used.
   
   ![](http://docs.evostream.com/ems_quick_start_guide/assets/1click_vpc.jpg)
   
   ​
   
   **Note:** See http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Introduction.html for more information on VPC.
   
   ​
   
   D. Choose a **Security Group**
   
   ![](http://docs.evostream.com/ems_quick_start_guide/assets/1click_security.jpg)
   
   ​
   
   The default security group has been designed to provide outside access to all ports used for streaming. The ports are defined and used as follows:
   
   | Port | Use                                      |
   | :--: | :--------------------------------------- |
   | 1935 | RTMP                                     |
   | 1112 | Telnet  to EMS                           |
   | 8080 | HTTP Requests                            |
   | 7777 | HTTP for API                             |
   | 6666 | Live FLV                                 |
   |  22  | SSH                                      |
   | 8888 | HTTP -  EvoStream Media Server Management |
   | 5544 | RTSP                                     |
   
   These Security Settings can be changed but it will impact the accessibility of the streams on your server.
   
   ​
   
   E. Choose or create a **Key Pair**
   
   ![](http://docs.evostream.com/ems_quick_start_guide/assets/1click_keys.jpg)
   
   Either choose an existing key pair for instance access or create a new one for your account. If you choose an existing pair you MUST have the .pem file already downloaded from that pair. Amazon does not allow you to download key pairs a second time.
   
   ​
   
   F. Review the settings created, click on **Launch with 1-Click**
   
   ![](http://docs.evostream.com/ems_quick_start_guide/assets/aws_instance_1click_launch.jpg)
   
   **Manual Launch**
   
   ![](http://docs.evostream.com/ems_quick_start_guide/assets/aws_instance_manual.jpg)
   
   A. Select the EMS version and click the Launch with EC2 Console of the chosen Region
   
   ![](http://docs.evostream.com/ems_quick_start_guide/assets/manual_launch.jpg)
   
   ​



### Connect to the EMS

While most work with the EMS happens at the command line or through the HTTP based API calls, the EMS does have a Web UI that can be used. To access the UI simply point your browser at the proper URL: http://<DomainOrPublicIP>:8888/EMS_Web_UI/index.php

<DomainOrPublicIP> will need to be replaced with the Public Domain or Public IP of your new EC2 Instance. To get the public domain name and instance ID:

- In the Navigation pane of the EC2 Management Console, under Instances, click Instances.


- Select the running instance.


- In the lower pane, click the Description tab. The Public DNS value is the public domain name of your running instance and the Instance ID is the instances instance ID.



#### Connecting via SSH

Connecting to your new instance via SSH is exactly the same as connecting to any Linux EC2 computer. You will access it using the “ubuntu” user and use the .pem key you chose during Instance setup. For example:

ssh –i ./evostream-keys.pem ubuntu@1.2.3.4



#### Connecting via SSH from Windows (Putty)

EvoStream Media Server configuration can be accomplished using SSH and a client. Public AMI instances use a public/private key pair to log in instead of a password. The public key half of this pair is embedded in your instance, allowing you to use the private key half to log in securely without a password.

On Windows operating systems, you can open a secure session to your Amazon EC2 instance by using the PuTTY Secure Shell client, which you can download from:

http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html.

The first thing you’ll need to do is convert the private key. The PuTTY Secure Shell client doesn't natively support the private key format generated by Amazon EC2. Fortunately, PuTTY has a tool called PuTTYgen that you can use to convert your private key to the required PuTTY Private Key File (*.ppk) format. To convert the [key-pairname].pem file that you created to a [key-pair-name].ppk file, do the following:

1. Start PuTTYgen (Start > All Programs > PuTTY > PuTTYgen).
2. In the PuTTY Key Generator dialog box, click Load and select the [key-pairname].pem file that you want to convert. You'll need to select the All Files *.* option in the File filter drop-down list to see PEM files in the file list.
3. Click Save private key and save the file with the name [key-pair-name].ppk.

To connect via SSH:

1. Start PuTTY (Start > All Programs > PuTTY > PuTTY).
   
2. In the PuTTY Configuration dialog box, in the Category tree, select Session.
   
3. On the Basic options for your PuTTY session page, in Specify the destination you want to connect to:
   
   - In the Host Name (or IP address) field, enter [instance-public-dns], where [instance-public-dns] is the public domain name of your Amazon EC2 instance running EvoStream Media Server.
   - In the Port field, enter 22
   - Under Connection type, select the SSH option
   
4. In the Category tree, select Connection > SSH > Auth
   
5. On the Options controlling SSH authentication page, click the Browse button to find and open the [key-pair-name].ppk file.
   
   **Note:** If you will be opening this same session later, you can save it for future use. To save the session information:
   
   - Select Session in the Category tree
   - On the Basic options for your PuTTY session page, enter a name for the session in Saved Sessions, and then click the Save button
   - On the Options controlling SSH authentication page, click the Open button to open the secure SSH session. The first time you connect to your instance, you'll get a PuTTY Security Alert that references the first use of [key-pair-name]. Click Yes to accept the security key.
   
6. On the Options controlling SSH authentication page, click the Open button to open the secure SSH session. The first time you connect to your instance, you'll get a PuTTY Security Alert that references the first use of [key-pair-name]. Click Yes to accept the security key.
   
7. If you previously saved the SSH session information for this Amazon EC2 instance, do the following:
   
   - Start PuTTY (Start > All Programs > PuTTY > PuTTY).
   
   
   - In the PuTTY Configuration dialog box, in the Category tree, select Session.
   
   
   - On the Basic options for your PuTTY session page, in Load, save or delete a stored session, click the saved SSH session name and then click the Load button.
   
   
   - Click the Open button to open the secure SSH session.

**Note:** You should see the login as: prompt in the SSH client window. Enter the username ubuntu to login to your Amazon EC2 instance.

To end your SSH session, enter the exit command or press CTRL+D. You may have to do this twice if you're logged-in as the root user.



### EC2 Instance Termination

When you terminate an instance, you'll lose all changes or files that you have on the server. If you have anything that you don't want to lose, be sure to save it to Amazon Simple Storage Service (Amazon S3) before terminating the instance or you'll lose data.

After you've saved your data, do the following to terminate an instance:

- In the Navigation pane, under Instances, click Instances.


- Select the running instance(s) that you want to terminate.


- Click the Actions button, and then click Terminate. The Instance State column for the selected instance(s) will show shutting-down and then terminated.

**Note:** Amazon recommends that you confirm the machine reaches the terminated state before signing out. Charges will continue to accrue for instances that fail to shut down.