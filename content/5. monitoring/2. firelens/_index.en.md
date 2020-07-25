---
title: "FireLens"
weight: 42
---

{{% notice note %}}
You attached **CloudWatchLogsFullAccess** policy to **ecsInstanceRole** role and enabled **FireLens** integration when you create **catsdef** for this chapter. 
{{% /notice %}}

{{% notice note %}}
FireLens works with Fluentd and Fluent Bit. AWS provide the AWS for Fluent Bit image or you can use your own Fluentd or Fluent Bit image. FireLens for Amazon ECS enables you to use task definition parameters to route logs to an AWS service or AWS Partner Network (APN) destination for log storage and analytics. In this lab, you will learn one of the simplest use cases: Firelens Fluent Bit and CloudWatch Logs. 
{{% /notice %}}

1)	Move to [CloudWatch Log groups.](https://ap-northeast-2.console.aws.amazon.com/cloudwatch/home?region=ap-northeast-2#logs:)
2)	Filter **ecs-demogo-log**
![FilterLogGroups](/images/monitoring/firelens_1.svg)
3)	Click **ecs-demogo-log** and navigate each log stream.
![LogStream](/images/monitoring/firelens_2.png)
4)	Expand each log to find more information. 
![DetailLogs](/images/monitoring/firelens_3.svg)
You can find information about container_id, ecs_cluster, etcs_task_definition and logs etc. 

