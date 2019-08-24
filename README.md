# Docker-Cheatsheat
Some overview and basic commands for working with Docker

```
docker version
docker info
```
___

###### DOCKER ARCHITECTURE
runc: creates and run containers
shim: makes the container standalone
containerd: bridge b/w daemon & runc, A container supervisor(monitor)
daemon: an engine working behind the scene
___

###### IMAGES
-a package containing everythiing(code,sys. libraries,settings,tools etc)
-lightweight
-a blueprint of the app

Note: An image cannot be deleted if there is a container running from it
```
docker image ls ; docker images
docker image rm <image-name/id>
```
___

###### CONTAINERS
```
docker run -it <user/image> sh  [Ctrl P+Q (to detach)]
docker container ls ; docker ps
docker ps -a
docker exec -it <container name/id> sh
docker container stop <container name/id>
docker container start <container name/id>
docker container rm <container name/id> [must be stopped first OR ADD --force after name/id]
docker run -d <image>
docker ps -a | grep -i node [using regEX]
docker run -it --name=xyz <image> sh ; docker container run -it --name=xyz <image> sh
```

*-p[thePortYouWillUse:thePortAppReuqires]*
`docker run -d -p=9000:80`
___

###### DOCKERFILE
FROM -> Base Image
COPY . /usr/share/nginx/html -> Copy from current dir files to specified container directory
RUN -> Executes a command 
EXPOSE -> exposing the port for the container
ENTRYPOINT -> the command required to run the app

######An example of Dockerfile
*FROM nodejs:alpine
WORKDIR cd
EXPOSE 8080
ENTRYPOINT ['node','/app.js']*

```
docker build -t <image-name> .
docker tag nginx user/nginx:testv1
docker push user/nginx:testv1
```
___

###### EXTRAS
```
docker history <image>
docker inspect <image>
```
___

###### For BINDING -v [SystemDirectory:ContainerDirectiry]
`docker run -it --name abc -p 7400:80 -v ~/Desktop:/home/abc <image> sh`

