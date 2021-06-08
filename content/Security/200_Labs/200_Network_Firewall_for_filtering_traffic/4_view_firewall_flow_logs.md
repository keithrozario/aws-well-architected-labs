---
title: "View Firewall Flow Logs"
date: 2021-06-03T14:47:09+08:00
chapter: false
weight: 4
pre: "<b>4. </b>"
---

By default, the lab enables flow logging on the AWS Network Firewall, that logs data to a Cloudwatch log group. Flow logging captures all network flow from our firewall's stateful engine.

{{% notice note %}}
Flow logs do not capture the firewall's *stateless* engine, only those packets that are routed to the firewalls *stateful* engine.
{{% /notice %}}

### 3.1 View Logs in CloudWatch Logs Group

1. Open the Cloudwatch console at https://console.aws.amazon.com/cloudwatch/
2. Select the log group ending with *anf-log* (e.g. well-architected-labs-anf-log)
3. Select the top most Log Stream from the list
4. From here we can select events from our previous steps. To view granular data.
5. We can also filter the list of events by applying [filtering conditions](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/FilterAndPatternSyntax.html)

![cloudwatch_log_rules](/Security/200_Network_Firewall_for_filtering_traffic/Images/cloudwatch_log_groups.png)


