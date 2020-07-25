---
title: "Service Cats"
weight: 43
---

### Create service cats
1)	Click **Create** in DEMOGO-ECS **Services** tab.
2)	Step 1: Configure service 
![CreateCats](/images/ecs/service/cats_create.png)
- Launch type: **EC2**
- Task Definition 
Family: **catsdef**
Revision: 1 **(latest)**
- Service name: `cats`
- Number of tasks: `2`
- Task Placement: **AZ Balanced Spread**
1. **Next step** 

4)	Step 2: Configure network
- Load balancing
  -  Load balancer type – Application Load Balancer
  -  Load balancer name: Select **demogo-alb**
  
1. Select **cats:0:80** and click **Add to load balancer.** 
![AddCats](/images/ecs/service/cats_add_to_lb.png)

1. **Container to load balance**
  ![CatsContainer](/images/ecs/service/cats_configure_container_to_lb.png)
- Production listener port: **80:HTTP**
- Target group name: Click **create new** and type `cats`
- path pattern: /cats*, Evaluation order: `1`
- Health check path: `/cats/`
1. Service discovery: **Uncheck**  
![ServiceDiscovery](/images/ecs/service/service_discovery.png)
1. Set Auto Scaling: Select **Do not adjust the service's desired count**
![AutoScale](/images/ecs/service/set_auto_scale.png)
1. Review and create service **cats.**  