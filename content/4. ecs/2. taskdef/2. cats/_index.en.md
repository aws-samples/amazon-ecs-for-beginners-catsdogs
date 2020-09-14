---
date: 2020-03-25
title: "Cats task definition"
weight: 35
---

{{% notice note %}}
You just created **web** task definition and the way to define **cats** task is almost same. The only difference with **cats** is to configure **FireLens**, which is a container log router for Amazon ECS to send logs to Amazon CloudWatch Logs. 
{{% /notice %}}

## Create catsdef
1)	Move to [Amazon ECS](https://console.aws.amazon.com/ecs) Task definition to create new.  
2)	Select launch type compatibility: **EC2**  
![SelectEC2](/images/ecs/taskdef/taskdef_select_ec2.png)
3)	Task Definition Name: `catsdef`  

### Configure FireLens
#### Enable FireLens
4)	Scroll down to *Log Router Integration* and check *Enable Firelens Intigration.* Select **fluentbit** and click **Apply.**  

{{% notice note %}}
AWS provides a Fluent Bit image with plugins for both CloudWatch Logs and Kinesis Data Firehose. We recommend using Fluent Bit as your log router because it has a lower resource utilization rate than Fluentd. For more information, see [CloudWatch Logs for Fluent Bit](https://github.com/aws/amazon-cloudwatch-logs-for-fluent-bit) and [Amazon Kinesis Firehose for Fluent Bit.](https://github.com/aws/amazon-kinesis-firehose-for-fluent-bit)
{{% /notice %}}

![EnableFireLens](/images/ecs/taskdef/enable_firelens.png)

Scroll up to *Container Definitions* and check if **log_router** container was created. 
![CheckLogRouter](/images/ecs/taskdef/taskdef_added_log_router.png)

#### Log Configuration of log_router container
Click **log_router** container and scroll down to *Advanced container configuration – STORAGE AND LOGGING* to configure log. 
1. Log configuration: Uncheck **Auto-configure CloudWatch Logs**
2. Log driver and options:
![LogConfig](/images/ecs/taskdef/taskdef_log_router_logging.png)
- Log driver: **awslogs**
- Log options: Copy and paste is recommended.
  
|Key|Value|Input|
|------|---|---|
|awslogs-group|Value|`firelens-container`|
|awslogs-region|Value|`ap-northeast-2`|
|awslogs-stream-prefix|Value|`firelens`|
|`awslogs-create-group`|Value|`true`|

1. Scroll down to the end and click **Update**. 

### Add cats container
Come back to *Container Definitions* and click **Add container** to add **cats**.
![CatsTask](/images/ecs/taskdef/taskdef_cats_uri.png)
1. Configure **cats** container. 
- Container name: `cats`
- Image: your **cats** latest image URI 

{{% notice tip %}}
Open new browser tab and move to ECR. Select **cats** repository and click the button of **latest** tagged image. 
{{% /notice %}}
![CatsLatest](/images/ecs/taskdef/taskdef_cats_latest_image.png)
- Memory Limits - Hard limit 128
- Port mappings
    + Host port: 0
    + Container port: 80 (tcp)

#### Log Configuration of cats container
Scroll down to *Advanced container configuration – STORAGE AND LOGGING* and configure **cats** container logging.
1. Log configuration: Uncheck **Auto-configure Cloudwatch Logs.**
2. Log driver and options: 
![CatsLogConfig](/images/ecs/taskdef/taskdef_cats_log_config.png)
- Log driver: awsfirelens
- Log options

|Key|Value|Input|
|------|---|---|
|Name|Value|`cloudwatch`|
|`log_group_name`|Value|`ecs-demogo-log`|
|`log_stream_prefix`|Value|`from-fluent-bit`|
|`region`|Value|`ap-northeast-2`|
|`auto_create_group`|Value|`true`|

1. Click **Add** then the window closes. Check if **cats** container added. 
2. Click **Create**. 


{{% notice tip %}}
Or you can simply copy and paste the template below to create the same **cats** task definition via console, or saved to a file and used with the AWS CLI --cli-input-json option.
{{% /notice %}}

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