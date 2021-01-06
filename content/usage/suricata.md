---
title: "Suricata"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 10
---

![](../../images/suricata.png)

## Description
Suricata is a free and open source, mature, fast and robust network threat detection engine.

The Suricata engine is capable of real time intrusion detection (IDS), inline intrusion prevention (IPS), network security monitoring (NSM) and offline pcap processing.

## Purpose
Suricata allows users of DetectionLab to test and develop IDS signatures in addition to using it for PCAP analysis. 

## Configuration Details
* Suricata is configured to monitor both the eth0 and eth1 network interfaces
* Traffic from the Windows hosts destined for the internet **does not** transit through logger, so you will unfortunately be blind to that traffic.
* The suricata configuration is in `/etc/suricata/suricata.yml`
* The emergingthreat "Open" and PTResearch "AttackDetection" rulesets are installed by default via `suricata-update`

## Data Location
* Splunk 
  * Alerts: `index=suricata`

## External Links
* https://suricata.readthedocs.io/en/suricata-6.0.1/
