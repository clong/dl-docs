---
title: "osquery"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 8
---

![](../../images/osquery.png)

## Description
osquery is an operating system instrumentation framework for Windows, OS X (macOS), Linux, and FreeBSD. The tools make low-level operating system analytics and monitoring both performant and intuitive.

osquery exposes an operating system as a high-performance relational database. This allows you to write SQL queries to explore operating system data. With osquery, SQL tables represent abstract concepts such as running processes, loaded kernel modules, open network connections, browser plugins, hardware events or file hashes.

## Purpose
While many endpoint security agents collect ongoing and streaming data such as process creation and file modification, osquery allows you to take a "point in time" examination about the state of your devices which makes searching for anomolies and outliers more straightforward. Osquery is able to introspect into many areas in the operating system, and using JOINs allows you to gather quite a bit of context with a single query.

## Configuration Details
* In DetectionLab, osquery agents are enrolled into [Fleet](../fleet/). The queries and configurations for the osquery agent are supplied by Fleet over a TLS connection.
* The parameters for configuring this connection to Fleet are stored in `C:\Program Files\osquery\osquery.flags`.
* osquery runs as a service via the `osqueryd` service.

## Data Location
* Splunk 
  * Query results: `index=osquery`
  * INFO/WARN/ERROR logs: `index=osquery-status`

## External Links
* https://osquery.io
* https://medium.com/palantir/osquery-across-the-enterprise-3c3c9d13ec55