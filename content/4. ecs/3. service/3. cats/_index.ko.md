---
title: "Cats 서비스"
weight: 43
---

### Cats 서비스 생성하기 
1)	DEMOGO-ECS 클러스터의 **Services** 탭에서 **Create**을 클릭합니다. 
2)	Step 1: Configure service 
![CreateCats](/images/ecs/service/cats_create.png)
- Launch type: **EC2** 
- Task Definition 
Family: **catsdef**
Revision: 1 **(latest)** 
- Service name: `cats`
- Number of tasks: `2`
- Task Placement: **AZ Balanced Spread**
3. **Next step**을 클릭합니다.

4)	Step 2: Configure network
- Load balancing
  -  Load balancer type – Application Load Balancer
  -  Load balancer name: **demogo-alb**를 선택합니다. 
  
5. **cats:0:80**이 선택된 상태에서 **Add to load balancer**를 클릭합니다.
![AddCats](/images/ecs/service/cats_add_to_lb.png)

6. **Container to load balance**를 설정합니다.
  ![CatsContainer](/images/ecs/service/cats_configure_container_to_lb.png)
- Production listener port: **80:HTTP**
- Target group name: **create new**를 선택하고 `cats`를 입력합니다. 
- path pattern: /cats*, Evaluation order: `1`
- Health check path: `/cats/`
7. Service discovery: 선택 **해제**합니다.  
![ServiceDiscovery](/images/ecs/service/service_discovery.png)
1. Set Auto Scaling: **Do not adjust the service's desired count**를 선택합니다. 
![AutoScale](/images/ecs/service/set_auto_scale.png)
9. Review: 검토 후 **cats** 서비스를 생성합니다. 