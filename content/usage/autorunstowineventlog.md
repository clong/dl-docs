---
title: "AutorunsToWinEventLog"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 3
---

![](../../images/autorunstowineventlog.png)

---

## Purpose
Log all of the items enumerated by Sysinternals' Autoruns to the Windows Event Log for easy analysis/searching

## Configuration Details
* Runs once a day 
* Triggered by a scheduled task named "AutorunsToWinEventLog"

## Data Location
* Splunk
  * `index=wineventlog source=WinEventLog:Autoruns`

## External Links
* https://github.com/palantir/windows-event-forwarding/tree/master/AutorunsToWinEventLog