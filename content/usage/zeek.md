---
title: "Zeek"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 14
---

## Description
Zeek is a passive, open-source network traffic analyzer. It is primarily a security monitor that inspects all traffic on a link in depth for signs of suspicious activity. More generally, however, Zeek supports a wide range of traffic analysis tasks even outside of the security domain, including performance measurements and helping with trouble-shooting.

## Purpose
Zeek is meant to be a companion to Suricata in DetectionLab. Suricata excels at signature based detections and PCAP analysis while Zeek is excellent for connection logging, protocol analysis, and other monitoring and analysis tasks. 

## Configuration Details
* Zeek configuration is in `/opt/zeek`
* Zeek monitors both eth0 and eth1 interfaces by default

## Data Location
Splunk:
  * `index=zeek`

## External Links  
* https://docs.zeek.org/en/current/