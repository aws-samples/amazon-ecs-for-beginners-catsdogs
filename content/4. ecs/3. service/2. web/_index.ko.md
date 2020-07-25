---
title: "Web 서비스"
weight: 42
---

## Web 서비스 생성하기 
1)	[Amazon ECS](https://console.aws.amazon.com/ecs)로 이동하여 DEMOGO-ECS 클러스터를 선택합니다. **Web** 서비스를 생성하기 위해 **Services** 탭에서 **Create**을 클릭합니다. 별도 설명이 없는 설정은 기본값으로 남겨둡니다.
![CreateService](/images/ecs/service/create_service.png)
2)	Step 1: Configure service 
![ConfigureWeb](/images/ecs/service/configure_web_service.png)
- Launch type: EC2 
- Task Definition 
    - Family: **web**
    - Revision: **1 (latest)** (Revision 값이 여러개라면 'latest'를 선택합니다.) 
- Service name: `web`
- Number of tasks: `2`
- Task Placement: **AZ Balanced Spread**을 선택하고 **Next step**을 클릭합니다.
3)	Step 2: Configure network
![WebLB](/images/ecs/service/web_lb.png)
- Load balancing
    - Load balancer type: **Application Load Balancer** 
    - Service IAM role: **ecsServiceRole** (만약 IAM role이 없다면 **create new role**을 선택합니다.)
    - Load balancer name: **demogo-alb**를 선택합니다.
![ContainerPort](/images/ecs/service/web_container_port.png)
- Container to load balance: **web:0:80**을 선택하고 **Add to load balancer**를 클릭합니다. 

![WebContainer](/images/ecs/service/web_al_2.png)
- Production listener port: 드롭다운에서 **80:HTTP**를 선택합니다. 
- Target group name: 드롭다운에서 **web**을 선택합니다. 그러면 다른 옵션들은 자동으로 채워집니다.  

4)	Service discovery (optional) – 체크박스를 선택 **해제**하고 **Next**를 클릭합니다. 
![ServiceDiscovery](/images/ecs/service/service_discovery.png)
5)	Set Auto Scaling: **Do not adjust the service's desired count**를 선택합니다.
![AutoScale](/images/ecs/service/set_auto_scale.png)
{{% notice note %}}
실습 **6. 오토스케일링**에서 **web**을 업데이트하여 **서비스 오토스케일링**을 설정할 것입니다. 지금 단계에서는 자동 조정을 비활성화한 상태로 실습을 계속합니다.
{{% /notice %}}
6)	Review: 설정을 검토하고 **web** 서비스를 생성합니다. 
7)	View services를 클릭하여 **2개**의 **web 태스크**가 생성된 것을 확인합니다.
![Check](/images/ecs/service/check_web_tasks.png) 