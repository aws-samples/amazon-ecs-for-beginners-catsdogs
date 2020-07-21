---
title: "Service Auto Scale"
weight: 51

---

{{% notice note %}}
You can use CloudWatch metrics and others to scale out your service (**add more tasks**) to deal with high demand at peak times, and to scale in your service (**run fewer tasks**) to reduce costs during periods of low utilization. In this lab, you will enable service auto scaling for service **web.**
{{% /notice %}}

![ServiceAutoScale](../../../static/images/autoscale/service_auto_scale.svg)

## What you will do
1. [Configure Service Auto Scale](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/ko/autoscale/service/config/)
2. [Service Load Test](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/ko/autoscale/service/loadtest/) 
3. [Monitoring](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/ko/autoscale/service/monitoring/)