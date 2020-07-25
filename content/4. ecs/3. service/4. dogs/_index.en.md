---
title: "Service Dogs"
weight: 44
---

### Create service dogs 
1) Click **Create** in DEMOGO-ECS **Services** tab.
2)	Step 1: Configure service 
![CreateDogs](/images/ecs/service/service_dogs_create.png)
- Launch type: **Fargate**
- Task Definition 
Family: **dogsdef**
Revision: 1 **(latest)** 
- Service name: `dogs`
- Number of tasks: `2`
- Task Placement: **AZ Balanced Spread**
1. **Next step**
2. Configure network
![ConfigureVPC](/images/ecs/service/service_dogs_vpc.png)
- Cluster VPC: **10.0.0.0/16 (DemoGoECSVPC)**
- Subnets: Select **PrivateSubnet1**(10.0.3.0/24) and **PrivateSubnet2**(10.0.4.0/24)
- Security Group: It will be auto-created. 
- Auto-assgin public IP: **DISABLED**
1. Load balancer type: Select **Application Load Balancer**
2. Container name: Select **dogs:80:80** and click **Add to load balancer.**
![AddToLB](/images/ecs/service/dogs_add_to_lb.png)
1. **Container to load balance**
![DogsALB](/images/ecs/service/dogs_container_to_lb.png)
- Production Listener port: **80:HTTP**
- Target group name: Select **create new** and type `dogs`
- path pattern: /dogs*, Evaluation order: `2`
- Health check path: `/dogs/`
1. Service discovery: **Uncheck**
![ServiceDiscovery](/images/ecs/service/service_discovery.png)
1. Set Auto Scaling: **Do not adjust the service's desired count**
![AutoScale](/images/ecs/service/set_auto_scale.png)
10.	Review and create service **dogs.**