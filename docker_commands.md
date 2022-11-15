#IMAGES

**docker images** -> show you all images with details

**docker pull imageName:imageVersion** -> allow you to download images
**docker pull --platform platform imageName:imageVersion** -> allow you to download images by platform like linux/x86_64

**docker image rm imageName:imageVersion** -> allow you to remove images

#CONTAINERS
###CREATE
**docker create imageName:imageVersion** -> allow you to create a container, give you the container ID

**docker create --name customContainerName imageName:imageVersion** -> allow you to create a container with a customContainerName, give you the container ID

**docker create -pPORTPHYSICAL:PORTOFCONTAINER --name customContainerName imageName:imageVersion** -> allow you to create a container with custom port mapping, with a customContainerName, give you the container ID

**docker create -pPORTPHYSICAL:PORTOFCONTAINER --network networkName --name customContainerName imageName:imageVersion** -> allow you to create a container with custom port mapping, with a customContainerName and with one network, give you the container ID

###RUN
**docker run -pPORTPHYSICAL:PORTOFCONTAINER --network networkName --name customContainerName imageName:imageVersion -d** -> do all of before

###OTHERS
**docker start containerID** -> allow you to start one container by containerID or containerName

**docker stop containerID** -> allow you to stop one container by containerID or containerName

**docker rm containerID/containerName** -> allow you to remove one container by containerID or containerName

**docker ps** -> show you the active containers
**docker ps -a** -> show you all containers

**docker logs containerID/containerName** -> show you all logs of the container
**docker logs --follow containerID/containerName** -> show you all logs of the container

#NETWORK

**docker network create networkName** -> create a network

**docker network rm networkName** -> remove a network

**docker network ls** -> show you all networks created

#DOCKERFILE (Dockerfile)

**docker build -t imageName:imageTag route(for example: ./)** -> to create a image from dockerfile
<pre>
FROM imageName:imageVersion -> image to create our container
RUN mkdir -p folderOfApp (for example: /home/app) -> commands in the image that we want to do
COPY folderOfSourceCode folderOfApp (for example: ./ /home/app) -> command for example to copy the source code to our container
EXPOSE portOfApp -> physical port mapped
CMD ["java", "-jar","/home/app/Main.jar"] -> command to run our app 
</pre>

#DOCKER COMPOSE (docker-compose.yml)

**docker compose up** -> to create the containers with compose
**docker compose down** -> to remove the containers with compose
<pre>
version: composeVersion (for example: "3.9")
services: -> allow you to describe how will be to the new container
    containerName: (for example: javaApp)
        build: . -> path of the Dockerfile of javaApp
        ports:
            - "3000:3000" -> "hostPort:containerPort"
        links:
            - nameOfTheOtherContainerToLinkLikeANetwork
        MySql:
            image: imageName (for example: mysql:latest)
        ports:
            - "3306:3306" -> "hostPort:containerPort"
        enviroment: -> enviroment variables
            - var1=0 (for example: root_user=admin)
            - var2=admin (for example: password=admin)
</pre>



