## Links

Documentation

https://docs.docker.com/engine/understanding-docker/

Docker Hub

https://hub.docker.com/

Install Docker

https://docs.docker.com/engine/installation/linux/ubuntulinux/

Install Docker Compose

https://github.com/docker/compose/releases

## Playing with Busybox

Show Docker version

    docker version

Pull the busybox image from the Docker registry

    docker pull busybox

List docker images

    docker images

Run a Docker container based on busybox image

    docker run busybox

Provide a command to busybox

    docker run busybox echo "hello from busybox"

Shows also containers that are currently running

    docker ps

Shows all containers that we ran

    docker ps -a

Run a busybox container interactively

    docker run -it busybox sh

Automatically remove the container when it exits

    docker run -it --rm busybox sh

Delete a bunch of containers in one go

    docker rm $(docker ps -a -q -f status=exited)

Run a static web site in detached mode

    docker run -d -P --name static-site prakhar1989/static-site

Show exposed ports

    docker port static-site

Specify a custom port

    docker run -p 8888:80 prakhar1989/static-site

## Docker Images

Pull a specific version of `ubuntu` image

    docker pull ubuntu:14.04

## Docker Networks

List networks

    docker network ls

Create our own network

    docker network create foobar

Inspect the foobar network

    docker network inspect foobar

