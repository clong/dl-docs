---
title: "Troubleshooting & Known Issues"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 20
---

An unfortunate result of maintaining a project with so many moving parts is that it's prone to have issues. Although I do my best to keep everything working and run automated build tests once per week, sometimes issues slip through the cracks. 

Be sure to check the GitHub issues page for solved issues related to your problem: https://github.com/clong/DetectionLab/issues

Here are some strategies for resolving common problems:

---
**Issue:** You run into an error while provisioning a host

**Solution:** Each problem is different. Take a look at the error text and see if you can determine what the exact problem is based on the error message. Often times, running `vagrant reload <hostname> --provision` is enough to get things back on track. That command will simply restart the VM and start provisioning over again. If that doesn't work, try destroying the host via `vagrant destroy <hostname>` and then re-creating it using `vagrant up <hostname>`. If you continue to run into the same error, search [DetectionLab issues](https://github.com/issues). Finally, if you can't find a solution to your problem, please open a new issue!

---

**Issue:** You get stuck and want to start fresh

**Solution:** Navigate to **DetectionLab/Vagrant** and run `vagrant destroy -f` to force destroy all VMs. Afterwards, delete the `.vagrant` hidden folder inside of **DetectionLab/Vagrant** to ensure the VMs and their metadata have been properly removed. Optionally, delete and re-clone the entire DetectionLab git repo after those steps have been completed.

---

**Issue:** When RDP'ing to one of the Windows hosts, you see the following error message: 

> An authentication error has occurred. The function requested is not supported. This could be due to CredSSP encryption oracle remediation

![](../../images/rdp.png)

**Workarounds:**

From the host you are RDP'ing from, run gpedit.msc, and then browse to Computer Configuration > Administrative Templates > System > Credentials Delegation in the navigation pane. 
Change the **Encryption Oracle Remediation** policy to Enabled, and then change **Protection Level** to **Vulnerable**.

See this issue for more detail: https://github.com/clong/DetectionLab/issues/478

---

**Issue:** Splunk says "Your Splunk license has expired or you have exceeded your license too many times"

**Workarounds:**
1. Make some modifications to ingest less data 
2. Sign up for a free Splunk dev license which gives you 10GB/day ingest: https://dev.splunk.com/enterprise/dev_license/ and apply that license
3. Simply re-provision the logger host (no need to re-provision the windows hosts - they'll automatically reconnect):
   1. `vagrant destroy -f logger; vagrant up logger`

---

**Issue:** Vagrant reports: `Message: HTTPClient::KeepAliveDisconnected:` while provisioning.                     
**Workaround:** Run `$ vagrant reload <hostname> --provision`

---

**Issue:** `Vagrant timed out while attempting to connect via WinRM` after Win10 host joins the domain.                        
**Workaround** Documented in [#21](https://github.com/clong/detectionlab/issues/21). Just run `$ vagrant reload win10 --provision`

---

**Issue:** Vagrant is unable to forward a port for you.

**Workaround:** Documented in [#11](https://github.com/clong/detectionlab/issues/11). There are a few possibilities:
1. Try a `vagrant reload <hostname> --provision`. For whatever reason `vagrant up` doesn't fix conflicts but reload does.
2. Check if something is legitimately occupying the port via `sudo lsof -n -iTCP:<port_number>`
3. Follow the instructions from this comment: https://github.com/hashicorp/vagrant/issues/8130#issuecomment-272963103

---

**Issue:** Your primary hard drive doesn't have enough space for DetectionLab.

**Workaround:** Documented in [#48](https://github.com/clong/detectionlab/issues/48). You can change the default location for Vagrant by using the [VAGRANT_HOME](https://www.vagrantup.com/docs/other/environmental-variables.html#vagrant_home) environment variable.

---

**Issue:** You're having problems running Virtualbox while Hyper-V or CredentialGuard are enabled

**Workaround:** This is not a supported configuration. See https://stackoverflow.com/questions/37955942/vagrant-up-vboxmanage-exe-error-vt-x-is-not-available-verr-vmx-no-vmx-code and https://github.com/clong/DetectionLab/issues/433

---

**Issue:** You see an error message like `VBoxManage: error: Unknown option: --clipboard`

**Workaround:** This should be fixed in Virtualbox 6.1.4, but please see [this issue](https://github.com/clong/DetectionLab/issues/374#issuecomment-577920555) for details on how to fix this.