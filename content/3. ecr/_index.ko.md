---
title: "Amazon ECR"
weight: 20
pre: "<b>3. </b>"
---

{{% notice note %}}
Amazon Elastic Container Registry(ECR)를 Amazon ECS와 통합하여 Amazon ECS에서 실행되는 애플리케이션에 대한 컨테이너 이미지를 손쉽게 저장, 실행 및 관리할 수 있습니다. 태스크 정의에 Amazon ECR 리포지토리를 지정하기만 하면 Amazon ECS에서 애플리케이션에 적합한 이미지를 가져옵니다.
{{% /notice %}}

## Amazon ECR 소개
![ECR](../../static/images/ecr/ecr_1.svg)

## 실습 단계
![ECRLab](../../static/images/ecr/ecr_2.svg)

1. **cats, dogs** ECR 리포지토리 생성하기
2. *Workstation*에 접속하여 **cats, dogs** 도커 이미지 빌드하고 태깅하기
3. 작업한 도커 이미지를 Amazon ECR로 푸시하기
