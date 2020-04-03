---
date: 2020-03-28
title: "Dogs Task Definition"
weight: 36
---

{{% notice note %}}
Because **dogs** has **Fargate** launch type, not like **web** and **cats**, few options are different. For instance,  Amazon ECS task definitions for Fargate require that you specify CPU and memory at the task level. Amazon ECS tasks for Fargate require the awsvpc network mode, which provides each task with an elastic network interface. Find more on [Amazon ECS on AWS Fargate](https://docs.aws.amazon.com/ko_kr/AmazonECS/latest/developerguide/AWS_Fargate.html).
{{% /notice %}}

### Create dogsdef
1. Move to [Amazon ECS](https://console.aws.amazon.com/ecs) Task definition and create new.
2. Select launch type compatibility: **Fargate**
![SelectFargate](../../../../static/images/ecs/taskdef/taskdef_select_fargate.png)
3. Task Definition Name: `dogsdef`
![DogTask](../../../../static/images/ecs/taskdef/taskdef_dogs_1.png)
4. Task size
![TaskSize](../../../../static/images/ecs/taskdef/task_size_fargate.png)
- Task memory (GB): 0.5GB
- Task CPU (vCPU): 0.25 vCPU
5. Go to *Container Definitions* and click **Add container.** 
![AddContainer](../../../../static/images/ecs/taskdef/taskdef_add_container.png)
6. Configure **dogs** container.
![AddDogsContainer](../../../../static/images/ecs/taskdef/taskdef_add_dogs.png)
- Container name: `dogs`
- Image: your **dogs** latest image URI 
    * Copy from the browser tab opening Amazon ECR. 
![DogsLatest](../../../../static/images/ecr/ecr_dogs_latest.png)
- Memory Limits: Soft limit 128
- Port mappings: Container port 80
7. Click **Add** then the window closes. Check if **dogs** container is added. 
8. Click **Create**. 