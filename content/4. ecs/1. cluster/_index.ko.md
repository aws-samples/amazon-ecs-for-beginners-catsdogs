---
date: 2020-03-26
title: "ECS 클러스터"
weight: 31
---

{{% notice note %}}
Amazon ECS 클러스터는 작업 또는 서비스의 논리적 그룹입니다. 이번 실습에서는 고가용성을 위해 2개 가용영역에 DEMOGO-ECS 클러스터를 배포하고, 다음 실습 단계인 **5. 모니터링** 실습에 필요한 IAM 권한을 ECS 인스턴스에 부여합니다. 
{{% /notice %}}

![ECS](../../../static/images/ecs/ecs_cluster.svg)

1. **DEMOGO-ECS** 클러스터 생성
2. **ecsInstanceRole**에 CloudWatch Logs 권한 부여