---
title: "Basic Vagrant Usage"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 4
---

It's easiest to think of Vagrant as a command-line wrapper for interacting with Virtualbox and VMware.

{{% notice tip %}}
When running Vagrant commands, you must be in a directory containing a Vagrantfile or you will receive the following error: **A Vagrant environment or target machine is required to run this command.**
{{% /notice %}}

## Setting a default provider
If you happen to have both Virtualbox and VMware Workstation/Fusion installed, it may be helpful to set the [VAGRANT_DEFAULT_PROVIDER](https://www.vagrantup.com/docs/providers/default.html) environment variable to either **vmware_desktop** or **virtualbox**.

## Basic Vagrant Usage 
**All commands must be run from the "DetectionLab/Vagrant" folder**

* Bring up all Detection Lab hosts using Virtualbox: **vagrant up --provider=virtualbox**
* Bring up all Detection Lab hosts using VMware: **vagrant up --provider=vmware_desktop**
* Bring up a specific host: **vagrant up \<hostname\>**
* Restart a specific host: **vagrant reload \<hostname\>**
* Restart a specific host and re-run the provision process: **vagrant reload \<hostname\> --provision**
* Destroy a specific host: **vagrant destroy \<hostname\>**
* Destroy the entire Detection Lab environment: **vagrant destroy** (Adding -f forces it without a prompt)
* SSH into a host (only works with Logger): **vagrant ssh logger**
* Run a WinRM command on a host (only works with DC, WEF, and WIN10): **vagrant winrm --command hostname --shell powershell \<hostname\>**
* Check the status of each host: **vagrant status**
* Suspend the lab environment: **vagrant suspend**
* Resume the lab environment: **vagrant resume**
* Shutdown each host: **vagrant halt**

Feel free to test it out! Navigate to **DetectionLab/Vagrant** and run **vagrant status**. If this is a fresh repo, you should see:

```bash
$ vagrant status
Current machine states:

logger                    not created (vmware_desktop)
dc                        not created (vmware_desktop)
wef                       not created (vmware_desktop)
win10                     not created (vmware_desktop)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
```

