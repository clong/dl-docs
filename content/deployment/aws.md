---
title: "AWS"
date: 2020-08-13T17:21:36-07:00
draft: false
weight: 5
---

### Prerequisites
* Terraform
* An AWS account
* An IAM user and role for Terraform
  * An AWS keypair for that user
* [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)

### Deployment
**Expected time to completion:** 25 minutes

By building DetectionLab in AWS, we can take advantage of the pre-built Windows AMIs that have already been completely provisioned. Here is what happens when `terraform apply` is called:

1. A VPC is created
2. A subnet is created
3. An internet gateway is created to give our subnet access to the outside world
4. A security group is created to allow inbound traffic from whitelisted IP addresses. These IP addresses are configured in the `terraform.tfvars` file you create in step 4 below.
5. The logger host is fully provisioned from an Ubuntu base AMI. 
6. The Windows host are pre-provisioned and are spun up from an AMI. No provisioning is necessary.
7. Instances can then be accessed via RDP, SSH, and via your browser.

{{% notice tip %}}
Please remember that keeping your instances online for long periods of time will rack up your AWS bill. Don't forget to **terraform destroy** your instances once you're done using it!
{{% /notice %}}


### Deployment Instructions
1. Clone the DetectionLab repo to your filesystem: `git clone https://github.com/clong/DetectionLab.git`
1. In your AWS console, create and apply [this policy](https://gist.github.com/clong/5eae6a83e6484bb2c01fa5e9cc6e8c9d) to the IAM user whose keypair you will be using for terraform. This policy has been tailored to only use the required permissions needed for DetectionLab.
1. [Configure the AWS command line utility](https://docs.aws.amazon.com/polly/latest/dg/setup-aws-cli.html) and set up a profile for Terraform via `aws configure --profile terraform`.
1. Create a private/public keypair to use to SSH into logger: `ssh-keygen -b 4096 -f ~/.ssh/id_logger`
1. Copy the file at `DetectionLab/AWS/Terraform/terraform.tfvars.example` to `/DetectionLab/AWS/Terraform/terraform.tfvars`
1. In `terraform.tfvars` (the file you just copied), provide overrides for the variables specified in [variables.tf](./variables.tf). 
{{% notice info %}}
AMIs are currently only available in us-west-1 and us-east-1 due to storage costs. If you'd like to bring up DetectionLab in another region, please view [deploying DetectionLab in a different AWS region.](../../customization/differentawsregion/)
{{% /notice %}}
{{% notice warning %}}
Failing to complete this step will cause the lab to be unreachable.
{{% /notice %}}
1. From the `DetectionLab/AWS/Terraform` directory, run `terraform init` to setup the initial Terraform configuration
1. Run `terraform apply` to begin the provisioning process

### Quickstart Video
A sample video of the setup process can be viewed here: 
[![DetectionLab - Terraform](https://i.vimeocdn.com/video/777172792_640.webp)](https://vimeo.com/331695321)

### Building your own AMIs
For more information about creating your own AMIs (as opposed to using the pre-built ones), please read this wiki page: [Terraform: Building Your Own AMIs](https://github.com/clong/DetectionLab/wiki/Terraform:-Building-Your-Own-AMIs)