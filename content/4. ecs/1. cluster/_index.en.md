---
date: 2020-03-28
title: "ECS Cluster"
weight: 31
---

{{% notice note %}}
An Amazon ECS cluster is a logical grouping of tasks or services. You will deploy DEMOGO-ECS cluster across multi-AZ for high availability. You will attach additional IAM policy for the next lab **5. Monitoring**. 
{{% /notice %}}

![ECS](/images/ecs/ecs_cluster.svg)

1. Create **DEMOGO-ECS** cluster
2. Attach CloudWatchLogsFullAccess to **ecsInstanceRole**