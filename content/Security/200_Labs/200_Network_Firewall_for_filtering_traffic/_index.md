---
title: "Level 200: Network Firewall for filtering traffic"
menutitle: "Network Firewall for filtering traffic"
date: 2021-06-01T14:16:08+08:00
chapter: false
weight: 3
hidden: false
---

**Last Updated:** June 2021

**Author:** Keith Rozario, Solutions Architect


## Introduction

This hands-on lab will guide you through how to configure an [AWS Network Firewall](https://aws.amazon.com/network-firewall/) to inspect, filter and log network traffic from an [Amazon Virtual Private Cloud](https://aws.amazon.com/vpc). You will use the AWS Management Console and AWS CloudFormation to guide you through how to deploy AWS Network Firewall. Skills learned will help you secure your workloads in alignment with the [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/).


## Prerequisites

- An [AWS account](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html) that you are able to use for testing.
- Permissions to create resources in CloudFormation, VPC, EC2, Systems Manager, AWS Network Firewall.
- Basic understanding of [Amazon Virtual Private Cloud](https://aws.amazon.com/vpc)

## Costs

- Cost of AWS Network Firewall is ~$0.395/hr or ~$285/month. It is recommended that you execute the final tear-down step once the lab is complete to avoid incurring additional charges.

## Steps:

{{% children  %}}
