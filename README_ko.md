# DemoGo - Cats and Dogs

## 사랑과 행복을 찾아서
![catsdogs](static/images/intro/catsdogs.svg)
이 워크샵은 Amazon ECS, Fargate 또는 도커 컨테이너의 워크플로우에 친숙하지 않은 분들도 쉽게 따라할 수 있습니다.

## Amazon ECS
Amazon Elastic Container Service(Amazon ECS)는 **완전관리형 컨테이너 오케스트레이션 서비스**입니다. 기본적으로 Amazon Route 53, Secrets Manager, AWS Identity and Access Management(IAM), Amazon CloudWatch 등의 다른 서비스와 통합을 통해 컨테이너 배포 및 확장을 위한 익숙한 환경을 제공할 수 있습니다. **다른 AWS 서비스와의 신속한 통합**을 통해 ECS에 새로운 기능을 추가할 수도 있습니다. ECS를 통해 애플리케이션에서 **Amazon EC2** 및 **AWS Fargate**를 스팟 및 온디맨드 요금 옵션과 조합하여 유연하게 사용할 수도 있습니다.

## 실습 목적
- 이 워크샵을 통해 Amazon ECS의 **기본 개념**과 **주요 구성 요소**들을 이해합니다.
- Amazon ECS 관리에 활용할 수 있는 **유용한 도구들**을 실습합니다.  

## 다루는 AWS 서비스
* Amazon Elastic Container Service (ECS)
* Amazon Elastic Container Resistry (ECR)
* AWS Fargate
* AWS FireLens
* Amazon CloudWatch
* Auto Scaling
* AWS Identity and Access Management (IAM)
* Amazon CloudFormation
* Amazon EC2
* Amazon Application Load Balancer (ALB)

## 전체 아키텍처
![Architecture](static/images/intro/architecture.svg)

## 실습 범위
* AWS CloudFormation를 이용하여 **실습에 필요한 리소스**를 자동으로 배포
* Amazon ECR에서 **도커 이미지** **관리**
* Amazon ECS **클러스터**, **작업 정의**, **서비스** 생성
* 각 서비스별 **EC2**와 **Fargate** 중 알맞은 **시작 유형** 선택
* 컨테이너 웹 애플리케이션 **cats and dogs**을 Application Load Balancer 경로 기반으로 구성
* **Container Insights**로 Amazon ECS **모니터링**
* **AWS FireLens**과 **CloudWatch Logs**로 **컨테이너 로그 수집**
* Amazon ECS **서비스 오토스케일링**
* Amazon ECS **클러스터 오토스케일링**

## 다음 링크에서 계속합니다. 
[English]
http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/en/

[Korean]
http://ecs.catsdogs.kr.s3-website.ap-northeast-2.amazonaws.com/ko/

## 컨텐츠 기여
버그 보고, 새로운 기능, 오탈자 정정이나 문서 추가 등 프로젝트에 기여하고 싶다면 [가이드 라인](/CONTRIBUTING.md)을 참고하여 이슈 또는 pull request를 제출해 주세요. 저희가 효과적으로 대응할 수 있도록 관련한 정보를 정확히 포함해주시면 감사하겠습니다. 저희는 커뮤니티의 피드백과 기여를 소중하게 생각합니다.

## 라이센스
이 라이브러리는 LICENSE 파일에 명시되어 있는 바와 같이 MIT-0 라이센스를 따릅니다. 
