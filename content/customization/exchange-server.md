---
title: "Adding an Exchange Server to DetectionLab"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 5
---

Due to the [recent vulnerabilities in Microsoft Exchange](https://msrc-blog.microsoft.com/2021/03/05/microsoft-exchange-server-vulnerabilities-mitigations-march-2021/), I have decided to add an optional Exchange server to the DetectionLab build. Exchange is complicated to install, takes a long time, and is quite resource intensive, therefore it's not an ideal candidate for DetectionLab. However, I think it's important that defenders have quick and easy access to an Exchange environment to better understand the impact of these vulnerabilities. Here's how you can add the Exchange server to your DetectionLab deployment:

## AWS
This feature has unfortunately been deprecated due to the difficulty and instability with creating the AWS AMI.

---

## VMware and Virtualbox
{{% notice warning %}}
Installing Exchange on Vagrant is still under development and isn't working reliably yet.
{{% /notice %}}

1. Create the lab normally
2. cd into `DetectionLab/Vagrant/Exchange`
3. Run `vagrant up exchange`

--

## Azure
Implemented via Ansible

--

## ESXi
Still under testing and development.
