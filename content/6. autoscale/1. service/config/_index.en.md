---
title: "Configure Service Auto Scale"
weight: 49
---

1. Move to [Amazon ECS](https://console.aws.amazon.com/ecs) and select **DEMOGO-ECS** cluster.
2. Select **web** on **Services** tab and click **Update**
![WebUpdate](../../../../static/images/autoscale/web_update.svg)
3. Step 1: Configure service - **Skip**
4. Step 2: Configure network - **Skip**
5. Step 3: Set Auto Scaling
* Service Auto Scaling: **Configure Service Auto Scaling to adjust your services' desired count**
* Minimum number of tasks: `2`
* Maximum number of tasks: `8` 
![SetAutoScaling](../../../../static/images/autoscale/set_auto_scaling.png)
1. Automatic task scaling policies – click **Add scaling policy**
2. Configure **Add policy**.
![TargetTracking](../../../../static/images/autoscale/target_tracking.png)
* Scaling policy type: **Target tracking**
* Policy name: `ALB-request-tracking`
* ECS service metric: **ALBRequestCountPerTarget**

{{% notice tip %}}
You can refer the recent trends from the graphs, based on the metrics you choose. 
{{% /notice %}}
* Target value: `4000` 
* Scale-out cooldown period: `10` seconds 

{{% notice note %}}
We are setting low numbers with an intention to verify the result fast.
{{% /notice %}}

8. **Next step** and click **Update Service**. 

