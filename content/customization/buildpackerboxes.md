---
title: "Building Your Own Packer Boxes"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 5
---

If you find yourself wanting to customize the Packer boxes or don't trust running VMs downloaded from VagrantCloud, you have the ability to build them from scratch.

By using this method, you will be building the Vagrant boxes yourself using Packer. This method will take ~1 hour to build the boxes and another ~90-120 minutes to provision them for a total of **2-3 hours**.


### Steps
1. `cd` to the `DetectionLab/Packer` directory and build the Windows 10 and Windows Server 2016 boxes using the commands below. Each build will take about 1 hour. You can run these commands in parallel in separate terminal windows:

```text
$ cd DetectionLab/Packer
$ packer build --only=[vmware|virtualbox]-iso windows_10.json
$ packer build --only=[vmware|virtualbox]-iso windows_2016.json
```

1. Once both boxes have built successfully, move the resulting boxes (.box files) from the Packer folder to the Boxes folder:

    `cd DetectionLab/Packer && mv *.box ../Boxes`

1. **cd** into the `DetectionLab/Vagrant` directory and edit **Vagrantfile**. Change the lines 

`cfg.vm.box = "detectionlab/win2016"` 

`cfg.vm.box = "detectionlab/win10` 

to

`cfg.vm.box = "../Boxes/windows_2016_<provider>.box"` 

`cfg.vm.box = "../Boxes/windows_10_<provider>.box"` 

respectively. 

**\<provider\>** should be either "virtualbox" or "vmware".

Now when you run **vagrant up**, vagrant will use these locally created boxes instead of downloading them from VagrantCloud.