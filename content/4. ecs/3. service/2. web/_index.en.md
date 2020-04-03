---
title: "Service Web"
weight: 42
---

## Create service web 
1)	Move to [Amazon ECS](https://console.aws.amazon.com/ecs) and select **DEMOGO-ECS** cluster. Go to **Services** tab and click **Create**. Leave default to the rest options not mentioned.
![CreateService](../../../../static/images/ecs/service/create_service.png)
2)	Step 1: Configure service 
![ConfigureWeb](../../../../static/images/ecs/service/configure_web_service.png)
- Launch type: EC2 
- Task Definition 
    - Family: **web**
    - Revision: **1 (latest)** (Revision number might be different. Choose the **latest**.) 
- Service name: `web`
- Number of tasks: `2`
- Task Placement: Select **AZ Balanced Spread** and click **Next step.**
3)	Step 2: Configure network
![WebLB](../../../../static/images/ecs/service/web_lb.png)
- Load balancing
    - Load balancer type: **Application Load Balancer** 
    - Service IAM role: **ecsServiceRole** (If you don’t have any, select **create new role.**)
    - Load balancer name: Select **demogo-alb**
![ContainerPort](../../../../static/images/ecs/service/web_container_port.png)
- Container to load balance: Select **web:0:80** and click **Add to load balancer.**

![WebContainer](../../../../static/images/ecs/service/web_al_2.png)
- Production listener port: Select **80:HTTP** from the dropdown.
- Target group name: Select **web** from the dropdown then other options will be automatically filled. 

4)	Service discovery (optional) – **Uncheck** and click **Next**
![ServiceDiscovery](../../../../static/images/ecs/service/service_discovery.png)
5)	Set Auto Scaling: **Do not adjust the service's desired count**
![AutoScale](../../../../static/images/ecs/service/set_auto_scale.png)
{{% notice note %}}
You will configure **service auto scale** in **6. Auto Scaling** later.
{{% /notice %}}
6)	Review and create **web** service. 
7)	Click **View services** and check if **two** web tasks are **running**.
![Check](../../../../static/images/ecs/service/check_web_tasks.png) 