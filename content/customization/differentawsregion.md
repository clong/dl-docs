---
title: "Deploying DetectionLab in a Different AWS Region"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 5
---

For cost reasons, DetectionLab AMIs are only currently hosted in us-west-1 and us-east-1. Each region I host AMIs in increases my monthly AWS bill. However, you are welcome to copy those public AMIs into your AWS account in any region you'd like. Here's how:

### Via the AWS Console
1. Log into AWS and select the EC2 service
2. Click "AMIs" on the left hand column and ensure you are currently either in us-west-1 or us-east-1
3. Change the filter from "Owned by me" to "Public Images"
4. Add the following filter: "Owner : 505638924199"
![](https://github.com/clong/DetectionLab/blob/master/img/ami_share_1.png?raw=true)
5. You should see 3 AMIs appear: detectionlab-dc, detectionlab-wef, detectionlab-win10
6. For each AMI (you have to do this one at a time), click on the box next to the AMI > Actions > Copy AMI. From here, you will be able to select which region to copy the AMI to. Do this for all three AMIs.
![](https://github.com/clong/DetectionLab/blob/master/img/ami_share_2.png?raw=true)
![](https://github.com/clong/DetectionLab/blob/master/img/ami_share_3.png?raw=true)
7. Switch to the target region you chose in step 6 and visit the AMIs panel. You should see 3 pending AMI transfers.
![](https://github.com/clong/DetectionLab/blob/master/img/ami_share_4.png?raw=true)
8. Edit `Terraform/variables.tfvars` and change the `dc_ami`, `wef_ami`, and `win10_ami` default values from empty string ("") to the AMI ID shown in your AWS console.