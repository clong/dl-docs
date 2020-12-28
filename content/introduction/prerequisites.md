---
title: "Prerequisites"
date: 2020-08-13T14:41:31-07:00
draft: false
weight: 2
---

The pre-requisities for deploying DetectionLab depend on which platform you are deploying it to.

#### Virtualbox

Deploy DetectionLab to your local machine as invidudial Virtualbox VMs.

* Windows, Linux, and MacOS are all supported
* 55GB+ of free disk space
* 16GB+ of RAM highly recommended
* Vagrant 2.2.9+
* Packer 1.6.0+ (only required if building your own boxes)
* Virtualbox 6.0+ (older versions may work but are not tested)

#### VMware Fusion/Workstation

Deploy DetectionLab to your local machine as invidudial VMware VMs.

* Windows, Linux, and MacOS are all supported
* VMware Fusion or Workstation (It must be registered, trials will not work)
* The [VMware Desktop Vagrant Plugin](https://www.vagrantup.com/vmware/#buy-now) (costs $79)
* The [Vagrant VMware Utility](https://www.vagrantup.com/docs/vmware/vagrant-vmware-utility.html) must be installed
* 55GB+ of free disk space
* 16GB+ of RAM highly recommended
* Vagrant 2.2.9+
* Packer 1.6.0+ (only required if building your own boxes)
* VMware Fusion 11+ or Workstation 15+ (older versions may work but are not tested)

#### AWS

Deploy DetectionLab to AWS as 4 separate EC2 instances.

* AWS Account
* Terraform v12
* awscli

#### Azure

Deploy DetectionLab to Azure account as 4 separate instances.

* Azure Subscription ($200 free compute credit upon signup!)
* Terraform v12
* [az](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest) (Azure commandline)
* Ansible

#### ESXi 

Deploy DetectionLab to an ESXi server.

* ESXi 6.x
  * 7.x is not currently supported
* Packer 1.6.0+
* Vagrant 2.2.9+
* Ansible
* Terraform v12

#### HyperV

* Windows 10 1809 or later 
* Windows Server 2019 
* Windows Hyper-V Server 2019 

#### LibVirt

* libvirt
* virt-manager
* QEMU+kvm
