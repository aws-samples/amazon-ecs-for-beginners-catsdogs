---
date: 2020-03-28
title: "Web task definition"
weight: 34
---

{{% notice note %}}
**Web** task definition uses **EC2** launch type. The docker iamge which **web** uses is provided. Leave default unless specified. 
{{% /notice %}}

### Create web task definition
1. Move to [Amazon ECS](https://console.aws.amazon.com/ecs) Task definition. Click  **Create new Task Definition**
2. Select launch type compatibility: **EC2** 
![SelectEC2](../../../../static/images/ecs/taskdef/taskdef_select_ec2.png)
1. Task Definition Name: `web`
![WebTask](../../../../static/images/ecs/taskdef/taskdef_web_1.png)
1. Scroll down to *Container Definitions* and click **Add container**.
![AddWebContainer](../../../../static/images/ecs/taskdef/taskdef_add_container.png)
1. Config **web** container.  
![ConfigWebContainer](../../../../static/images/ecs/taskdef/taskdef_add_container_2.png)
- Container name: `web`
- Image: `038445823716.dkr.ecr.ap-northeast-2.amazonaws.com/web:latest`
- Memory Limits - Hard limit 128
- Port mappings 
    + Host port: 0	
    + Container port: 80

6. Click **Add** in tne bottom right. The window closes.
2. Click **create**.