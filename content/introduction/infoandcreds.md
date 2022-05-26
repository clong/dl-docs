---
title: "Lab Information and Credentials"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 2
---

![Overview](https://github.com/clong/DetectionLab/blob/master/img/Overview.png?raw=true&width=1200)

* **Domain Name:** windomain.local
* **Admininstrator login:** vagrant:vagrant
* **Fleet login:** https://192.168.56.105:8412 - admin@detectionlab.network:admin123#
* **Splunk login:** https://192.168.56.105:8000 - admin:changeme
* **MS ATA login:** https://192.168.56.103 - wef\vagrant:vagrant
* **Guacamole login:** http://192.168.56.105:8080/guacamole - vagrant:vagrant
* **Velociraptor login:** https://192.168.56.105:9999 - admin:changeme

## Lab Hosts
* **DC - Windows 2016 Domain Controller**
  * WEF Server Configuration GPO
  * Powershell logging GPO
  * Enhanced Windows Auditing policy GPO
  * Sysmon
  * Velociraptor
  * osquery
  * Splunk Universal Forwarder (Forwards Sysmon & osquery)
  * Sysinternals Tools
  * Microsft Advanced Threat Analytics Lightweight Gateway
* **WEF - Windows 2016 Server**
  * Microsoft Advanced Threat Analytics
  * Windows Event Collector
  * Windows Event Subscription Creation
  * Powershell transcription logging share
  * Sysmon
  * Velociraptor
  * osquery
  * Splunk Universal Forwarder (Forwards WinEventLog & Powershell & Sysmon & osquery)
  * Sysinternals tools
* **Win10 - Windows 10 Workstation**
  * Simulates employee workstation
  * Sysmon
  * Velociraptor
  * osquery
  * Splunk Universal Forwarder (Forwards Sysmon & osquery)
  * Sysinternals Tools
* **Logger - Ubuntu 16.04**
  * Splunk Enterprise
  * Fleet osquery Manager
  * Zeek
  * Suricata
  * Guacamole
  * Velociraptor server

## Splunk Indexes
Index Name | Description
-----------|------------
evtx_attack_samples | Samples from https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES
osquery | osquery/Fleet result logs
osquery-status | osquery/fleet INFO/WARN/ERROR logs
powershell | Powershell transcription logs
suricata | Suricata IDS logs
sysmon | Logs from the Sysmon service
threathunting | Used for the ThreatHunting app
wineventlog | Windows Event Logs
zeek | Zeek network traffic logs

## Installed Tools on Windows
  * Sysmon
  * Velociraptor Agent
  * osquery
  * AutorunsToWinEventLog
  * Process Monitor
  * Process Explorer
  * PsExec
  * TCPView
  * Notepad++
  * Google Chrome
  * WinRar
  * Mimikatz
  * Wireshark
  * Powersploit
  * Atomic Red Team
  * BadBlood

## Applied GPOs
* [Custom Event Channel Permissions](https://rawgit.com/clong/DetectionLab/master/Vagrant/resources/GPO/reports/Custom%20Event%20Channel%20Permissions.htm)
* [Default Domain Controllers Policy](https://rawgit.com/clong/DetectionLab/master/Vagrant/resources/GPO/reports/Default%20Domain%20Controllers%20Policy.htm)
* [Default Domain Policy](https://rawgit.com/clong/DetectionLab/master/Vagrant/resources/GPO/reports/Default%20Domain%20Policy.htm)
* [Domain Controllers Enhanced Auditing Policy](https://rawgit.com/clong/DetectionLab/master/Vagrant/resources/GPO/reports/Domain%20Controllers%20Enhanced%20Auditing%20Policy.htm)
* [Powershell Logging](https://rawgit.com/clong/DetectionLab/master/Vagrant/resources/GPO/reports/Powershell%20Logging.htm)
* [Servers Enhanced Auditing Policy](https://rawgit.com/clong/DetectionLab/master/Vagrant/resources/GPO/reports/Servers%20Enhanced%20Auditing%20Policy.htm)
* [Windows Event Forwarding Server](https://rawgit.com/clong/DetectionLab/master/Vagrant/resources/GPO/reports/Windows%20Event%20Forwarding%20Server.htm)
* [Workstations Enhanced Auditing Policy](https://rawgit.com/clong/DetectionLab/master/Vagrant/resources/GPO/reports/Workstations%20Enhanced%20Auditing%20Policy.htm)