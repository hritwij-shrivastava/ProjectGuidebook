# Docker Cheat Sheet

This README provides a quick reference for common Docker commands and operations. Docker is a powerful containerization tool that allows you to package and run applications and services in isolated environments called containers. Here are some essential Docker commands and tasks:

## Check Docker Version
To verify the installed Docker version, use one of the following commands:
```bash
docker version
# or
docker -v
```

## Docker Hub
Docker Hub is a cloud-based registry where you can find and share container images. Visit [Docker Hub](https://hub.docker.com/) to explore available images.

## List Docker Images
View all Docker images currently present on your system:
```bash
docker images
# or
docker image ls
```

## Pull Docker Images
Download Docker images from a registry or repository. For example, to pull the Python image:
```bash
docker pull python
```

## Search for Docker Images
Search for Docker images available on Docker Hub or other registries:
```bash
docker search MySQL
```

## Start a Docker Container
Run a Docker container based on an image. For example, to start a Python container:
```bash
docker run python
```

## List All Containers
Display a list of all Docker containers, including stopped ones:
```bash
docker ps -a
```

## Delete a Docker Container
Remove a specific Docker container using its container ID or name:
```bash
docker rm 822daa8c484f
```

## Delete All Containers
Forcefully remove all Docker containers:
```bash
docker rm -f $(docker ps -a -q)
```

## Delete a Docker Image
Delete a specific Docker image using its image ID or name:
```bash
docker image rm 822daa8c484f
```

## Delete All Unused Resources
Remove all unused Docker resources, including containers and images:
```bash
docker system prune -a
```

## Save a Docker Image
Export a Docker image to a tarball file (e.g., `ubuntu-node-17.tar` or `biovocalary-docker.tar`):
```bash
docker save -o D:\ubuntu-node-17.tar ubuntu-node-17
# or
docker save -o ./biovocalary-docker.tar biovocalary-docker
```

## Load a Docker Image
Import a Docker image from a tarball file:
```bash
docker load -i ubuntu-node-17.tar
```

## Build a Docker Image
Create a Docker image using a Dockerfile and assign it a tag (e.g., `biovocalary-docker`):
```bash
docker build -t biovocalary-docker .
```

## Run a Docker Container with Port Mapping
Start a Docker container with port mapping and a name (e.g., `bioapp`):
```bash
docker run -p 8000:9000 -d --name bioapp biovocalary-docker
```

## Interactive Mode in a Docker Container
Access an interactive shell within a running Docker container:
```bash
docker exec -it bioapp bash
# or
docker run -it bioapp /bin/bash
# or
docker run -ti 74f2314a03de bash
```

## Stop a Running Docker Container
Gracefully stop a running Docker container by name (e.g., `bioapp`):
```bash
docker stop bioapp
```

## Run a Docker Container with an Environment File
Start a Docker container with environment variables from a file (e.g., `.env`):
```bash
docker run --env-file ./.env -p 8000:9000 -d --name bioapp biovocalary-docker
```

Feel free to customize and adapt these commands to your specific Docker use cases. Docker is a versatile tool for managing containers, and these commands will help you get started with common tasks.