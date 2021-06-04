## build jenkins with docker

``` bash
$ docker run 
-v /usr/bin/docker:/usr/bin/docker 
-v /home/jenkins/jenkins_data:/var/jenkins_home  
-p 8080:8080  --user 1001:998 --name jenkins-server 
-d jenkins/jenkins:lts
```

