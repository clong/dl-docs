---
title: "Exchange Server"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 5
---

![](../../images/exchange.jpg?width=500)

## Description

A server running Microsoft Exchange can be added to DetectionLab. For more information, visit [Adding an Exchange Server to DetectionLab](../../customization/exchange-server/).

## Purpose

The original intent was to release this functionality shortly after the March 2021 [vulnerabilities outlined in this blog post](https://msrc-blog.microsoft.com/2021/03/05/microsoft-exchange-server-vulnerabilities-mitigations-march-2021/). However, it took much longer to implement this, so the purpose is simply to test detection and telemetry from Exchange. 

## Configuration Details

Credentials: 
* windomain\administrator : password

## Data Location

#### To log into the Exchange management shell:
1. Right click on **Exchange Management Shell** from the start menu and select "Run as a different user"
![](../../images/runas.png?width=400)
2. Use the credentials `windomain\administrator : vagrant`
![](../../images/runascreds.png?width=400)

To log into the actual exchange server:
1. Visit `https://exchange_server_ip/owa` in a browser. 
2. Use the credentials `windomain\adminstrator : vagrant` to login to the console.

![](../../images/exchangelogin.png)

If you get an error about "too many redirects" or a failed connection, try giving the Exchange server another 5-10 minutes to finish initializing. 

## External Links

