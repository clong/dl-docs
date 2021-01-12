---
title: "Atomic Red Team"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 2
---

![](../../images/invoke-atomicredteam.png)

## Description
Atomic Red Team allows every security team to test their controls by executing simple "atomic tests" that exercise the same techniques used by adversaries (all mapped to Mitre's ATT&CK).

## Purpose
The purpose of Atomic Red Team in DetectionLab is to allow the user to simulate TTPs and observe the resulting telemetry or create new detections.

## Configuration Details
* Installed from `install-redteam.ps1`
* The `Invoke-AtomicRedTeam` execution framework

## Sample Usage

Import Powershell module and atomics-path:
```bash
Import-Module "C:\Tools\AtomicRedTeam\invoke-atomicredteam\Invoke-AtomicRedTeam.psd1" -Force
$PSDefaultParameterValues = @{"Invoke-AtomicTest:PathToAtomicsFolder"="C:\Tools\AtomicRedTeam\atomics"}
```

Run E.g. technique T1218.010 (Signed Binary Proxy Execution: Regsvr32):
```bash
Invoke-AtomicTest T1218.010 -TestNumbers 1,2
```

Run all techniques:
```bash
Invoke-AtomicTest All
```

More here: https://github.com/redcanaryco/invoke-atomicredteam/wiki/Execute-Atomic-Tests-(Local)

## Data Location
This tools and test are located in **C:\Tools\AtomicRedTeam\\**

This tool/application does not generate logs

## External Links
* https://github.com/redcanaryco/atomic-red-team
* https://github.com/redcanaryco/invoke-atomicredteam