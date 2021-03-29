---
title: "Splunk"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 10
---

![](../../images/splunk.png)

## Description
Splunk is a software platform to search, analyze and visualize the machine-generated data gathered from the websites, applications, sensors, devices etc. which make up your IT infrastructure and business.

## Purpose
In DetectionLab, Splunk is used to centralize the data, logs, and telemetry from other software and operating systems. Splunk can be used to query data, make dashboards, and create alerts.

Replacing Splunk with ELK is a common request for DetectionLab, but since I strongly prefer Splunk I will not be replacing it. If you'd like to use ELK with DetectionLab, please check out the fork maintained by CyberDefenders here: https://github.com/cyberdefenders/DetectionLabELK

## Configuration Details
* Splunk is installed on Logger via [`logger_bootstrap.sh`](https://github.com/clong/DetectionLab/blob/master/Vagrant/logger_bootstrap.sh) along with a handful of apps to make it more useful. 
* A Splunk forwarder is installed on the WEF host to send all of the Windows Event Logs to Splunk. 
  * See [Install-SplunkUF](https://github.com/clong/DetectionLab/blob/master/Vagrant/scripts/install-splunkuf.ps1) for more details

The current Splunk indexes can be found on the [Lab Information and Credentials](../../introduction/infoandcreds/) page.

## Data Location
Splunk can be accessed at https://<logger>:8000

## External Links
* https://www.splunk.com/en_us/training/free-courses/splunk-fundamentals-1.html

