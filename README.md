## Jenkins Docker Container

Reference: https://github.com/jenkinsci/docker

1. Get the project

```
git clone https://github.com/churrops/docker-jenkins.git
cd docker-jenkins/build
```

2. Make image build 
(This image exists in docker hub, but if you want to build, execute this step)

```
docker build -t churrops/jenkins:2.126-alpine -t churrops/jenkins:latest .
```

3. Deploy with Docker Compose

```
cd ..
docker-compose up -d
```

or execute directly

```
$ docker volume create jenkins_home

$ docker container run --name jenkins-master \
  -d --privileged=true -p 8080:8080 -p 50000:50000 -u 0 \
  -v jenkins_home:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock \
  churrops/jenkins:2.126-alpine

$ docker container exec -it jenkins-master cat /var/jenkins_home/secrets/initialAdminPassword
```

4. Open URL in your browser and use output value of InitialAdminPassword for unlocked Jenkins (only first time)

```
http://your-ip:8080
```

5. If is first time you install Jenkins, use output value of InicialAdminPassword for unlock Jenkis


## Destroing the Project

```
docker container rm -f jenkins-master
docker image rm -f churrops/jenkins:2.126-alpine
docker volume delete jenkins_home
```

Enjoy!
