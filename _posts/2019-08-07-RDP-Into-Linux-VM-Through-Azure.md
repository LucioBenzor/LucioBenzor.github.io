---
layout: post
title: "RDP into a Linux VM through Azure"
date: 2019-08-07
---

Part of my job involves testing vulnerability scanners and running them through the paces before recommending them. In this endeavor,
I use a series of Azure VMs that I've domain-joined as a sandbox.

I've been wanting to test these scanners through a Linux Ubuntu VM and decided to boot one up in Azure and configure it to be able to employ 
Microsoft Remote Desktop to access it in the same way as my other VMs. By default Linux doesn't play well with Microsoft RDP and port 3389 is closed  


*note: Ubuntu server only has a command-line interface. Ubuntu 1604 LTS is the OS I choose and has a GUI.*  

# Set Up

* SSH into the VM. From the Azure portal, under connect, you'll have a choice of RDP or SSH. Copy the SSH command.
* Copy the SSH command into a command prompt window or powershell. You'll be prompted for the password of the Linux VM.
* If the connection is successful, you'll see <nameOfVM>@<nameOfVM>:~$
* run the following to install xfce:
  
```shell
sudo apt-get update
sudo apt-get install xfce4
```
* then run the following to install and enable xrdp, an rdp client for Linux:

```shell
sudo apt-get install xrdp
sudo enable xrdp
```

* Set the desktop environment for xrdp to use with the following:

```shell
echo xfce4-session >~/.xsession
```

* Then restart the service:

```shell
sudo service xrdp restart
```

* Create a network rule in the Azure GUI for the VM to allow RDP. Go to {NameOfVm} > Networking > Inbound port rules > Add inbound port rule

and create a rule with the following parameters:

| Security Option | Value         | 
| ------------- |:-------------:| 
| Source     | any |
| Source Port Ranges     | *      |  
| Destination | Any     |
| Destination Port Ranges | 3389
|Protocol | TCP
|Action | Allow
|Priority | 300
|Name | RDP rule

* Go back to the Linux VM and double-check the 3389 rule and the rdp by entering:

```shell
sudo netstat -ntlp | grep :3389
sudo netstat -plnt | grep rdp
```

* Go back to Azure and download the RDP file and run it to establish the connection!


**That's It!!**












