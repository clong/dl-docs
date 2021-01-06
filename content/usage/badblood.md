---
title: "BadBlood"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 4
---

![](../../images/badblood.png)

## Description

Fill an Active Directory domain with thousands of objects such as users, computers, OUs, etc.

## Purpose

Allow the user to quickly populate a domain without having to manually add users, computers, etc.

## Configuration Details

BadBlood has been modified in DetectionLab to create 500-1500 users down from the default of 1000-5000.
See [`Install-RedTeam.ps1`](https://github.com/clong/DetectionLab/blob/master/Vagrant/scripts/install-redteam.ps1) for more details.

## Data Location

This tool is located in C:\Tools.

## External Links
* https://github.com/davidprowe/BadBlood