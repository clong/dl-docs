---
title: "PurpleSharp"
date: 2020-03-28T23:23:36-07:00
draft: false
weight: 10
---

![](../../images/purplesharp.png)

## Description
PurpleSharp is an open source adversary simulation tool written in C# that executes adversary techniques within Windows Active Directory environments. The resulting telemetry can be leveraged to measure and improve the efficacy of a detection engineering program. PurpleSharp leverages the MITRE ATT&CK Framework and executes different techniques across the attack life cycle: execution, persistence, privilege escalation, credential access, lateral movement, etc

## Purpose
PurpleSharp enables DetectionLab users to easily simulate adversary techniques to generate attack telemetry with the goal of:

* Build new detection analytics
* Enhance existing detection analytics
* Validate detection resiliency

## Configuration Details
* The latest release of PurpleSharp is automatically downloaded by  [`install-redteam.ps1`](https://github.com/clong/DetectionLab/blob/master/Vagrant/scripts/install-redteam.ps1)
* No configuration is necessary, the binary is all you need to simulate attacks.

## Sample Usage

PurpleSharp supports several modes of simulation execution:
* Local: Execute techniques on a local host
* Remote: Execute techniques on a remote host
* Commandline: Execute techniques with command line parameters
* JSON: Execute techniques with a JSON file as input

A few examples below:

Execute 3 process injection techniques locally:
```bash
PurpleSharp.exe /t T1055.002,T1055.003,T1055.004
```

Execute the same process injection techniques on a remote host (network connectivity and administrative access required):
```bash
PurpleSharp.exe /rhost 192.168.1.1 /ruser admin /d lab.local /t T1055.002,T1055.003,T1055.004
```

Execute 3 simulation playbooks containing different techniques with a [JSON file](https://gist.github.com/mvelazc0/19ad02605ea8c6fe843b1b222a26b092) as input.
```bash
PurpleSharp.exe /pb variations.json
```

For more information and examples, visit the [documentation](https://purplesharp.readthedocs.io/) and look at the [demos](https://purplesharp.readthedocs.io/en/latest/demos/demos.html).

## Data Location
This tool is located in **C:\Tools\PurpleSharp\\**

Logs are generated in the same folder as PurpleSharp.exe

## External Links
* https://github.com/mvelazc0/PurpleSharp
* https://purplesharp.readthedocs.io/ 