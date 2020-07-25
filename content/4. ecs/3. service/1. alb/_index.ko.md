---
title: "ALB 생성"
weight: 41
---
{{% notice note %}}
간단한 웹 서비스인 cats and dogs로 트래픽을 분배할 Application Load Balancer를 생성합니다. 실습에서 언급하지 않은 설정은 기본값으로 남겨둡니다.
{{% /notice %}}

## DEMOGO-ALB 생성
1. [EC2 Load Balancers](https://ap-northeast-2.console.aws.amazon.com/ec2/v2/home?region=ap-northeast-2#LoadBalancers:sort=loadBalancerName)로 이동합니다. 
2. **Create Load Balancer**를 클릭하고 **Application Load Balancer**를 선택합니다. 
![ALB](/images/ecs/service/select_alb.png)
3. Step 1: Configure Load Balancer 
- Name: `demogo-alb`
![ConfigALB](/images/ecs/service/demogo-elb.png)

4. 가용 영역
![AZs](/images/ecs/service/alb-vpc-az.png)
- VPC: DemoGoECSVPC (10.0.0.0/16)
- 가용영역 **ap-northeast-2a**와 **ap-northeast-2b**를 모두 체크합니다. 
- Subnet: **PublicSubnet1, 2**를 선택합니다. 
5. Click **Next: Configure Security Settings.**
5. Step 2: Configure Security Settings - **다음 단계로 넘어갑니다.** 

6. Step 3: Configure Security Groups
**existing security group**이 선택되었는지 확인하고 **default** 보안그룹은 선택 해제하고 **ecs-demogo-ALBSG**를 선택합니다. 
![ALBSG](/images/ecs/service/alb-security-group.png)
7. Step 4: Configure Routing 
![Routing](/images/ecs/service/alb_configure_routing.png)
- Target group: New target group
- Name: `web`
- Target type: Instance (앞 단계에서 생성한 **web** 작업 정의가 **EC2** 타입이기 때문입니다.)
- Port: 80
9. Step 5: Register Targets - **다음 단계로 넘어갑니다.**  
2. Step 6: Review and create - 설정값을 리뷰한 후 ALB를 생성합니다.
