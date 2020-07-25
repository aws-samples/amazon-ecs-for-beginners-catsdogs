---
date: 2020-03-28
title: "EC2 and Fargate"
weight: 2
---

{{% notice note %}}
You can host your cluster on a **serverless** infrastructure that is managed by Amazon ECS by launching your services or tasks using the **Fargate launch type**. AWS Fargate **removes** the need to choose server types, decide when to scale your clusters, or optimize cluster packing.  In this lab, you will have mixture **both** of EC2 and Fargate on a single EC2 cluster as an example. You can choose better fit for each workload. 
{{% /notice %}}

For instance, if you require greater control of your EC2 instances to support compliance and governance requirements or broader customization options, then use EC2. You should use EC2 for GPU workloads, which are not supported on Fargate today. If not, you choose [AWS Fargate](https://docs.aws.amazon.com/ko_kr/AmazonECS/latest/developerguide/AWS_Fargate.html) to launch the containers without having to provision or manage EC2 instances. Please visit [here](https://docs.aws.amazon.com/ko_kr/AmazonECS/latest/developerguide/application_architecture.html) to learn more how you architect your application on Amazon ECS depends on several factors, with the launch type you are using. 

![ECS](/images/intro/ec2fargate.svg)


**Cats and dogs** application consists of three services: **web**, **cats** and **dogs**. In this lab, **web** and **cats** uses *Amazon EC2* launch type and **dogs** uses *AWS Fargate* type on a single cluster **DEMOGO-ECS**.   

![MixedArchitecture](/images/intro/mixed_architecture.svg)

1. **Web** is main web page accessible by ALB's DNS name. Click **I♥Cats** and **I♥Dogs**. You will be redirected to each service **cats** and **dogs**.
2. **Cats**, EC2 task, randomly shows cats pictures whenever you refresh the web page.
3. **Dogs**, Fargate task, randomly shows dogs pictures whenever you refresh.