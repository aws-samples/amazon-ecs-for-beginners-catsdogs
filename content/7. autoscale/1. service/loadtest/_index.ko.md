---
title: "서비스 부하 테스트"
weight: 50
---

{{% notice note %}}
**Workstation** 인스턴스에 접속하여 부하 테스트를 위한 스크립트를 작성합니다. 이를 이용하여 서비스 **web**으로 부하 테스트를 수행합니다. 
{{% /notice %}}

1. **Workstation** 인스턴스에 접속합니다.
~~~
ssh -i [key pair name.pem] ec2-user@[Workstation Public IP]
~~~

2. **Workstation** 인스턴스에서 예시로 넣어둔 **service_loadtest.sh**의 내용을 리눅스 *cat* 명령어를 이용해 살펴봅니다.
![LoadTestScript](/images/autoscale/service_load_test_script.png)


3. vi 편집기를 이용하여 **service_loadtest_실습자이름.sh**을 작성합니다. [EC2 Load Balancers](https://ap-northeast-2.console.aws.amazon.com/ec2/v2/home?region=ap-northeast-2#LoadBalancers:sort=loadBalancerName)로 이동하여 **demogo-alb**의 DNS 이름을 메모장에 복사합니다. 
![CopyALBDNS](/images/autoscale/copy_alb_dns.png)

~~~
vi service_loadtest_[실습자이름].sh
~~~

~~~
ab -c 200 -n 200 -t 30 [실습자의 ALB DNS name] + / 
~~~

* /를 붙이는 이유는 서비스 **web**이 / 경로를 가지기 때문입니다.
* :wq!를 눌러 vi 편집을 마칩니다.

1. **service_loadtest_실습자이름.sh** 스크립트를 실행하기 위해 권한을 부여한 후 부하 테스트를 수행합니다. 연속으로 3분 이상 실행합니다. 다음 단계에서 모니터링합니다. 

~~~
chmod 755 service_loadtest_[실습자 이름].sh
~~~

~~~
./service_loadtest_[실습자이름].sh
~~~
![PerformLoadTest](/images/autoscale/perform_service_load_test.png)