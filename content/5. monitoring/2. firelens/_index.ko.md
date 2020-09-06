---
title: "AWS FireLens를 이용한 로그 라우팅"
weight: 42
---

{{% notice note %}}
이번 실습을 위해 앞 실습 **ECS 클러스터**에서 **ecsInstanceRole**에 **CloudWatchLogsFullAccess**를 부여하고, **ECS 작업 정의**에서 **catsdef** 작업 정의를 생성할 때 **FireLens**를 활성화한 것입니다. 
{{% /notice %}}

{{% notice note %}}
Amazon ECS용 FireLens를 사용하면 작업 정의 파라미터를 사용하여 로그를 AWS 서비스 또는 AWS 파트너 네트워크(APN) 대상으로 라우팅하여 로그를 저장 및 분석할 수 있습니다. 본 실습에서는 AWS가 제공한 Fluent Bit FireLens를 이용해 AWS 서비스인 CloudWatch Logs로 로그를 전송합니다. 
{{% /notice %}}


1)	[CloudWatch Log groups](https://ap-northeast-2.console.aws.amazon.com/cloudwatch/home?region=ap-northeast-2#logs:)로 이동합니다.
2)	**ecs-demogo-log**를 검색합니다. 
![FilterLogGroups](/images/monitoring/firelens_1.png)
3)	**ecs-demogo-log**를 클릭하고 각 로그 스트림을 살펴봅니다. 
![LogStream](/images/monitoring/firelens_2.png)
4)	각 로그를 펼쳐서 더 상세한 정보를 찾을 수 있습니다. container_id, ecs_cluster, etcs_task_definition 등의 정보를 담고 있습니다.  
![DetailLogs](/images/monitoring/firelens_3.png)
