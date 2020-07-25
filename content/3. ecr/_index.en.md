---
title: "Amazon ECR"
weight: 20
pre: "<b>3. </b>"
---

{{% notice note %}}
Amazon Elastic Container Registry (ECR) is integrated with Amazon ECS allowing you to easily store, run, and manage container images for applications running on Amazon ECS. All you need to do is specify the Amazon ECR repository in your Task Definition and Amazon ECS will retrieve the appropriate images for your applications.
{{% /notice %}}

## What is Amazon ECR
![ECR](/images/ecr/ecr_1.svg)

## What you will do
![ECRLab](/images/ecr/ecr_2.svg)

1. Create Amazon ECR **cats, dogs** repositories. 
2. SSH to *Workstation* instance to build and tag **cats, dogs** docker images. 
3. Push the images to Amazon ECR. 
