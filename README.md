JenkinsCIWithDockerIntegration
=============================

# Why this image?
There already thousands of jenkins images, why you must make your own, come on ...

because i want to run docker in an docker container where jenkins is running. And i wanted full control :)

# How to use this?
Sample docker-compose.yml

````
version: '3.2'
services:
  jenkins:
    image: timoreymann/jenkins-ci-with-docker
    restart: always
    ports:
#    Port for web ui
      - 8080:8080
#    Port used by jenkins
      - 50000:50000
    volumes:
#     Jenkins data directory
      - jenkins_home:/var/jenkins_home
#    Link docker from host to container to reuse installed docker ;)
      - /var/run/docker.sock:/var/run/docker.sock
volumes:
#  Create docker volume for jenkins data previously mentioned in volumes
   jenkins_home:
     driver: local
````

## Further steps
Just open your web browser and follow the install guide. Nothing else is to do.

## Backup
To backup jenkins simply backup the docker volume.
