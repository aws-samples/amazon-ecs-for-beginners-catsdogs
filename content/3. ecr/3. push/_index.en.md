---
title: "Tag and Push to ECR"
weight: 23
---

{{% notice note %}}
You will tag the images you built earlier and push to **cats**, **dogs** ECR repositories.
{{% /notice %}}

1. In order to tag and push images, *Workstation* has to login to ECR by docker login. 
~~~
sudo aws ecr get-login --no-include-email --region ap-northeast-2
~~~
![ECRlogin](/images/ecr/ecr_login_1.png)
~~~
sudo su
$(aws ecr get-login --no-include-email --region ap-northeast-2)
~~~
![ECRloginSucceeded](/images/ecr/ecr_login_2.png)
Check *Login Succeeded* message. 

2. Tag and push **cats**, **dogs** images to each ECR. You may refer to *View push command*.
![ECRCommands](/images/ecr/ecr_view_commands.png)

3. Copy the **tag**, **push** commands and run. 

{{% notice warning %}}
You must replace with your own cats, dog Repository URI. 
{{% /notice %}}

![ECRTagPush](/images/ecr/ecr_view_commands_2.png)
~~~
docker tag cats:latest cats Repository URI:latest 
~~~
~~~
docker push cats Repository URI:latest 
~~~
![CatsPush](/images/ecr/ecr_push_1.png)

4. Tag and push **dogs** too. 
~~~
docker tag dogs:latest dogs Repository URI:latest 
~~~
~~~
docker push dogs Repository URI:latest
~~~
![DogsPush](/images/ecr/ecr_push_dogs.png)

5. Check whether the images are pushed into ECR successfully.
![CatsPushed](/images/ecr/ecr_cats_latest.png)
![DogsPushed](/images/ecr/ecr_dogs_latest.png)
