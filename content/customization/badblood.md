---
title: "Use BadBlood to Add Random Users and Groups to Active Directory"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 5
---

DetectionLab comes pre-loaded with a bunch of tools, one of which is called [BadBlood](https://github.com/davidprowe/BadBlood)

If you'd like to populate active directory with a bunch of randomized users and groups, simply do the following:

1. Open a Powershell console with Administrator rights on the DC host, then run:
```
cd c:\Tools\BadBlood\BadBlood-master
.\Invoke-BadBlood.ps1
```
It will prompt you for confirmation, then begin adding hundreds of random users and groups.
