---
title: "Cluster IAM role"
weight: 32
---

{{% notice note %}}
ECS Instances need CloudWatch log access for FireLens to send the logs to CloudWatch Logs. You need to add **CloudWatchLogsFullAccess** to the role you created earlier. 
{{% /notice %}}

### Add IAM policy
1. Move to [IAM](https://console.aws.amazon.com/iam) roles.
2. Search the role you used earlier. If you created new one, then search `ecsInstancerole`
3. Select the role and click **Attach policies.**
![AttachePolicy](/images/ecs/cluster/attach_policy.png)
1. Filter **CloudWatchLogsFullAccess** policy and attach. 
![FilterPolicy](/images/ecs/cluster/filter_cw_logs_access.png)
1. Verify if **CloudWatchLogsFullAccess** is added correctly.
![AddedPolicy](/images/ecs/cluster/verify_attached_policy.png)