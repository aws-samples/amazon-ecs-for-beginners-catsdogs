---
title: "Cluster Auto Scale"
weight: 52

---

{{% notice note %}}
You can configure the Capacity Provider to enable managed scaling of the ASG, reserve excess capacity in the ASG, and also to manage termination of instances in the ASG. 
{{% /notice %}}

Capacity Providers work with both EC2 and Fargate. With EC2, you can create a Capacity Provider associated with an EC2 Auto Scaling Group (ASG). The Capacity Provider can be used to manage scaling of the ASG through ECS Cluster Auto Scaling, ensuring that the capacity necessary to run your task is requested even if it is not yet available. When running tasks and services, you can split them across multiple Capacity Providers. In this lab, you will create EC2 Capacity Provider associated with an EC2 ASG and perform load test.

![ClusterAutoScale](../../../static/images/autoscale/cluster_auto_scale.svg)

## What you will do
1. [Create Capacity Provider](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/en/autoscale/cluster/capacityprovider/) 
2. [Configure Auto Scaling Group (ASG)](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/en/autoscale/cluster/asg/)
3. [Cluster Load Test](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/en/autoscale/cluster/loadtest/)
4. [Monitoring](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/en/autoscale/cluster/monitoring/)
