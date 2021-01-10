---
title: "Sysmon"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 11
---

![](../../images/sysmon.png)

## Description
System Monitor (Sysmon) is a Windows system service and device driver which, once installed on a system, remains resident across system reboots to monitor and log system activity to the Windows event log. It provides detailed information about process creations, network connections, and changes to file creation time. 

## Purpose
Sysmon is used to monitor process creations, network connections and other events of interest in DetectionLab.

## Configuration Details
* Olaf Hartong's [Sysmon Modular](https://github.com/olafhartong/sysmon-modular) is used at the primary Sysmon configuration
* Sysmon is installed as a service on the Windows hosts

## Data Location
* Splunk
  * `index=sysmon`

## External Links
* https://github.com/olafhartong/sysmon-modular
* https://www.blackhillsinfosec.com/getting-started-with-sysmon/
