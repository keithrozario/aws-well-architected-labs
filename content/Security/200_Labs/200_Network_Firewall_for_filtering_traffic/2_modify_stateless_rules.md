---
title: "Modify Stateless Rule Group - Part 1"
date: 2021-06-03T14:47:09+08:00
chapter: false
weight: 2
pre: "<b>2. </b>"
---

Using the AWS Network Firewall, we will now modify the stateless Rule Group to allow ICMP network traffic to/from a specific IP address.

### 2.1 Select an IP

1. Visit [EC2 reachability Test](http://ec2-reachability.amazonaws.com/), and select an ip for the region you're deployed in. This will be our *target ip address*.

### 2.2 Modify Stateless RuleGroup to allow ICMP traffic

The lab deploys a Stateless Rule Group with a rule that blocks all ICMP traffic. In this step we will create a higher priority rules, one that allows ICMP traffic to our *target ip address*.

1. Open the VPC console at https://console.aws.amazon.com/vpc/
2. Click on Network *Firewall rule groups*
3. Select the *well-architected-labs-stateless-RG*
4. Click on *Edit Rules*
5. Click on *Add Rule*
6. Enter a rule with the following parameters
    * Priority = **1**
    * Protocol = **ICMP**
    * Source = **Any IPv4 address**
    * Destination = **Custom**
        * target ip address expressed in CIDR format (e.g. **3.80.0.0/32**)
    * Action = **Pass**
7. Click on *Add*
8. Click on *Save*

Your rulegroup should now display the following:

![stateless_rules](/Security/200_Network_Firewall_for_filtering_traffic/Images/stateless_rule_group_1.png)

### 2.3 Testing the rule

1. Open the AWS Console for Session Manager[https://console.aws.amazon.com/systems-manager/session-manager](https://console.aws.amazon.com/systems-manager/session-manager)
2. Click on Start Session
3. Select the instance name starting with the naming prefix you selected e.g.*well-architected-labs-instance* and click start session.
4. A terminal window should appear on screen.
5. From here, we can use the **ping** command to send ICMP traffic to the *target ip address*

![stateless_ping_test](/Security/200_Network_Firewall_for_filtering_traffic/Images/stateless_ping_test_fail.png)

{{% notice note %}}
The test has failed, even though we have allowed traffic from our VPC to the *target ip address*. Before proceeding to the next step (where we fix the issue), can you guess we couldn't successful *receive* a response from our target.
{{% /notice %}}