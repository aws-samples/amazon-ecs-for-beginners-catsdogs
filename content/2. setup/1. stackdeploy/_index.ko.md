---
title: "스택 배포"
weight: 11
---


{{% notice note %}}
본 실습을 시작하기 전에 필요한 AWS 리소스를 생성해야 합니다. 실습에 필요한 리소스는 AWS CloudFormation을 사용하여 구성합니다.
{{% /notice %}}

## CloudFormation Template
Amazon ECS Cats and Dogs 실습에 필요한 AWS 리소스를 사전에 생성하기 위해 제공된 CloudFormation template을 사용하여 CloudFormation stack을 생성합니다. 스택을 생성하면 실습에 사용할 VPC 리소스, ECS 인스턴스와 ALB가 사용할 보안그룹, Workstation 인스턴스와 IAM 리소스 등이 생성 됩니다. 이 모든 리소스는 Cats and Dogs 실습을 진행하는 데 필요합니다.

CloudFormation 스택을 시작하려면, [Launch Stack 버튼](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-2#/stacks/new?stackName=ecs-demogo&templateURL=https://ecs-demogo-cf-template.s3.ap-northeast-2.amazonaws.com/demogostack.yaml)을 클릭해서 CloudFormation 콘솔로 이동합니다.

{{% notice warning %}}
중요: 이 탬플릿은 ap-northeast-2(서울)을 위해 만들어졌으며 다른 AWS 리전에서는 작동하지 **않습니다.**
{{% /notice %}}

{{% button href="https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-2#/stacks/new?stackName=ecs-demogo&templateURL=https://ecs-demogo-cf-template.s3.ap-northeast-2.amazonaws.com/demogostack.yaml" icon="fab fa-aws" icon-position="left" %}}&nbsp;Launch Stack{{% /button %}}

![CloudFormation_01](/images/setup/cloud_formation1.png)

스택 생성 단계에서 스택 이름을 입력하고 실습에서 사용할 EC2 키 페어를 선택합니다. 그리고 나머지는 기본 값을 유지하고 마지막 단계에서 CloudFormation이 IAM 리소스를 생성할 때 커스텀 이름을 사용할 수 있게 **Acknowledge 체크박스를 선택**하고 **Create stack** (스택 생성)을 클릭합니다.

![CloudFormation_02](/images/setup/cloud_formation2.png)
CloudFormation 스택을 완료하는 데 약 5분 정도 소요됩니다. 
![CloudFormation_03](/images/setup/cloud_formation3.png)

CloudFormation 콘솔을 확인하고 아래와 같이 **CREATE_COMPLETE** 상태를 기다립니다.
![CloudFormation_04](/images/setup/cloud_formation4.png)



