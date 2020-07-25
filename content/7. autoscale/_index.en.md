---
title: "Auto Scaling"
weight: 50
pre: "<b>6. </b>"
---

{{% notice note %}}
As you experienced in **5. Container Monitoring**, Amazon ECS publishes CloudWatch metrics with your **service**’s average CPU and memory usage. You can use these and other CloudWatch metrics to **automatically adjusts** capacity to maintain steady, predictable performance at the lowest possible cost. With **ECS Cluster Auto Scaling**, your ECS clusters running on EC2 can automatically scale as needed to meet the resource demands of all tasks and services in your cluster. You will learn how those two kinds of auto scaling work. 
{{% /notice %}}

## Amazon ECS Service Auto Scale
![ServiceAutoScale](/images/autoscale/service_auto_scale.svg)
You can use CloudWatch metrics and others to scale out your service (**add more tasks**) to deal with high demand at peak times, and to scale in your service (**run fewer tasks**) to reduce costs during periods of low utilization. 

## Amazon ECS Cluster Auto Scale
![ClusterAutoScale](/images/autoscale/cluster_auto_scale.svg) 
With **ECS Cluster Auto Scaling**, your ECS clusters running on EC2 can automatically scale as needed to meet the resource demands of all tasks and services in your cluster.

ECS Cluster Auto Scaling uses **ECS Capacity Provider** construct to manage **Amazon EC2 Auto Scaling Groups (ASG)** on your behalf. You can configure the Capacity Provider to enable managed scaling of the ASG, reserve excess capacity in the ASG, and also to manage termination of instances in the ASG. 

 > Previously, ECS did not have the ability to directly manage the scaling of ASG. Instead, you had to set up scaling policies on your ASG manually outside of ECS, and the metrics available for scaling did not account for the desired task count, only the tasks already running. 

 
