---
title: "Installing the Boss of the SOC (BOTS) Datasets"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 5
---

DetectionLab includes scripts to install the Splunk BOTSv2 and BOTSv3 datasets and all of their recommended apps.

### Installation

From the logger host, simply run: 

BOTSv2: `chmod +x /vagrant/scripts/install-botsv2.sh && /vagrant/scripts/install-botsv2.sh` 

BOTSv3: `chmod +x /vagrant/scripts/install-botsv3.sh && /vagrant/scripts/install-botsv3.sh`

If for some reason those files aren't available, you can access them directly in Github: 
* [install-botsv2.sh](https://github.com/clong/DetectionLab/blob/master/Vagrant/scripts/install-botsv2.sh)
* [install-botsv3.sh](https://github.com/clong/DetectionLab/blob/master/Vagrant/scripts/install-botsv3.sh)

Once installed, you can query the data in Splunk with:
`index=botsv3 earliest=0` 

{{% notice tip %}}
I recommend bumping the RAM on logger to 8GB+ if you can. Life gets really bad when logger uses all of its 4GB of memory and starts paging to disk <i class="far fa-frown"></i>
{{% /notice %}}


### Further Reading
Read more about the BOTSv2 and BOTSv3 datasets here: https://github.com/splunk/securitydatasets 

A walkthrough of BOTSv3 is also available here: https://clo.ng/blog/bots-part1/