---
title: "Windows: Virtualbox & VMware"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 3
---

### Supported Provisioners
* Virualbox
* A licensed copy of VMware Workstation
  * The [VMWare Desktop Vagrant plugin](https://www.vagrantup.com/vmware/#buy-now) is $79 and is required to use Vagrant with VMware. 
  * Install it with `vagrant plugin install vagrant-vmware-desktop`.
  * License it with `vagrant plugin license vagrant-vmware-desktop <path_to_.lic>`.
  * Additionally, the [Vagrant VMware Utility](https://www.vagrantup.com/docs/vmware/vagrant-vmware-utility.html) must also be installed

{{% notice warning %}}
If you have both Virtualbox and VMware installed, consider disabling the network adapters for the provider that you are not using. For example, if you want to build DetectionLab using Virtualbox, disable the VMware network adatpers (or vice-versa) to avoid a conflict. ![interfaces](../../images/interfaces.png)
{{% /notice %}}

### Instructions
1. Ensure the prerequisites listed above are installed and that you meet the [system requirements](http://detectionlab.network/introduction/prerequisites/)
2. Clone the DetectionLab repo to your filesystem: `git clone https://github.com/clong/DetectionLab.git`
3. Using a terminal, navigate to the **DetectionLab/Vagrant** repository and run **.\prepare.ps1** to verify that your system has all of the prerequisites installed:

![vagrantstatus](../../images/prepare_win.png)

At this point in time, we can bring up DetectionLab using the `vagrant up --provider=<provider>` command. The provider options are `virtualbox` or `vmware_desktop`.

When we run Vagrant up, here's what happens:
1. Vagrant will bring up one host at a time, starting with logger and followed by dc, wef, and win10. 
2. Three boxes will be downloaded from Vagrant cloud:
    * [bento/ubuntu18.04](https://app.vagrantup.com/bento/boxes/ubuntu-18.04)
    * [detectionlab/win2016](https://app.vagrantup.com/detectionlab/boxes/win2016)
    * [detectionlab/win10](https://app.vagrantup.com/detectionlab/boxes/win10)
3. Each box will go through provisioning, which configures the host and installs software. 

After running `vagrant up --provider=vmware_desktop` or `vagrant up --provider=virtualbox`, you should see something like this:

```text
PS C:\Users\build\DetectionLab\Vagrant> vagrant up --provider=virtualbox
Bringing machine 'logger' up with 'virtualbox' provider...
Bringing machine 'dc' up with 'virtualbox' provider...
Bringing machine 'wef' up with 'virtualbox' provider...
Bringing machine 'win10' up with 'virtualbox' provider...
==> logger: Importing base box 'bento/ubuntu-18.04'...
==> logger: Matching MAC address for NAT networking...
==> logger: Checking if box 'bento/ubuntu-18.04' version '202007.17.0' is up to date...
==> logger: Setting the name of the VM: logger
==> logger: Clearing any previously set network interfaces...
==> logger: Preparing network interfaces based on configuration...
    logger: Adapter 1: nat
    logger: Adapter 2: hostonly
==> logger: Forwarding ports...
    logger: 22 (guest) => 2222 (host) (adapter 1)
==> logger: Running 'pre-boot' VM customizations...
==> logger: Booting VM...
==> logger: Waiting for machine to boot. This may take a few minutes...
    logger: SSH address: 127.0.0.1:2222
    logger: SSH username: vagrant
    logger: SSH auth method: private key
    logger:
    logger: Vagrant insecure key detected. Vagrant will automatically replace
    logger: this with a newly generated keypair for better security.
    logger:
    logger: Inserting generated public key within guest...
    logger: Removing insecure key from the guest if it's present...
    logger: Key inserted! Disconnecting and reconnecting using new SSH key...
==> logger: Machine booted and ready!
==> logger: Checking for guest additions in VM...
==> logger: Setting hostname...
==> logger: Configuring and enabling network interfaces...
==> logger: Mounting shared folders...
    logger: /vagrant => C:/Users/user/DetectionLab/Vagrant
==> logger: Running provisioner: shell...
    logger: Running: C:/Users/build/AppData/Local/Temp/vagrant-shell20200813-3372-yqjhma.sh
    logger: [05:34:56]: Adding apt repositories...
    logger: Get:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
    logger: Hit:2 http://archive.ubuntu.com/ubuntu bionic InRelease
...
...
```

If all goes well, this process should continue for 1-2 hours depending on your computer and network speed. The boxes are very large, but only need to be downloaded once. 

Once provisoning is finished, you can access the VMs through the GUI or SSH/RDP to them directly. You can also verify services are accessible by running `.\post_build_checks.ps1`:

![vagrantstatus](../../images/post_build_win.png?width=600)


If for some reason you encounter an error or any issues, checkout the troubleshooting page linked below. If you can't find an answer to your question, please [open an issue](https://github.com/clong/DetectionLab/issues) on the DetectionLab GitHub!

### Troubleshooting
Visit the [troubleshooting](../troubleshooting/) page.