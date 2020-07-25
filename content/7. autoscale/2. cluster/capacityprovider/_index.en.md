---
title: "Create Capacity Provider"
weight: 55
---
1)	Go to [ECS](https://console.aws.amazon.com/ecs) Cluster and select **DEMOGO-ECS** and select **Capacity Providers** tab. Click **Create**.
![CreateCapacityProvider](/images/autoscale/cluster/create_capacity_provider&#32;(1).png)
2)	Create Capacity Provider
![CreateACapacityProvider](/images/autoscale/cluster/create_capacity_provider_2.png)
* Capacity provider name: `demogo-capacity-provider` 
* Auto Scaling group: EC2ContainerService-[your cluster name]-EcsInstanceAsg
  * This ASG was auto-created when you create your cluster.
* Managed scaling: **Disabled** 
  * You will manually configure on the next step.
* Target capacity %: `100` 
* Managed termination protection: **Disabled**

{{% notice note %}}
When managed scaling is enabled, the target capacity value is used as the target value for the CloudWatch metric used in the Amazon ECS-managed target tracking scaling policy. For example, a value of 100 will result in the Amazon EC2 instances in your Auto Scaling group being completely utilized.
{{% /notice %}}

3)	Update cluster
Default capacity provider strategy: Select ‘demogo-capacity-provider’ from the dropdown.
![UpdateCluster](/images/autoscale/cluster/update_cluster.png)