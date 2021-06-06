---
title: "Windows Event Forwarding"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 15
---

![](../../images/windowseventforwarding.png)

## Description
Windows Event Forwarding (WEF) is a powerful log forwarding solution integrated within modern versions of Microsoft Windows.

* Windows Event Forwarding allows for event logs to be sent, either via a push or pull mechanism, to one or more centralized Windows Event Collector (WEC) servers.
* WEF is agent-free, and relies on native components integrated into the operating system. WEF is supported for both workstation and server builds of Windows.

## Purpose
Instead of relying on third-party forwarders (e.g. Splunk, Beats), we can leverage native Windows components. Windows event forwarding subscriptions are XML documents that allow you to include or exclude events based on highly granular information. In DetectionLab, advanced Windows auditing is enabled and the WEF host is used as a Windows event collector. Windows endpoints pull event "subscriptions" from WEF, defining which events we want to collect. Once the events have been centralized on WEF, they are then sent to Splunk via a single Splunk forwarder.

## Configuration Details
* DetectionLab uses Palantir's Windows Event Forwarding configuration: https://github.com/palantir/windows-event-forwarding
* WEF is configured as the Windows Event Collector and Subscription Manager
* Subscriptions can be viewed using Event Viewer on the WEF host

## Data Location
Locally on WEF:
  * WEC1-WEC7 event channels under "Applications and Services" logs in Event Viewer
Splunk:
  * `index=wineventlog` and `index=sysmon`

## External Links
* https://github.com/palantir/windows-event-forwarding
* https://medium.com/@palantir/windows-event-forwarding-for-network-defense-cb208d5ff86f
* https://docs.microsoft.com/en-us/windows/security/threat-protection/use-windows-event-forwarding-to-assist-in-intrusion-detection
* https://hackernoon.com/the-windows-event-forwarding-survival-guide-2010db7a68c4
