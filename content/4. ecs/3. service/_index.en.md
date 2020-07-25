---
title: "ECS Service"
weight: 40
---

{{% notice note %}}
Amazon ECS allows you to run and maintain a specified number of instances of a task definition simultaneously in an Amazon ECS cluster. This is called a **service.** If any of your tasks should fail or stop for any reason, the Amazon ECS service scheduler launches another instance of your task definition to replace it and maintain the desired count of tasks in the service depending on the scheduling strategy used. 
{{% /notice %}}

{{% notice note %}}
In addition to maintaining the desired count of tasks in your service, you can optionally run your service behind a **load balancer.** The load balancer distributes traffic across the tasks that are associated with the service.
{{% /notice %}}

In this lab, you will create 3 services referring task definitions that you created earlier. These services are associated with the **target groups** by **ALB path patterns.**

![ECSService](/images/ecs/service/ecs_service.svg)

- **web** target group - path pattern /
- **cats** target group - path pattern /cats
- **dogs** target group - path pattern /dogs