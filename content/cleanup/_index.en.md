---
title: "Clean Up"
weight: 100
pre: "<b>8. </b>"
---

1.	Move to [ECS](https://console.aws.amazon.com/ecs) Clusters and delete **DEMOGO-ECS** cluster.

2.	Move to [ECS](https://console.aws.amazon.com/ecs) Task Definitions and click each **catsdef** and **dogsdef**. Select all and click **Actions**, **deregister**.
![CleanUp1](../../static/images/cleanup/cleanup_1.png)
3.	Move to [ECR](https://console.aws.amazon.com/ecr) Repositories and delete **cats** and **dogs**
![CleanUp2](../../static/images/cleanup/cleanup_2.png)
4.	Move to [EC2](https://console.aws.amazon.com/ec2) Load Balancer and delete **demogo-alb.**

5.	Delete target group **web**, **cats** and **dogs.**
![CleanUp3](../../static/images/cleanup/cleanup_3.png)
6.	Move to [IAM](https://console.aws.amazon.com/iam) role and filter **ecs-demogo** and delete. 
![CleanUp4](../../static/images/cleanup/cleanup_4.png)
7.	Move to [CloudFormation](https://console.aws.amazon.com/cloudformation) and delete **ecs-demogo** stack. 
![CleanUp5](../../static/images/cleanup/cleanup_5.png)
8.	Select all resources that are failing to delete, if you have any. 
![CleanUp6](../../static/images/cleanup/cleanup_6.png)
9.	Move to [VPC](https://console.aws.amazon.com/vpc) and delete **DemoGoECSVPC** manually. 
![Cleanup7](../../static/images/cleanup/cleanup_7.png)
10.	Move to [CloudWatch](https://console.aws.amazon.com/cloudwatch) Log groups and delete **/aws/ecs/containerinsights/DEMOGO-ECS/performance**, **ecs-demogo-log** and **firelens-container**.
![CleanUp8](../../static/images/cleanup/cleanup_8.png)
