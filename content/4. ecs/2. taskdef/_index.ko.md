---
date: 2020-03-25
title: "ECS 작업 정의"
weight: 33
---

{{% notice note %}}
Amazon ECS에서 Docker 컨테이너를 실행하려면 작업 정의(Task Definition)가 필요합니다. Amazon ECR 실습에서 생성한 cats, dogs의 도커 이미지를 참조하는 **catsdef**, **dogsdef** 작업 정의를 생성합니다. **web** 작업 정의가 사용할 도커 이미지는 별도로 제공됩니다. 
{{% /notice %}}

작업 정의에서 지정할 수 있는 몇몇 파라미터는 다음과 같습니다. [각 파라미터](https://docs.aws.amazon.com/ko_kr/AmazonECS/latest/developerguide/task_definition_parameters.html)에 대해 더 알아봅니다.  
- 작업의 각 컨테이너에 사용할 도커 이미지
- 각 작업 또는 작업 내 각 컨테이너에서 사용할 CPU 및 메모리의 양
- 사용할 시작 유형(Launch Type)으로서 해당 작업(Task)이 호스팅되는 인프라를 결정
- 작업의 컨테이너에 사용할 도커 네트워킹 모드
- 작업에 사용할 로깅 구성 등

![TaskDef](/images/ecs/ecs_taskdef.svg)

## 실습 순서
1. **web** 작업 정의 생성
2. **catsdef** 작업 정의 생성
3. **dogsdef** 작업 정의 생성