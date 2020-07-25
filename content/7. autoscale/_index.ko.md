---
title: "오토스케일링"
weight: 50
pre: "<b>6. </b>"
---

{{% notice note %}}
앞 실습 **5. 모니터링**에서 살펴본 것처럼 Amazon ECS는 서비스의 평균 CPU, 메모리 사용량 등을 CloudWatch의 지표를 게시합니다. 이와 함께 다른 CloudWatch 지표를 사용하여 [사용률](https://docs.aws.amazon.com/ko_kr/AmazonECS/latest/developerguide/cloudwatch-metrics.html#service_utilization)에 맞추어 **서비스**를 **자동으로 확장 또는 축소**합니다. 더 나아가 Amazon ECS **클러스터 오토스케일링**을 사용하면 클러스터의 모든 태스크 및 서비스의 리소스 수요에 맞게 필요에 따라 자동으로 인스턴스를 확장할 수 있습니다. 본 실습에서 서비스와 클러스터에 부하테스트를 수행하여 어떻게 두 가지 오토 스케일링이 동작하는지 알아봅니다.
{{% /notice %}}

## Amazon ECS 서비스 오토스케일링
![ServiceAutoScale](/images/autoscale/service_auto_scale.svg)
Amazon ECS는 수요에 맞게 서비스를 스케일 아웃(**태스크 수를 추가**)하거나 사용량이 적은 때에는 스케일 인(**태스크 수를 감소**)하여 자동으로 조정할 수 있습니다. 

## Amazon ECS 클러스터 오토스케일링
![ClusterAutoScale](/images/autoscale/cluster_auto_scale.svg)
ECS Cluster Auto Scaling을 사용하면 EC2에서 실행되는 ECS 클러스터가 클러스터의 모든 태스크 및 서비스의 리소스 수요에 맞게 필요에 따라 자동으로 확장할 수 있습니다. 

ECS Cluster Auto Scaling은 ECS에서 ECS **용량 공급자**를 사용하여 사용자를 대신해 Amazon EC2 Auto Scaling 그룹(ASG)을 관리합니다. 사용자는 **ASG**의 관리형 확장을 활성화하고, ASG에서 초과 용량을 예약하고, ASG에서 인스턴스 종료를 관리하도록 용량 공급자를 구성할 수 있습니다. 

 > 원래 ECS는 ASG의 확장을 직접 관리하는 기능이 없었습니다. 그 대신 ECS 외부에서 ASG에 수동으로 확장 정책을 설정해야 했고, 확장에 제공되는 지표에는 사용자가 원하는 태스크 수가 반영되지 않고 이미 실행되는 태스크만 반영되었습니다. 


