---
title: "Service Check"
weight: 48
---


1. Check status of each service in **DEMOGO-ECS** is **ACTIVE** and each has **two** of **running tasks.**
![ServiceCheck](/images/ecs/check/service_check.png)

1. Go to **Tasks** tab and check each task's status is **RUNNING.** What **Container instance** each service is running on. You can see **dogs** services do not have **Container instance** information because it uses **FARGATE.**
![MixedServiceCheck](/images/ecs/check/service_check_1.png) 


1. Move to [Amazon EC2 Load Balancers.](https://ap-northeast-2.console.aws.amazon.com/ec2/v2/home?region=ap-northeast-2#LoadBalancers:) Copy DNS name of **demogo-alb** **DNS Name** and paste to your web browser. It leads you to **web** having default path.
![ALBDNS](/images/ecs/check/service_check_2.png)

![WebMain](/images/intro/web.svg)

4. Click **I♥Cats** and **I♥Dogs.** Amazing friends are waiting for you!  
![catsdogs](/images/intro/catsdogs_jj.svg)

{{% notice note %}}
Congratulation! You just created simple containerized application on Amazon ECS **WITHOUT** deploying a single server to configure, manage, patch, or reboot!
{{% /notice %}}
 