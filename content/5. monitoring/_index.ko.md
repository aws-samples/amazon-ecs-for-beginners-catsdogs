---
title: "모니터링"
weight: 40
pre: "<b>5. </b>"

---

{{% notice note %}}
모니터링은 Amazon ECS와 사용자 AWS 솔루션의 안정성, 가용성 및 성능을 유지하는 중요한 역할을 합니다. 다중 지점 실패(multi-point failure)발생시 이를 보다 쉽게 디버깅할 수 있도록 AWS 솔루션의 모든 부분으로부터 모니터링 데이터를 수집해야 합니다.
{{% /notice %}}

![MonitoringOverview](../../static/images/monitoring/monitoring.svg)

## Amazon CloudWatch 컨테이너 인사이트
CloudWatch Container Insights는 컨테이너 애플리케이션 및 마이크로서비스에 대한  **CPU, 메모리, 디스크, 네트워크 같은 리소스 사용률** 등의 지표와 로그를 수집 및 처리하여 요약합니다. 

## AWS FireLens
FireLens는 Amazon ECS 및 AWS Fargate용 **컨테이너 로그 라우터**로, AWS의 서비스나 로그 분석 및 저장용 파트너 솔루션을 광범위하게 사용할 수 있는 확장성을 제공합니다. FireLens on Amazon ECS and AWS Fargate [다양한 샘플 아키텍처](https://github.com/aws-samples/amazon-ecs-firelens-examples)를 참고합니다. 이번 실습에서는 FireLens FluentBit과 CloudWatch Logs를 이용해 손쉽게 구성해봅니다.
