---
title: "Adding an Exchange Server to DetectionLab"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 5
---

This page is still in progress and unfininshed. 

Due to the [recent vulnerabilities in Microsoft Exchange](https://msrc-blog.microsoft.com/2021/03/05/microsoft-exchange-server-vulnerabilities-mitigations-march-2021/), I have decided to add an optional Exchange server to the DetectionLab build. Exchange is complicated to install, takes a long time, and is quite resource intensive, therefore it's not an ideal candidate for DetectionLab. However, I think it's important that defenders have quick and easy access to an Exchange environment to better understand the impact of these vulnerabilities. Here's how you can add the Exchange server to your DetectionLab deployment:

## ESXi
1. In the `ESXi/terraform.tfvars` file that you should have already created, add a line with the following content: `create_exchange_server = true`. This overrides the default `false` value from `variables.tf`
2. Follow the instructions for the ESXi deployment up until step 8.
3. At step 8, uncomment out the exchange values inside of `inventory.yml` and fill in the IP address for the exchange host.

