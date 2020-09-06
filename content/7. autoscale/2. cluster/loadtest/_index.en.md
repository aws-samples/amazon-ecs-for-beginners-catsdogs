---
title: "Cluster Load Test"
weight: 57
---

1.	SSH to your **Workstation** EC2 instance.
~~~
ssh -i [key pair name.pem] ec2-user@[Workstation Public IP]
~~~

2.  Check **cluster_loadtest.sh** example. 
![ClusterScript](/images/autoscale/cluster/cluster_load_test_1.png)
~~~
cat cluster_loadtest.sh
~~~

3. Create **cluster_loadtest_YourName.sh** using vi editor. Use your **demogo-alb** DNS name. Change the permission to execute. 

~~~
vi cluster_loadtest_[Your Name].sh
~~~

~~~
ab -c 800 -n 800 -t 10 [Your ALB DNS name] + /
ab -c 800 -n 800 -t 10 [Your ALB DNS name] + /cats
ab -c 800 -n 800 -t 10 [Your ALB DNS name] + /dogs
~~~

* Type :wq! to finish editing.

~~~
chmod 755 cluster_loadtest_[Your Name].sh
~~~

1. Run **cluster_loadtest.sh** in serial. At least 3 minutes.  


~~~ 
./cluster_loadtest_[Your Name].sh 
~~~
![ClusterLoadTest](/images/autoscale/cluster/cluster_load_test_2.png)