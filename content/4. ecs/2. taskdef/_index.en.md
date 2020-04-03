---
date: 2020-03-28
title: "ECS Task Definition"
weight: 33
---

{{% notice note %}}
A task definition is required to run Docker containers in Amazon ECS. Here you will create **catsdef**, **dogsdef** Task Definitions, including **cats, dogs** docker images you created **3. Amazon ECR**. 
{{% /notice %}}

Some of the [parameters](https://docs.aws.amazon.com/ko_kr/AmazonECS/latest/developerguide/task_definition_parameters.html) you can specify in a task definition include: 
* The Docker image to use with each container in your task
* How much CPU and memory to use with each task or each container within a task
* The launch type to use, which determines the infrastructure on which your tasks are hosted
* The Docker networking mode to use for the containers in your task
* The logging configuration to use for your tasks…and more. 

![TaskDef](../../../static/images/ecs/ecs_taskdef.svg)

## What you will do
1. Create **web** task definition 
2. Create **catsdef** task definition 
3. Create **dogsdef** task definition 