# Continuous Integration for basic web project with jenkins

### basic web:
![](https://raw.githubusercontent.com/toanduc0671/NguyenDucToan-week5/main/images/basicweb.png)

## build jenkins with docker

```bash
$ docker run 
-v /usr/bin/docker:/usr/bin/docker 
-v /home/jenkins/jenkins_data:/var/jenkins_home  
-p 8080:8080  --user 1001:998 --name jenkins-server 
-d jenkins/jenkins:lts
```

![](https://raw.githubusercontent.com/toanduc0671/NguyenDucToan-week5/main/images/startjenkins.png)

### add jenkinsfile to github main branch:

````jenkinsfile
pipeline {

  agent none

  stages {
    stage("Test") {
      agent {
          docker {
            image 'python:3.8-slim-buster'
            args '-u 0:0'
          }
      }
      steps {
        sh "pip install poetry"
        sh "poetry install"
        sh "poetry run pytest"
      }
    }

  post {
    success {
      echo "SUCCESSFUL"
    }
    failure {
      echo "FAILED"
    }
  }
}
````

