---
title: "도커 이미지"
weight: 22
---

{{% notice note %}}
이번 단계에서 실습자는 *Workstation* 인스턴스에 접속하여 Docker CLI를 이용해 **cats**와 **dogs** 도커 이미지를 빌드합니다.
{{% /notice %}}


1. [Amazon EC2](https://console.aws.amazon.com/ec2)로 이동하여 Instances 목록에서 *Workstation*를 선택하고 **IPv4 Public IP**를 복사합니다. 터미널을 열고 SSH 접속합니다.  
~~~
ssh -i [key pair name.pem] ec2-user@[Workstation Public IP]
~~~

{{% notice tips %}}
로컬 터미널을 사용하지 않아도 EC2에 웹 브라우저에서 간편하게 접속할 수 있습니다. Workstation을 클릭하고 Connect를 클릭하여 세 가지 **Connection method** 중 EC2 Instance Connect (browser-based SSH connection)를 선택합니다. User name은 root가 아닌 ec2-user를 사용하시는 것이 보안상 좋습니다.
{{% /notice %}}

![](/images/ecr/webssh.png)
![](/images/ecr/webssh2.png)

1. cats와 dogs의 Dockerfile 내용을 확인합니다. 도커는 Dockerfile을 읽어 자동으로 이미지를 빌드합니다. Dockerfile은 이미지 조립하기 위해 호출해야 하는 커맨드들을 담고 있습니다. 
~~~
cd catsdogs 
cd cats 
cat Dockerfile
~~~ 
cats 디렉토리의 Dockerfile은 **cats** 도커 이미지를 빌드하기 위해 필요합니다. 어떤 내용을 담고 있는지 리눅스 *cat* 명령어를 이용하여 확인합니다.
![CatImage](/images/ecr/build_cats_1.png)

{{% notice tips %}}
[Dockerfile](https://docs.docker.com/engine/reference/builder/#dockerfile-reference)의 **FROM**, **RUN** 등이 무엇을 의미하는지 더 알아봅니다. 예를 들어 **FROM** 명령어는 새 빌드 단계를 초기화하고 후속 명령어에 대한 기본 이미지를 설정합니다.
{{% /notice %}}

1. **cats**를 빌드합니다. 
~~~
docker build -t cats . 
~~~
![CatImageBuild](/images/ecr/build_cats_2.png)

4. **dogs**에서도 동일한 작업을 수행하기 위해 디렉토리를 이동합니다.
~~~
cd ..
cd dogs
cat Dockerfile 
~~~
마찬가지로 이 Dockerfile은 dogs 도커 이미지를 빌드하기 위해 필요합니다.

5. **dogs**를 빌드합니다.
~~~
docker build -t dogs .
~~~