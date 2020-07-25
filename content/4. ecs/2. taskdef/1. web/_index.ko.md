---
date: 2020-03-25
title: "Web 작업 정의"
weight: 34
---

{{% notice note %}}
**Web** 작업 정의는 **EC2** 타입으로 생성합니다. Web이 사용할 도커 이미지는 본 실습에서 제공하는 URI를 사용합니다. 별도로 설명하지 않은 설정은 기본값으로 둡니다.
{{% /notice %}}

### Web 작업 정의 생성
1. [Amazon ECS](https://console.aws.amazon.com/ecs) Task definition로 이동하여 **Create new Task Definition**을 클릭합니다. 
2. Select launch type compatibility: **EC2**를 선택합니다.
![SelectEC2](/images/ecs/taskdef/taskdef_select_ec2.png)
1. Task Definition Name: `web`를 입력합니다. 
![WebTask](/images/ecs/taskdef/taskdef_web_1.png)
1. *Container Definitions*까지 스크롤을 내린 후 **Add container**를 클릭합니다.
![AddWebContainer](/images/ecs/taskdef/taskdef_add_container.png)
1. Web 컨테이너를 설정합니다.
![ConfigWebContainer](/images/ecs/taskdef/taskdef_add_container_2.png)


- Container name: `web`
- Image: `038445823716.dkr.ecr.ap-northeast-2.amazonaws.com/web:latest` 
- Memory Limits - Hard limit 128
- Port mappings 
    + Host port: 0	
    + Container port: 80
<!---1. *Advanced container configuration – ENVIRONMENT*까지 스크롤을 내립니다.
![WebContainerCPU](./images/Picture5.png)
- CPU Unit: 100--->

6. 우측 하단의 **Add**를 클릭합니다. 창이 닫힙니다. 
2. 하단의 **create**을 클릭하여 **web** 작업 정의를 생성합니다. 