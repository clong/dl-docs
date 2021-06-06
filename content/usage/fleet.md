---
title: "Fleet"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 6
---

![](../../images/fleet.png)

---

## Description
Fleet is an open source osquery manager that allows you to remotely manage, query, and configure osquery across a multitude of devices.

## Purpose
Using Fleet in osquery allows people to make simple query or configuration changes using a nice WebUI instead of having to modify file contents across multiple hosts. 

## Configuration Details
* Fleet is installed on logger and can be controlled via `service fleet start/stop`
* [Palantir's osquery configuration](https://github.com/palantir/osquery-configuration) and queries come pre-configured in Fleet when using DetectionLab.

## Data Location
* Splunk 
  * Query results: `index=osquery`
  * INFO/WARN/ERROR logs: `index=osquery-status`

## External Links
* https://github.com/fleetdm/fleet