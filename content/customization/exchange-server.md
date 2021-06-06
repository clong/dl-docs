---
title: "Adding an Exchange Server to DetectionLab"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 5
---

Due to the [recent vulnerabilities in Microsoft Exchange](https://msrc-blog.microsoft.com/2021/03/05/microsoft-exchange-server-vulnerabilities-mitigations-march-2021/), I have decided to add an optional Exchange server to the DetectionLab build. Exchange is complicated to install, takes a long time, and is quite resource intensive, therefore it's not an ideal candidate for DetectionLab. However, I think it's important that defenders have quick and easy access to an Exchange environment to better understand the impact of these vulnerabilities. Here's how you can add the Exchange server to your DetectionLab deployment:

## AWS
An AMI with Exchange pre-installed is provided. I have included the Exchange functionality as a Terraform module. You will have to make two minor changes to Terraform files to enable the provisioning of Exchange since it is disabled by default:

1. In `AWS/Terraform/exchange.tf`, remove the two block comment lines: `/*` and `*/` and save the file.

Diff: 
```diff

## Remove the block comment to enable the creation of the Exchange server
- /*
module "exchange" {
  source = "./modules/exchange"
  region = var.region
  subnet_id = aws_subnet.default.id
  security_group_id = [aws_security_group.windows.id]
  instance_name_prefix = var.instance_name_prefix
  custom-tags = var.custom-tags
  exchange_ami = var.exchange_ami
}
- */
```
2. In `AWS/Terraform/outputs.tf`, remove the leading line comments (`#`) on the exchange outputs:

Diff:
```diff
- #output "exchange_public_ip" {
- #  value = module.exchange.exchange_public_ip
- #}
+ output "exchange_public_ip" {
+   value = module.exchange.exchange_public_ip
+ }

- #output "exchange_url" {
- #  value = module.exchange.exchange_url
- #}
+ output "exchange_url" {
+   value = module.exchange.exchange_url
+ }
```

By making these changes, you "enable" the Exchange module and its associated outputs. To disable it, simply reverse the changes in those two files.

---

## VMware and Virtualbox
{{% notice warning %}}
Installing Exchange on Vagrant is still under development and isn't working reliably yet.
{{% /notice %}}

1. Create the lab normally
2. cd into `DetectionLab/Vagrant/Exchange`
3. Run `vagrant up exchange`

## Azure
Not yet implemented. The Ansible code needs to be improved.

## ESXi
Still under testing and development.
