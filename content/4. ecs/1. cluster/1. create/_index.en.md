---
title: "Create cluster"
weight: 31
---

{{% notice note %}}
You will create EC2 Linux cluster **DEMOGO-ECS** and an IAM role **ecsInstanceRole** for the cluster instances.
{{% /notice %}}

1. Move to [Amazon ECS](https://console.aws.amazon.com/ecs). If it is your first time to run ECS, you will see **Get started** screen. Please ignore and directly head to Amazon ECS Clusters and click **Create Cluster.**
![CreateCluster](/images/ecs/cluster/ecs_cluster_1.png)
2)	Step 1: Select cluster template – Select **EC2 Linux + Networking**.
![SelectClusterTemplate](/images/ecs/cluster/select_linux.png)
3)	Step 2: Configure cluster	
![ConfigureCluster](/images/ecs/cluster/create_demogo_ecs.png)
- Cluster name: `DEMOGO-ECS`
- Instance Configuration    
    + Provisioning model: On-Demand Instance
    + EC2 Instance type: m5.large
    + Number of instances: `2` 
    + EC2 AMI id: Amazon Linux 2 AMI
    + EBS storage: 22
    + Key pair: Choose your key pair. 
4. Networking
![ConfigureNetwork](/images/ecs/cluster/cluster_network.png)
+ VPC: **DemoGoECSVPC (10.0.0.0/16)**
+ Subnets: **Private subnet 1,2 (10.0.3.0/24, 10.0.4.0/24)**
+ Security Group: **ecs-demogo-ECSInstanceSG**

5. Container instance IAM role: Select **Create new role**. It automatically creates a role named **ecsInstanceRole.**  
![IAMrole](/images/ecs/cluster/cluster_iam_role.png)

{{% notice info %}}
If you created **ecsInstanceRole** before, select it. You will add more permission in the next step. However, if you should not change ecsInstanceRole for any reason, please create another IAM role for this workshop.
{{% /notice %}}

6. CloudWatch Container Insight: check **Enable Container Insights** and click **Create.**
![ContainerInsight](/images/ecs/cluster/enable_container_insights.png)