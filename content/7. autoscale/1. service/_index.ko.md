---
title: "서비스 오토스케일링"
weight: 51

---

{{% notice note %}}
Amazon ECS는 수요에 맞게 서비스를 스케일 아웃(태스크 수를 추가)하거나 사용량이 적은 때에는 스케일 인(태스크 수를 감소)하여 자동으로 조정할 수 있습니다. 본 실습에서는 세 가지 서비스 중 **web**에 **서비스 오토스케일링**을 설정하여 테스트합니다.
{{% /notice %}}

![ServiceAutoScale](/images/autoscale/service_auto_scale.svg)

## 실습 순서
1. [서비스 오토스케일링 구성](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/ko/autoscale/service/config/)
2. [서비스 web 부하 테스트](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/ko/autoscale/service/loadtest/)
3. [결과 확인](http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/ko/autoscale/service/monitoring/)