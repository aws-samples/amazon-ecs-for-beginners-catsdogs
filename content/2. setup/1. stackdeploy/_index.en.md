---
title: "Stack deploy"
weight: 11
---


{{% notice note %}}
You will deploy CloudFormation stack to create VPC environment, **Workstation** EC2 instance, IAM role, security groups and other prerequisites. 
{{% /notice %}}

Click the [Launch Stack button](https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-2#/stacks/new?stackName=ecs-demogo&templateURL=https://ecs-demogo-cf-template.s3.ap-northeast-2.amazonaws.com/demogostack.yaml).

{{% notice warning %}}
Important! You must choose **ap-northeast-2 (Seoul) region**.
{{% /notice %}}

{{% button href="https://console.aws.amazon.com/cloudformation/home?region=ap-northeast-2#/stacks/new?stackName=ecs-demogo&templateURL=https://ecs-demogo-cf-template.s3.ap-northeast-2.amazonaws.com/demogostack.yaml" icon="fab fa-aws" icon-position="left" %}}&nbsp;Launch Stack{{% /button %}}

1. You will be redirected to CloudFormation. 
![CloudFormation_01](../../../static/images/setup/cloud_formation1.png)
2. Select your key pair. 
![CloudFormation_02](../../../static/images/setup/cloud_formation2.png)
1. Skip **Configure stack options** and click **Next**.
2. Review and create - check **I acknowledge that AWS CloudFormation might create IAM resources** and click **Create stack.**
![CloudFormation_03](../../../static/images/setup/cloud_formation3.png)
5. Wait till the stack status turned to **CREATE_COMPLETE**. It takes about 5 minutes.
![CloudFormation_04](../../../static/images/setup/cloud_formation4.png)



