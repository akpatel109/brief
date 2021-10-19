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
docker run ubuntu sleep 5 | run "sleep 5" command on ubuntu container
docker exec cont_name command | run command on running container
docker run -d image | run container in detached mode
docker attach contName/contId | attach to running container
docker run -it centos bash | run bash on centos container and directly opens terminal of container in interactive mode
