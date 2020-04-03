---
title: "컨테이너 인사이트"
weight: 41
---

{{% notice note %}}
CloudWatch Container Insights를 사용해 컨테이너식 애플리케이션 및 마이크로서비스의 지표 및 로그를 수집하고 집계하며 요약할 수 있습니다. 이 지표에는 CPU, 메모리, 디스크, 네트워크 같은 리소스 사용률이 포함되어 있습니다. 또한 Container Insights는 컨테이너 재시작 오류 같은 진단 정보를 제공하여 문제를 격리하고 신속하게 해결할 수 있도록 도와줍니다. 
{{% /notice %}}
<!---Container Insights에서 수집한 지표에 대해 CloudWatch 경보를 설정할 수도 있습니다--->
### Container Insights로 ECS 모니터링하기
1.	[Amazon CloudWatch](https://console.aws.amazon.com/cloudwatch)로 이동합니다.
2.	드롭다운에서 **Container Insights**를 선택합니다. CloudWatch가 ECS의 다양한 모니터링 지표들을 한 눈에 볼 수 있도록 자동 생성한 대시보드를 살펴봅니다. 
![InsightDashboard](../../../static/images/monitoring/container_insight_1.png)
3.	ECS Clusters, ECS Services, ECS Tasks들을 하나씩 살펴봅니다.  [지표별 상세 내용](https://docs.aws.amazon.com/ko_kr/AmazonCloudWatch/latest/monitoring/Container-Insights-metrics-ECS.html)을 더 알아봅니다. 
![ECSCluster](../../../static/images/monitoring/container_insight_2.png)
4. Container Insights는 ECS **클러스터** 뿐만 아니라 **태스크**의 지표들도 수집합니다. 어떤 태스크가 클러스터의 CPU, 메모리, 네트워크, 스토리지 등의 리소스를 얼마나 소모하는지 감시할 수 있습니다. 모니터링하고자 하는 태스크를 검색합니다. 
![ECSTasks](../../../static/images/monitoring/container_insight_3.png)
5. 두 개 이상의 컨테이너를 가진 태스크인 경우 **컨테이너별** Container Performance 지표들도 확인할 수 있습니다.
![ECSContainers](../../../static/images/monitoring/container_insights_4.png)
