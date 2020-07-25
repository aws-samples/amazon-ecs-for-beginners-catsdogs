---
title: "Monitoring"
weight: 40
pre: "<b>5. </b>"

---

{{% notice note %}}
Monitoring is an important part of maintaining the reliability, availability, and performance of Amazon ECS. You should collect monitoring data from all of the parts of your AWS solution so that you can more easily debug a multi-point failure if one occurs. 
{{% /notice %}}

![MonitoringOverview](/images/monitoring/monitoring.svg)

## Amazon CloudWatch Container Insights
CloudWatch Container Insights collects, aggregates, and summarizes metrics and logs from your containerized applications and microservices. The metrics include **utilization for resources** such as CPU, memory, disk, and network. The metrics are available in CloudWatch automatic dashboards.

## AWS FireLens
FireLens is a **container log router** for Amazon ECS and AWS Fargate that gives you extensibility to use the breadth of services at AWS or partner solutions for log analytics and storage. Find out [sample logging architectures for FireLens](https://github.com/aws-samples/amazon-ecs-firelens-examples) on Amazon ECS and AWS Fargate. In this lab, you will configure logging to CloudWatch Logs with FireLens Fluent Bit. 
