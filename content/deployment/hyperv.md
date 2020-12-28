---
title: "HyperV"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 10
---

### Intro

This page contains the instruction to build DetectionLab for HyperV. 
Hyper-V support for DetectionLab is a recent addition and requires more testing to ensure its stability and usability.  

A big thank you to [@man715](https://github.com/man715) for adding this in [PR #513](https://github.com/clong/DetectionLab/pull/513)

{{% notice info %}}
I do not officially support or troubleshoot DetectionLab issues using the HyperV provider. You're welcome to open issues for community support, but I will not personally be able to assist with them.
{{% /notice %}}

### Requirements 

The version of Hyper-V will need to be compatible with Hyper-V VM configuration version 9.0. 
You will need to be running one of the following operating systems: 
* Windows 10 1809 or later 
* Windows Server 2019 
* Windows Hyper-V Server 2019 

For a breakdown of what Operating Systems support which VM configuration versions please visit: (https://docs.microsoft.com/en-us/windows-server/virtualization/hyper-v/deploy/upgrade-virtual-machine-version-in-hyper-v-on-windows-or-windows-server) 
This build also requires vagrant-reload. If you do not have it installed, you will be prompted to install it.  

### Known Issues

Unfortunately, due to some issues with Vagrant and Microsoft, running DetectionLab with Hyper-V is not as easy as it is with other providers. You will need to do the following BEFORE trying to run `vagrant up`. 
1) Patch Vagant 
Vagrant does not play nice with Windows SMB share authentication. It uses cmdkey which is not properly implemented. More details about the issue can be found in this issue:(https://github.com/hashicorp/vagrant/issues/10661) 
To patch this, go find the mount_shared_folder.rb file and replace `"cmdkey /add:#{options[:smb_host]} /user:#{options[:smb_username]} /pass:\"#{options[:smb_password]}\""` with `"cmdkey '/add:\"#{options[:smb_host]}\"' '/user:\"#{options[:smb_username]}\"' '/pass:\"#{options[:smb_password]}\"'"` 

2) Windows will require you to enter an administrator username and password to be able to create and mount the SMB share. 
This means the build will not be fully automated. One thing you can do is add `config.vm.synced_folder '../Vagrant', '/vagrant', smb_username: "username", smb_password: "password"` to the Vagrantfile on line 2. For security reasons, this is not a good idea as you will be storing your username and password in plaintext. 
By not having this line added to the Vagrantfile you will be required to put in your username and password at least 2 times per machine.  

3) Selecting Virtual Switch 
During the build you will also have to select the virtual switch you want to use for each server. This cannot be avoided. There is a option that can be used to force the network adapter to use a particular switch; however, using that option breaks this build process.  

A really hacky workaround is, if you are using the smb_username and smb_password options, would be to press the option number corresponding with the virtual switch you want to use then enter four times after `vagrant up`. So, if you know you want the virtual switch 1 `vagrant up` 1 enter 1 enter 1 enter 1 enter 

Yes, I know hacky but it works.  

4) A workaround for logger losing network access/assigned IP or access to any of apps including splunk after a your first shutdown, would be to edit the /etc/netplan/01-netcfg.yaml on logger's machine and remove anything after renderer: networkd. Then reboot the VM.

To check if all your virtual machines have an IP assigned use the following powershell command: `Get-VMNetworkAdapter -VMName *`. See [Issue #525](https://github.com/clong/DetectionLab/issues/525) for more detail.

### How this build works 

The majority of this build works the same as the VirtualBox build. The most notable difference is on the Windows builds. There is a script that will create an internal virtual switch called "NATSwitch." Throughout the build process, a script will create a second network adapter and attach it to the NATSwitch on the VM being built. After the machine is built the original network adapter will be removed from the VM.  

## Note 

This build will run two scripts on the host machine. It is advisable to always check any scripts that will be run on your machine before running them. 
