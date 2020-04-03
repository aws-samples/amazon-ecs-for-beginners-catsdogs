---
title: "클러스터 오토스케일링"
weight: 52

---

{{% notice note %}}
ECS Cluster Auto Scaling을 사용하면 ASG의 확장 정책은 ECS Capacity Provider를 통해 ECS에서 관리됩니다. 사용자는 ASG의 관리형 확장을 활성화하고, ASG에서 초과 용량을 예약하고, ASG에서 인스턴스 종료를 관리하도록 Capacity Provider를 구성할 수 있습니다. 
{{% /notice %}}

{{% notice note %}}
EC2와 Fargate 모두에서 용량 공급자(Capacity Providers)를 사용할 수 있습니다. EC2를 사용하면 EC2 Auto Scaling 그룹(ASG)과 연결된 용량 공급자를 생성할 수 있습니다. 이를 통해 ASG의 확장을 관리하여 작업을 실행하는 데 필요한 용량이 아직 사용할 수 없는 경우에도 요청되도록 할 수 있습니다. 작업과 서비스를 실행할 때 여러 용량 공급자로 작업(Task)과 서비스를 분할할 수 있습니다. 본 실습에서는 ASG와 연결된 EC2 용량 공급자를 생성하고 부하 테스트를 수행하여 어떻게 클러스터 오토스케일링이 동작하는지 살펴봅니다. 
{{% /notice %}}

![ClusterAutoScale](../../../static/images/autoscale/cluster_auto_scale.svg)

## 실습 순서
1. [용량 공급자 생성](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/ko/autoscale/cluster/capacityprovider/)
2. [ASG(Auto Scaling Group) 구성](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/ko/autoscale/cluster/asg/)
3. [클러스터 부하 테스트](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/ko/autoscale/cluster/loadtest/)
4. [결과 확인](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/ko/autoscale/cluster/monitoring/)
