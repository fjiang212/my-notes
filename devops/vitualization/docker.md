# Concepts
* An **image** is an executable package that includes everything needed to run an application–the code, a runtime, libraries, environment variables, and configuration files
* A **container** is a runtime instance of an image–what the image becomes in memory when executed (that is, an image with state, or a user process)

# Architecture
## Overview 
https://docs.docker.com/engine/docker-overview/

![alt text](images/architecture.svg)

## Storage 
https://docs.docker.com/storage/
* Volumes are stored in a part of the host filesystem which is managed by Docker (/var/lib/docker/volumes/ on Linux). Non-Docker processes should not modify this part of the filesystem. Volumes are the best way to persist data in Docker.
* Bind mounts may be stored anywhere on the host system. They may even be important system files or directories. Non-Docker processes on the Docker host or a Docker container can modify them at any time.
* tmpfs mounts are stored in the host system’s memory only, and are never written to the host system’s filesystem.

![alt text](images/types-of-mounts.png)
# Install & Config
## Installation
https://docs.docker.com/install/linux/docker-ce/centos/

## Configuration
* Config docker service to use insecure registry
https://github.com/Juniper/contrail-docker/wiki/Configure-docker-service-to-use-insecure-registry
```
Edit the file /etc/docker/daemon.json
{
  "insecure-registries" : ["10.84.34.155:5000"]
}
```
* Get an Oauth token to Artifactory for future interactions
```
curl -k -u username:password "https://artifactory:8444/artifactory/api/docker/docker-dev-local2/v1/auth" > ~/.dockercfg
You could check the results using:
cat .dockercfg
{
"https://artifactory:8444" : {
"auth" : "longauthtokenasgeneratedbyartifactoryhere",
"email" : "your.email@test.com"
}
```
# Docker Commands
* Docker information
```
docker info #view details about your docker installation
```
* Set up docker daemon proxy

https://docs.docker.com/config/daemon/systemd/#httphttps-proxy

* Docker basic commands
```
docker build -t friendlyname .  # Create image using this directory's Dockerfile
docker run -p 4000:80 friendlyname  # Run "friendlyname" mapping port 4000 to 80
docker run -d -p 4000:80 friendlyname         # Same thing, but in detached mode
docker container ls                                # List all running containers
docker container ls -a             # List all containers, even those not running
docker container stop <hash>           # Gracefully stop the specified container
docker container kill <hash>         # Force shutdown of the specified container
docker container rm <hash>        # Remove specified container from this machine
docker container rm $(docker container ls -a -q)         # Remove all containers
docker image ls -a                             # List all images on this machine
docker image rm <image id>            # Remove specified image from this machine
docker image rm $(docker image ls -a -q)   # Remove all images from this machine
docker login             # Log in this CLI session using your Docker credentials
docker tag <image> username/repository:tag  # Tag <image> for upload to registry
docker push username/repository:tag            # Upload tagged image to registry
docker run username/repository:tag                   # Run image from a registry
```

* Docker cleanup
docker system prune will delete ALL dangling data (i.e. In order: containers stopped, volumes without containers and images with no containers). Even unused data, with -a option.
You also have:
```
docker container prune
docker image prune
docker network prune
docker volume prune
```
For unused images, use docker image prune -a (for removing dangling and ununsed images). Warning: 'unused' means "images not referenced by any container": be careful before using -a.

* Attach to running docker container
```
$ sudo docker exec -i -t 665b4a1e17b6 /bin/bash #by ID
or
$ sudo docker exec -i -t loving_heisenberg /bin/bash #by Name
```

* Run docker with enviroment varialbe and binding volume
```
docker run -it \
-e SAMPLE_SEVER='test.sample.com' \
-e SAMPLE_USER='AAAA' \
-e SAMPLE_PASSWORD='AAAA' \
-v /home/vagrant/certs/non-production:/usr/share/sample/certs
sample:latest bash 

```
# Develop images
## Guide and reference
* [Dockerfile Reference](https://docs.docker.com/engine/reference/builder/#escape)
* https://docs.openshift.com/container-platform/3.7/creating_images/guidelines.html
