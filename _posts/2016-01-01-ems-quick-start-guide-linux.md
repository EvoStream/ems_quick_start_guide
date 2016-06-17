---
title: Quick Start Guide for Linux
layout: post
date:   2016-01-01 00:00:00 +0000
categories: jekyll update
permalink: quick_start_guide_for_linux
---

## Purpose

This document provides instructions on how to install EvoStream Media Server (EMS) on Linux operating systems. It also provides instructions for some basic features of the EMS such as starting EMS, pulling, playing source streams and shutting down the EMS.





## Getting EvoStream Media Server

There are two options for installing the EMS: Linux archive or apt/yum installation.

### A.	(Depricated) Linux Archive Installation

1. Download the EMS tarball at the [Release 1.7.1 Archives](http://tarballs.evostream.com/release/4491/)
2. Extract the **.tar.gz** file to install the EMS at a directory of your choice.



### B.	APT/YUM Installation

#### Pre-requisites:

Administrative privileges are required. This can be accomplished in many ways.

``` 
$ sudo su –
```

If the sudo utility is available:

``` 
$ su –
```

**Note:**

The prompt changes from ' **$**' to ' **#**' when administrative privileges are enabled.



#### Installation Procedure:

1\. Retrieve the script used to install the EvoStream software repository and store it

- Debian based Linux distributions (Ubuntu or Debian)  
  
  ``` 
  # wget http://apt.evostream.com/installkeys.sh -O /tmp/installkeys.sh
  ```
  
- RedHat based Linux distributions (CentOS, Fedora, RHEL)  
  
  ``` 
  # curl http://yum.evostream.com/installkeys.sh -o /tmp/installkeys.sh
  ```

2\. Execute the script to install the EvoStream software repository  

``` 
# sh /tmp/installkeys.sh
```

If successful, the following message should be printed on the console:  

``` 
"EvoStream keys installed successfully"
```

At this stage, the EvoStream software repository is successfully installed and you can install packages from it.

The following steps are used to install the EvoStream Media Server, and can be repeated to update the EMS to the most recent release.

**Note:**

Steps 2 and 3 must be executed only once

3\. Install EvoStream Media Server.

- Debian based Linux distributions (Ubuntu or Debian)  
  
  ``` 
  # apt-get install evostream-mediaserver
  ```
  
- RedHat based Linux distributions (CentOS, Fedora, RHEL)  
  
  ``` 
  # yum install evostream-mediaserver
  ```





## License Installation

There are two options for installing the license file: manual or via Web UI.

### A.	Manual

Copy the License.lic to:

- If via Linux Archive: `../config`
- If via APT/YUM: `/etc/evostreamms/`



### B.	Via Web UI

1\. Run the EMS

- Linux Archive  
  
  ``` 
  $ cd [Path to EMS bin folder]
  $ ./run_daemon_ems.sh
  ```
  
- APT/YUM  
  
  ``` 
  # service evostreamms start
  # service evostreamms start_console
  ```

2\. Open the EMS Web UI by pointing your browser to [http://localhost:8888/EMS_Web_UI/index.php](http://localhost:8888/EMS_Web_UI/index.php)

   ![gsgfl1.jpg]({{site.baseurl}}/assets/qsgfl1.jpg)

3\. Click **INSTALL EMS LICENSE**

4\. Locate the license file, and enter the directory where license will be installed

5\. Click **Install License**

   ![qsgfl2.jpg]({{site.baseurl}}/assets/qsgfl2.jpg)

6\. A message for successful installation will be displayed

7\. Restart the EMS

   ![qsgfl3.jpg]({{site.baseurl}}/assets/qsgfl3.jpg)

**Tip:** A successful EMS startup will show GO! GO! GO! on the console.





## Connecting to Telnet

To use EMS, a telnet is needed for communication. User needs to enable the telnet client to be able to run the EMS API commands.

1\. Open a command prompt, and run telnet

- For ASCII telnet interface  
  
  ``` 
  $ telnet localhost 1112
  ```
  
- For ASCII CLI interface  
  
  ``` 
  $ telnet localhost 1222
  ```

A telnet localhost will be opened after pressing Enter key.

2\. For preliminary check, type:  

``` 
version
```

The result for ASCII CLI is shown below:

![qsgfl4.jpg]({{site.baseurl}}/assets/qsgfl4.jpg)





## Basic EMS API

### A.	Adding a Stream

The pullStream command is the simplest command to get an external stream.

Sample command:  

``` 
pullstream uri=rtmp://s2pchzxmtymn2k.cloudfront.net/cfx/st/mp4:sintel.mp4 localstreamname=test
```



### B.	Stream Playback

Pulled streams are automatically saved in EMS. To play the pulled stream, use a media player that supports the media format that was pulled.

EMS automatically converts the stream pulled in different protocols so no worries if you want to play the stream using an RTMP or RTSP protocol for example.

To play in media player:

1\. Go to Open Network Stream

2\. Enter the URL of the pulled stream  

``` 
rtsp://127.0.0.1:5544/test
rtmp://127.0.0.1/live/test
```

The EMS will fetch the pulled stream via localStreamName and playback will start once the file is found.

![qsgfl5.jpg]({{site.baseurl}}/assets/qsgfl5.jpg)

Please refer to **EMS User's Guide** and **EMS API Definitions** for more information.



### C.	Stopping the EMS server

If the user wants to shut down the EMS, just send the command:  

``` 
shutdownServer
```

The EMS will respond with a key:

![qsgfl6.jpg]({{site.baseurl}}/assets/qsgfl6.jpg)

Then send another shutdownserver command using the key:  

``` 
shutdownServer key=bVjvUo8HQ6VzDFJv
```

The EMS will shut down after sending the command.
