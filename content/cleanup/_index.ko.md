---
title: "실습 리소스 정리"
weight: 100
pre: "<b>8. </b>"
---
<p align="left">
1.	[Amazon ECS](https://console.aws.amazon.com/ecs) 클러스터로 이동하여 **DEMOGO-ECS** 클러스터를 삭제합니다.

2.	[Amazon ECS](https://console.aws.amazon.com/ecs) Task Definitions으로 이동하여 **catsdef**와 **dogsdef**를 각각 클릭하여 모두 선택한 후 **Actions**를 눌러 **deregister**를 클릭합니다.
![CleanUp1](/images/cleanup/cleanup_1.png)
3.	[Amazon ECR](https://console.aws.amazon.com/ecr) Repositories로 이동하여 **cats**와 **dogs**를 삭제합니다.
![CleanUp2](/images/cleanup/cleanup_2.png)
4.	[Amazon EC2](https://console.aws.amazon.com/ec2) Load Balancer로 이동하여 **demogo-alb**를 삭제합니다.

5.	타겟 그룹에서 **web**, **cats**, **dogs**를 삭제합니다.
![CleanUp3](/images/cleanup/cleanup_3.png)
6.	[IAM](https://console.aws.amazon.com/iam) role에서 **ecs-demogo**를 검색하여 삭제합니다.  
![CleanUp4](/images/cleanup/cleanup_4.png)
7.	[CloudFormation](https://console.aws.amazon.com/cloudformation)에서 **ecs-demogo** 스택을 삭제합니다. 
![CleanUp5](/images/cleanup/cleanup_5.png)
8.	만약 삭제하지 못하는 리소스가 있다면 모두 선택하고 **Delete stack**을 클릭합니다.  
![CleanUp6](/images/cleanup/cleanup_6.png)
9.	[VPC](https://console.aws.amazon.com/vpc)로 이동하여 **DemoGoECSVPC**를 수동으로 삭제합니다.
![Cleanup7](/images/cleanup/cleanup_7.png)
10.	[Amazon CloudWatch](https://console.aws.amazon.com/cloudwatch) Log groups로 이동하여 다음 리소스를 삭제합니다.
![CleanUp8](/images/cleanup/cleanup_8.png)
* /aws/ecs/containerinsights/DEMOGO-ECS/performance
* ecs-demogo-log
* firelens-container
</p>
