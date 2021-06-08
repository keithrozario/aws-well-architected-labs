---
title: "Modify Stateful Firewall Rule Group"
date: 2021-06-03T14:47:09+08:00
chapter: false
weight: 3
pre: "<b>3. </b>"
---

Using the AWS Network Firewall, we will modify the stateful Rule Group to allow HTTPS traffic to a specific domain.

### 3.1 Modify the Stateful Rule Group

By default, the lab deploys a Stateful Rule Group with a rule that only allows the following domains **.amazonaws.com**, **.amazon.com**. In this step we will allow additional domains, by adding them to the allow list.

1. Open the VPC console at https://console.aws.amazon.com/vpc/
2. Click on Network *Firewall rule groups*
3. Select the *well-architected-labs-statelful-RG*
4. Click on *Edit Rules*
5. Click on *Add domains*
6. Enter the list of domains you wish to allow and click save

{{% notice note %}}
Indicate wildcard domains with an initial '.'. For example,.example.com matches example.com and matches all subdomains of example.com, such as abc.example.com and www.example.com. 
{{% /notice %}}

### 3.2 Test the rule

1. Open the AWS Console for Session Manager[https://console.aws.amazon.com/systems-manager/session-manager](https://console.aws.amazon.com/systems-manager/session-manager)
2. Click on Start Session
3. Select the instance name starting with the naming prefix you selected e.g.*well-architected-labs-instance* and click start session.
4. A terminal window should appear on screen.
5. From here, we can use the **curl** command to send HTTP traffic to the target domain e.g.

```
curl -I http://ec2-reachability.amazonaws.com/
```
6. We can test both HTTP and HTTPs domains, to test for **pass** and **allow** conditions.

![stateful_rules](/Security/200_Network_Firewall_for_filtering_traffic/Images/stateful_curl_test.png)

