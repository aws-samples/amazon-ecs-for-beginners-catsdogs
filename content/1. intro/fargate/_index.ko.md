---
date: 2020-03-25
title: "EC2와 Fargate"
weight: 2
---

{{% notice note %}}
Amazon ECS는 EC2 뿐만 아니라 Fargate를 지원하여 컨테이너에 적합한 서버리스 컴퓨팅을 제공합니다. 본 실습에서는 동일한 EC2 클러스터 내에서 업무별 성격에 따라 EC2와 Fargate를 구분하여 사용하는 예시를 보여줍니다.
{{% /notice %}}

Amazon ECS에서 애플리케이션의 아키텍처 설계에 있어 어떤 시작 유형(Launch Type)을 사용할지 결정하는 것은 중요합니다. 예를 들어, 컴플라이언스 및 정부 요구사항 등으로 EC2 인스턴스에 대한 제어를 강화해야 하는 경우나, 좀 더 폭넓은 사용자 지정 옵션이 필요한 경우라면 EC2를 사용해야만 합니다. GPU 워크로드라면 이는 Fargate에서 현재 지원되지 않으므로 EC2를 사용해야 합니다. 만약 이런 경우가 아니라면, [AWS Fargate](https://docs.aws.amazon.com/ko_kr/AmazonECS/latest/developerguide/AWS_Fargate.html)는 EC2 인스턴스를 프로비저닝하거나 관리할 필요 없이 AWS에서 컨테이너를 시작할 수 있는 가장 쉬운 방법입니다. EC2, Fargate 시작 유형에 대해 더 상세한 내용은 다음 [지침](https://docs.aws.amazon.com/ko_kr/AmazonECS/latest/developerguide/application_architecture.html)을 참고합니다.  

![ECS](../../../static/images/intro/ec2fargate.svg)


**Cats and dogs**는 **web**, **cats**, **dogs**라는 세 가지 서비스로 구성되어 있습니다. 
본 실습에서 **DEMOGO-ECS** 클러스터에서 **web**과 **cats**는 *Amazon EC2* 시작 유형의 [작업 정의(Task Definition)](https://docs.aws.amazon.com/ko_kr/AmazonECS/latest/developerguide/task_definitions.html)으로, **dogs**는 *AWS Fargate* 시작 유형으로 구성해볼 것입니다. 

![MixedArchitecture](../../../static/images/intro/mixed_architecture.svg)

1. 가운데의 **Web**은 ALB의 DNS 이름으로 접근할 수 있는 메인 웹 페이지로, **I♥Cats**와 **I♥Dogs** 배너를 클릭하면 각각 **cats**와 **dogs**로 이동합니다.
2. **Cats**는 웹 화면을 새로고침할 때마다 고양이 사진을 랜덤으로 보여줍니다. 
3. **Dogs**는 웹 화면을 새로고침할 때마다 강아지 사진을 랜덤으로 보여줍니다. 





