+++
title = "Introduction"
date = 2020-08-13T14:41:13-07:00
weight = 1
chapter = false
pre = "<i class='fas fa-asterisk'></i> "
+++

DetectionLab is a repository containing a variety of Packer, Vagrant, Powershell, Ansible, and Terraform scripts that allow you to automate
the process of bringing an ActiveDirectory environment online complete with logging and security tooling using a variety of different platforms. 

DetectionLab can currently be deployed to the following platforms:
* Virtualbox (Windows, MacOS, Linux)
* VMware Workstation/Fusion (Windows, MacOS, Linux)
* HyperV
* ESXi
* AWS
* Azure
* LibVirt (Not officially supported)
* Proxmox (Not officially supported)

DetectionLab was built with defenders in mind. Offensive security practitioners have entire Linux distributions dedicated to streamline
their work, so DetectionLab is my effort to simplify testing, analysis, research for defensive security practitioners. 

Read more about DetectionLab on Medium here: https://medium.com/@clong/introducing-detection-lab-61db34bed6ae

### Primary Lab Features
* Microsoft Advanced Threat Analytics (https://www.microsoft.com/en-us/cloud-platform/advanced-threat-analytics) is installed on the WEF machine, with the lightweight ATA gateway installed on the DC
* A Splunk forwarder is pre-installed and all indexes are pre-created. Technology add-ons are also preconfigured.
* A custom Windows auditing configuration is set via GPO to include command line process auditing and additional OS-level logging
* [Palantir's Windows Event Forwarding](http://github.com/palantir/windows-event-forwarding)  subscriptions and custom channels are implemented
* Powershell transcript logging is enabled. All logs are saved to `\\wef\pslogs`
* osquery comes installed on each host and is pre-configured to connect to a [Fleet](https://github.com/fleetdm/fleet) server via TLS. Fleet is preconfigured with the configuration from [Palantir's osquery Configuration](https://github.com/palantir/osquery-configuration)
* Sysmon is installed and configured using [Olaf Hartong's open-sourced Sysmon configuration](https://github.com/olafhartong/sysmon-modular)
* All autostart items are logged to Windows Event Logs via [AutorunsToWinEventLog](https://github.com/palantir/windows-event-forwarding/tree/master/AutorunsToWinEventLog)
* Zeek and Suricata are pre-configured to monitor and alert on network traffic
* Guacamole is installed to easily access all hosts from your local browser

![DetectionLab](../images/lab.png?width=1200)
