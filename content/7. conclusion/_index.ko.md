---
title: "실습 결과"
weight: 60
pre: "<b>7. </b>"
---

## 우리는 지금까지

*  **완전관리형 컨테이너 오케스트레이션 서비스**인 Amazon ECS에 *cats and dogs*를 **ALB**과 통합하여 배포했습니다. 
* 각 서비스별 특성에 맞게 **EC2**와 **Fargate** 중 적합한 **시작 유형**을 선택했습니다.
* Amazon ECR에서 cats와 dogs의 **도커 이미지를 관리**했습니다.
* Amazon CloudWatch **Container Insights**로 ECS 클러스터와 서비스, 컨테이너를 **모니터링**했습니다. 
* FluentBit 기반의 **AWS FireLens**를 이용해 Amazon CloudWatch Logs로 **컨테이너 로그**를 수집했습니다.
* 사용량에 맞게 **ECS 서비스와 클러스터를 오토스케일링**하도록 설정했습니다. 

## 그럼에도
* 이 모든 과제를 수행하면서 단 하나의 서버도 구성, 패치, 리부팅하는 등의 관리를 할 필요가 **없었습니다**! 
