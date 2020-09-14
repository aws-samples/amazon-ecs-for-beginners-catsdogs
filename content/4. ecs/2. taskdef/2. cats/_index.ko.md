---
date: 2020-03-25
title: "Cats 작업 정의"
weight: 35
---

{{% notice note %}}
Cats 작업 정의는 web과 마찬가지로 **EC2 타입**을 선택합니다. 추가로 로그 라우터인 **FireLens**를 활성화하여 **컨테이너 로그**를 Amazon CloudWatch Logs로 전송하도록 설정합니다.
{{% /notice %}}

## catsdef 생성
1)	[Amazon ECS](https://console.aws.amazon.com/ecs) Task definition으로 이동하여 새 작업 정의를 생성합니다.  
2)	Select launch type compatibility: **EC2**를 선택합니다.  
![SelectEC2](/images/ecs/taskdef/taskdef_select_ec2.png)
3)	Task Definition Name: `catsdef`를 입력합니다.

### FireLens 구성
#### FireLens 활성화
*Log Router Integration*까지 스크롤을 내린 후 *Enable Firelens Intigration* 박스에 체크되어 있는지 확인합니다. **fluentbit** 타입을 선택하고 **Apply**를 클릭합니다. 

{{% notice note %}}
AWS는 CloudWatch Logs 및 Kinesis Data Firehose 용 플러그인이 포함된 Fluent Bit 이미지를 제공합니다. Fluentd보다는 Fluent Bit이 리소스 사용률이 낮기 때문에 이를 로그 라우터로 사용하는 것이 좋습니다. 자세한 내용은 [Fluent Bit용 CloudWatch Logs](https://github.com/aws/amazon-cloudwatch-logs-for-fluent-bit) 및 [Fluent Bit용 Amazon Kinesis Firehose](https://github.com/aws/amazon-kinesis-firehose-for-fluent-bit)을 참고합니다. 
{{% /notice %}}

![EnableFireLens](/images/ecs/taskdef/enable_firelens.png)

다시 *Container Definitions*로 돌아와서 **log_router**컨테이너가 생성된 것을 확인합니다.  
![CheckLogRouter](/images/ecs/taskdef/taskdef_added_log_router.png)

#### log_router 컨테이너의 로그 설정
**log_router** 컨테이너를 클릭하여 *Advanced container configuration – STORAGE AND LOGGING*에서 로그를 설정합니다.
1. Log configuration: **Auto-configure CloudWatch Logs**가 선택 해제되어 있는지 확인합니다. 
2. 다음과 같이 로그를 설정합니다.
![LogConfig](/images/ecs/taskdef/taskdef_log_router_logging.png)
- Log driver: **awslogs**
- Log options: 키/값을 다음과 같이 작성합니다. 정확한 설정을 위해 복사 및 붙여넣기를 권장합니다.  
  
|Key|Value|입력값|
|------|---|---|
|awslogs-group|Value|`firelens-container`|
|awslogs-region|Value|`ap-northeast-2`|
|awslogs-stream-prefix|Value|`firelens`|
|`awslogs-create-group`|Value|`true`|

3. 맨 하단에서 **Update**를 클릭하여 **log_router**의 설정을 마칩니다. 

### cats 컨테이너 추가
*Container Definitions*에서 **Add container**를 클릭하여 cats 컨테이너를 추가합니다.
![CatsTask](/images/ecs/taskdef/taskdef_cats_uri.png)
1. cats 컨테이너를 다음과 같이 구성합니다. 
- Container name: `cats`
- Image: 실습자의 **cats** latest 이미지 URI 입력 

{{% notice tip %}}
브라우저에서 새 탭을 열어 ECR로 이동합니다. cats 리포지토리의 latest 태그된 이미지 URL 앞의 네모를 클릭하여 복사합니다. dogs도 동일한 작업을 수행해야 하므로 다음 단계까지 창을 열어둡니다. 
{{% /notice %}}
![CatsLatest](/images/ecs/taskdef/taskdef_cats_latest_image.png)
- Memory Limits - Hard limit 128
- Port mappings
    + Host port: 0
    + Container port: 80 (tcp)

<!---9)	*Advanced container configuration – ENVIRONMENT*까지 스크롤을 내립니다.
![ConfigCatsContainer](./images/Picture11.png) 
- CPU Unit: 100 --->
#### cats 컨테이너 로그 설정
*Advanced container configuration – STORAGE AND LOGGING*에서 **cats** 컨테이너의 로그를 설정합니다.
1. Log configuration: **Auto-configure Cloudwatch Logs**가 선택 해제되어 있는지 확인합니다.
2. 다음과 같이 **cats** 컨테이너의 로그를 설정합니다. 
![CatsLogConfig](/images/ecs/taskdef/taskdef_cats_log_config.png)
- Log driver: awsfirelens
- Log options

|Key|Value|입력값|
|------|---|---|
|Name|Value|`cloudwatch`|
|`log_group_name`|Value|`ecs-demogo-log`|
|`log_stream_prefix`|Value|`from-fluent-bit`|
|`region`|Value|`ap-northeast-2`|
|`auto_create_group`|Value|`true`|

3. **Add**를 누르면 창이 닫힙니다. cats 컨테이너가 추가된 것을 확인합니다.
4. **Create** 클릭하여 **catsdef** 생성을 마칩니다. 



{{% notice tip %}}
아래의 JSON 템플릿을 이용해 위의 번거로운 GUI 작업 없이 동일한 **cats** 작업 정의를 구성할 수 있습니다. 콘솔에서 JSON을 붙여넣거나 파일로 저장 후 AWS CLI --cli-input-json 옵션을 사용할 수 있습니다. 
{{% /notice %}}

* Task Definition 생성 화면에서 스크롤을 내리면 **Configure via JSON** 버튼이 있습니다.
![](/images/ecs/taskdef/json.png)

```
{
  "ipcMode": null,
  "executionRoleArn": null,
  "containerDefinitions": [
    {
      "dnsSearchDomains": null,
      "environmentFiles": null,
      "logConfiguration": null,
      "entryPoint": null,
      "portMappings": [],
      "command": null,
      "linuxParameters": null,
      "cpu": 0,
      "environment": [],
      "resourceRequirements": null,
      "ulimits": null,
      "dnsServers": null,
      "mountPoints": [],
      "workingDirectory": null,
      "secrets": null,
      "dockerSecurityOptions": null,
      "memory": null,
      "memoryReservation": 50,
      "volumesFrom": [],
      "stopTimeout": null,
      "image": "906394416424.dkr.ecr.ap-northeast-2.amazonaws.com/aws-for-fluent-bit:latest",
      "startTimeout": null,
      "firelensConfiguration": {
        "type": "fluentbit",
        "options": null
      },
      "dependsOn": null,
      "disableNetworking": null,
      "interactive": null,
      "healthCheck": null,
      "essential": true,
      "links": null,
      "hostname": null,
      "extraHosts": null,
      "pseudoTerminal": null,
      "user": "0",
      "readonlyRootFilesystem": null,
      "dockerLabels": null,
      "systemControls": null,
      "privileged": null,
      "name": "log_router"
    },
    {
      "dnsSearchDomains": null,
      "environmentFiles": null,
      "logConfiguration": {
        "logDriver": "awsfirelens",
        "secretOptions": null,
        "options": {
          "log_group_name": "ecs-demogo-log",
          "auto_create_group": "true",
          "log_stream_prefix": "from-fluent-bit",
          "region": "ap-northeast-2",
          "Name": "cloudwatch"
        }
      },
      "entryPoint": null,
      "portMappings": [
        {
          "hostPort": 0,
          "protocol": "tcp",
          "containerPort": 80
        }
      ],
      "command": null,
      "linuxParameters": null,
      "cpu": 0,
      "environment": [],
      "resourceRequirements": null,
      "ulimits": null,
      "dnsServers": null,
      "mountPoints": [],
      "workingDirectory": null,
      "secrets": null,
      "dockerSecurityOptions": null,
      "memory": 128,
      "memoryReservation": null,
      "volumesFrom": [],
      "stopTimeout": null,
      "image": "038445823716.dkr.ecr.ap-northeast-2.amazonaws.com/cats:latest",
      "startTimeout": null,
      "firelensConfiguration": null,
      "dependsOn": null,
      "disableNetworking": null,
      "interactive": null,
      "healthCheck": null,
      "essential": true,
      "links": null,
      "hostname": null,
      "extraHosts": null,
      "pseudoTerminal": null,
      "user": null,
      "readonlyRootFilesystem": null,
      "dockerLabels": null,
      "systemControls": null,
      "privileged": null,
      "name": "cats"
    }
  ],
  "placementConstraints": [],
  "memory": null,
  "taskRoleArn": null,
  "compatibilities": [
    "EC2"
  ],
  "taskDefinitionArn": "arn:aws:ecs:ap-northeast-2:038445823716:task-definition/catsdef:16",
  "family": "catsdef",
  "requiresAttributes": [
    {
      "targetId": null,
      "targetType": null,
      "value": null,
      "name": "com.amazonaws.ecs.capability.ecr-auth"
    },
    {
      "targetId": null,
      "targetType": null,
      "value": null,
      "name": "ecs.capability.firelens.fluentbit"
    },
    {
      "targetId": null,
      "targetType": null,
      "value": null,
      "name": "com.amazonaws.ecs.capability.docker-remote-api.1.19"
    },
    {
      "targetId": null,
      "targetType": null,
      "value": null,
      "name": "com.amazonaws.ecs.capability.docker-remote-api.1.21"
    },
    {
      "targetId": null,
      "targetType": null,
      "value": null,
      "name": "com.amazonaws.ecs.capability.logging-driver.awsfirelens"
    }
  ],
  "pidMode": null,
  "requiresCompatibilities": [
    "EC2"
  ],
  "networkMode": null,
  "cpu": null,
  "revision": 16,
  "status": "ACTIVE",
  "inferenceAccelerators": null,
  "proxyConfiguration": null,
  "volumes": []
}
```