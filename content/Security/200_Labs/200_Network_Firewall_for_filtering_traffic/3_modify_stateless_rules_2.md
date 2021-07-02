---
title: "Modify Stateless Rule Group - Part 2"
date: 2021-06-03T14:47:09+08:00
chapter: false
weight: 3
pre: "<b>3. </b>"
---

In the previous step we modified the stateless rule group to allow ICMP traffic to our *target ip address*, but were unable successfully ping the target. This is because the stateless rule group allowed ICMP traffic **to** the target, but not the returning response **from** the target. Stateless rules need to be specified for both outgoing and incoming traffic.In this step we'll add a second rule to allow the returning response from our target ip address.

### 3.1 Modify Stateless RuleGroup to allow returning ICMP traffic

1. Open the VPC console at https://console.aws.amazon.com/vpc/
2. Click on Network *Firewall rule groups*
3. Select the *well-architected-labs-stateless-RG*
4. Click on *Edit Rules*
5. Click on *Add Rule*
6. Click on *Add Rule*
7. Enter a rule with the following parameters
    * Priority = **2**
    * Protocol = **ICMP**
    * Source = **Custom**
        * target ip address expressed in CIDR format (e.g. **3.80.0.0/32**)
    * Destination = **Any IPv4 address**
    * Action = **Pass**
8. Click on *Add*
9. Click on *Save*

Your rulegroup should now display the following:

![stateless_rules](/Security/200_Network_Firewall_for_filtering_traffic/Images/stateless_rule_group_2.png)

### 3.2 Testing the rule

1. Open the AWS Console for Session Manager[https://console.aws.amazon.com/systems-manager/session-manager](https://console.aws.amazon.com/systems-manager/session-manager)
2. Click on Start Session
3. Select the instance name starting with the naming prefix you selected e.g.*well-architected-labs-instance* and click start session.
4. A terminal window should appear on screen.
5. From here, we can use the **ping** command to send ICMP traffic to the *target ip address*
6. We can also test other ip addresses to ensure they're still being blocked

![stateless_ping_test](/Security/200_Network_Firewall_for_filtering_traffic/Images/stateless_ping_test_success.png)