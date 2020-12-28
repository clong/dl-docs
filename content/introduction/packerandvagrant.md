---
title: "Understanding Packer & Vagrant"
date: 2020-08-13T14:41:31-07:00
draft: false
weight: 3
---

![Packer](https://www.packer.io/img/logo-hashicorp.svg?width=400)
![Vagrant](https://www.vagrantup.com/img/logo-hashicorp.svg?width=400)

To better understand the technology behind this project, it's important to understand the role that [Packer](https://www.packer.io/) and [Vagrant](https://www.vagrantup.com/) have.

A good way to think about this is to consider what would be required to build a lab like this without any automation. The steps would look something like this:
1. Obtain ISOs for Ubuntu, Windows Server 2016, and Windows 10
2. Using Virtualbox or VMware, install the operating systems onto the VMs
3. Once the operating systems have been installed, tailor a few operating settings to your liking
4. Take a snapshot of each VM once you've tweaked the settings
5. Now that a snapshot has been created, begin installing software on each VM. In the case of Detection Lab, this includes Splunk, Active Directory Domain Services, Windows Event Forwarding, and much more.
6. Join each host to the domain and ensure networking is correctly configured.

Obviously this process is extremely time consuming and tedious to repeat. Packer and Vagrant help automate the steps of this process. 

### Packer

At a high level, **Packer** is responsible for taking an operating system ISO and JSON configuration file as input, and generating a "Box" as output. 
This "Box" is essentially a compressed version of a Virtual Machine. Packer allows you to automate the installation of the operating system and can make configuration changes to the operating system as well.

![Packer](https://github.com/clong/DetectionLab/blob/master/img/packer_wiki.png?raw=true)

With DetectionLab, the boxes are pre-built and [hosted on vagrantcloud.com](https://app.vagrantup.com/detectionlab). There is no requirement for you to create these boxes unless you'd like to customize or change them.

### Vagrant

The simplest way to think about Vagrant is to think of it as a command line client for Virtualbox and VMware.
In the same way that Docker uses Dockerfiles, Vagrant uses Vagrantfiles. Vagrantfiles contain information about 
virtual machines, such as which operating system to use, the CPU/memory specifications, networking options, and also
any scripts or commands that the VM should execute. 

In the same way that you can use Docker to pull down containers, you can use Vagrant to pull down entire VMs. 

## Vagrant
Once Packer has completed creating a Box, **Vagrant** is able to use it to further provision (or install software) on the operating system. 
In the case of Detection Lab, this means installing Splunk, Active Directory, Windows Event Forwarding, Security Tooling, and much more.

![Vagrant](https://github.com/clong/DetectionLab/blob/master/img/vagrant_wiki.png?raw=true)
