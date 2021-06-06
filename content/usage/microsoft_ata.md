---
title: "Microsoft ATA"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 7
---

![](../../images/msata.png)

---

## Description
Advanced Threat Analytics (ATA) is an on-premises platform that helps protect your enterprise from multiple types of advanced targeted cyber attacks and insider threats.

## Purpose
Having Microsoft ATA allows defenders to test detections and gain a better sense of ATA's capabilities. It allows offensive security professionals to determine what tools and/or techniques will be detected by Microsoft ATA.

## Configuration Details
* Microsoft ATA is installed on the WEF host
* A lightweight gateway is installed on DC

## Sample Usage

To attempt a zone transfer:
From a cmd.exe prompt, run
```
C:\Users\vagrant>nslookup
Default Server:  UnKnown
Address:  192.168.38.102

> ls -d windomain.local
[UnKnown]
*** Can't list domain windomain.local: Query refused
The DNS server refused to transfer the zone windomain.local to your computer. If this
is incorrect, check the zone transfer security settings for windomain.local on the DNS
server at IP address 192.168.38.102.
```

To attempt to do a DCSync:
```
c:\tools\mimikatz\x64\mimikatz.exe
lsadump::dcsync /domain:windomain.local /user:krbtgt
```

Both of these activities should trigger MSATA alerts within a few minutes. 


## Data Location

## External Links
