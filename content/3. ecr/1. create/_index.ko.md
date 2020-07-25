---
title: "ECR 생성"
weight: 21
---

{{% notice note %}}
이번 실습에서는 cats와 dogs가 사용할 ECR 리포지토리를 생성합니다. 
{{% /notice %}}

**Amazon ECR는 개발자가 Docker 컨테이너 이미지를 손쉽게 저장, 관리 및 배포할 수 있게 해주는 완전관리형 Docker 컨테이너 레지스트리로, Amazon ECS와 통합되어 개발에서 프로덕션까지의 워크플로우를 간소화합니다.** <br/><br/>

1. [Amazon ECR](https://console.aws.amazon.com/ecr)로 이동합니다. ECR을 처음 사용하는 경우 Welcome 페이지가 보입니다. **Get Started**를 클릭하거나 좌측 네비게이션 바에서 **Repositories**를 클릭합니다. 
![MoveToECR](/images/ecr/ecr_3.png)
1. **Create repository**를 클릭하고 이름을 **cats**라고 지정합니다. 같은 방식으로 **dogs** 리포지토리도 생성합니다. 
![CreateECR](/images/ecr/ecr_4.png)
1. 두 리포지토리가 잘 생성되었는지 확인합니다.
![CheckECR](/images/ecr/ecr_5.png)