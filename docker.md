# Docker commands
command | description
--------|-------------
docker run imageName | #to run any image
docker ps | #shows status of running containers
docker ps -a | shows all containers
docker stop containerId/ContainerName | to stop any container
docker rm containerName | remove the container permanently, returns container name on successful
docker images | list images
docker rmi imageName | remove image, no container should be running that image
docker pull imageName | to pull the image
docker pull image:version
docker run ubuntu sleep 5 | run "sleep 5" command on ubuntu container
docker exec cont_name command | run command on running container
docker run -d image | run container in detached mode
docker attach contName/contId | attach to running container
docker run -it centos bash | run bash on centos container and directly opens terminal of container in interactive mode
docker run -v d:/imagedata:/var/lib/mysql mysql | to mount the data directory of container to local space
docker inspect containerName | returns details about container
docker logs containerName | to see stdout of container
docker run -p 8080:8080 -v /root/jenkins-data:/var/jenkins_home -u root jenkins | runs jenkins with local space mounting with root user
docker history imageName | see execution history of any image, shows dockerfile build command execution history

# DockerFile
- Every dockerfile is based on another image. Either an OS or another image. and then we do some other operations(Installation of dependencies, copy-paste etc...) based on our needs on that image.<br>
- dockerfile starts with <b>FROM</b> which provides base image to start with.
- It follows layered architecture. starts with the first line from dockerfile and on each line execution , it creates another layer on top of last layer. think of it as interpreted language execution.
- all the layers are cached. so in case of failure, it reads the successfull layers from cache when executed again. Same happens if the dockerfile is extended.

## sample docker file
```
FROM ubuntu

RUN apt-get update
RUN apt-get install python

RUN pip install flask
RUN pip install flask-mysql

COPY . /opt/source-code

ENTRYPOINT FLASK_APP=/opt/source-code/app.py flask run
```
## docker build command
```
docker build -t accountName/imageName
```
## push image to dockerhub public registry
```
docker push accountName/imageName
```
