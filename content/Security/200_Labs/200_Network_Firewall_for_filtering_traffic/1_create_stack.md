---
title: "Deploy Lab Based Environment"
date: 2021-06-03T14:47:09+08:00
chapter: false
weight: 1
pre: "<b>1. </b>"
---

Using AWS CloudFormation we are going to deploy:

- An AWS Network Firewall
- An Amazon VPC with:
    - A Network Firewall Endpoint 
    - An EC2 instance
    - An Internet Gateway
- A Cloudwatch Log Group

## VPC Architecture
![architecture_diagram](/Security/200_Network_Firewall_for_filtering_traffic/Images/lab_based_env.png)

- The EC2 instance is created for us to test the connectivity (pass/drop) of network traffic outbound to the internet
- The Network Firewall [VPC Endpoint](https://docs.aws.amazon.com/vpc/latest/privatelink/vpce-interface.html) is to allow our VPC to route traffic to the AWS Network Firewall
- [The Cloudwatch Log Group](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CloudWatchLogsConcepts.html) will serve as a destination for alerts from our AWS Network Firewall

## Deploying Cloudformation Stack

1. Download the latest version of the CloudFormation template here: [well_architected_lab_network_firewall.yml](/Security/200_Network_Firewall_for_filtering_traffic/Code/well_architected_lab_network_firewall.yml)

{{% common/CreateNewCloudFormationStack stackname="network-firewall" templatename="well_architected_lab_network_firewall.yaml" %}}
    * Under *NamingPrefix* specify a prefix for resources deployed by this stack (for easy identification), or leave as-is to use the default prefix of *well-architected-labs*
    * Under *LatestAmiId* you may leave as-is to use the latest Amazon Linux 2 AMI for our EC2 instance.
{{% /common/CreateNewCloudFormationStack %}}

## Checking deployment

To check if your deployments were successful:

1. Open the AWS Console for Session Manager[https://console.aws.amazon.com/systems-manager/session-manager](https://console.aws.amazon.com/systems-manager/session-manager)
2. Click on Start Session
3. Select the instance name starting with the naming prefix you selected e.g.*well-architected-labs-instance* and click start session.
4. A terminal window should appear on screen.

{{% notice note %}}
An SSH key is not configured in this lab, instead [AWS Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html) should be used to manage the EC2 instances as a more secure and scalable method.  
If you do not see your instance among the Target Instances list, wait 10 minutes after the cloud formation deployment is complete.
{{% /notice %}}

You have now set up the lab environment and are ready to proceed to the next step!
