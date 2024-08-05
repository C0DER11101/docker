# <ins>The very basics of docker(The absolute basics: not getting into layers, digests, etc..)</ins>

# `docker image pull`

* Download an image from a registry.
* Usage: `docker image pull [OPTIONS] NAME[:TAG|@DIGEST]`
* Alias: `docker pull`
* If no `TAG` is provided, then Docker Engine uses `:latest` tag as default.

## OPTIONS

* Checkout <a href="https://docs.docker.com/reference/cli/docker/image/pull/#options">here</a>

## Example

```bash
$ docker image pull ubuntu
Using default tag: latest
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest
```

# `docker container run`

* Create and run a new container from an image
* Usage: `docker container run [OPTIONS] IMAGE [COMMAND] [ARG...]`
* Alias: `docker run`
* `docker run` command runs a command in a new container, pulling the image if needed and starting the container.
* Use `docker ps -a` to view a list of all containers, including those that are stopped.

## OPTIONS

* Checkout <a href="https://docs.docker.com/reference/cli/docker/container/run/#options">here</a>

## Example

```bash
$ docker run --name nixZen -d -i ubuntu
669381c64e324f7f0770c38b7747766e87ac31961509bda58e5b4d10949cd7e7
$ docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
669381c64e32   ubuntu    "/bin/bash"   6 seconds ago   Up 4 seconds             nixZen
```

### Image

<img src="https://github.com/C0DER11101/docker/blob/d0cker/ubuntuImage.png" width="50%" height="50%">

### Container

<img src="https://github.com/C0DER11101/docker/blob/d0cker/container1.png" width="50%" height="50%">

# `docker container exec`

* Execute a command in a running container.
* Usage: `docker container exec [OPTIONS] CONTAINER COMMAND [ARG...]`
* Alias: `docker exec`
* The command specified with `docker exec` only runs while the container's primary process(PID 1) is running, and it isn't restarted if the container is restarted.
* The command must be an executable. A chained or quoted command doesn't work.

## OPTIONS

* Checkout <a href="https://docs.docker.com/reference/cli/docker/container/exec/#options">here</a>

## Example

```bash
$ docker exec -i -t nixZen bash
```

The options `-i` and `-t` can also be written as `-it`.

# `docker container stop`

* Stop one or more running containers.
* Usage: `docker container stop [OPTIONS] CONTAINER [CONTAINER...]`
* Alias: `docker stop`

## OPTIONS

* Checkout <a href="https://docs.docker.com/reference/cli/docker/container/stop/#options">here</a>

## Example

```bash
$ docker stop nixZen
$ docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS                        PORTS     NAMES
669381c64e32   ubuntu    "/bin/bash"   22 minutes ago   Exited (137) 24 seconds ago             nixZen
```

### Container exited

<img src="https://github.com/C0DER11101/docker/blob/d0cker/containerExited.png" width="50%" height="50%">

# `docker container start`

* Start one or more stopped containers.
* Usage: `docker container start [OPTIONS] CONTAINER [CONTAINER]...`
* Alias: `docker start`

## OPTIONS

* Checkout <a href="https://docs.docker.com/reference/cli/docker/container/start/#options">here</a>

## Example

```bash
$ docker container start nixZen
$ docker ps -a
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
669381c64e32   ubuntu    "/bin/bash"   27 minutes ago   Up 29 seconds             nixZen
```

### Container started

<img src="https://github.com/C0DER11101/docker/blob/d0cker/containerStarted.png" width="50%" height="50%">

# `docker container rm`

* Remove one or more containers.
* Usage: `docker container rm [OPTIONS] CONTAINER [CONTAINER...]`
* Alias: `docker container remove` `docker rm`

## OPTIONS

* Checkout <a href="https://docs.docker.com/reference/cli/docker/container/rm/#options">here</a>

## Example

```bash
$ docker container rm nixZen
```

# `docker image rm`

* Remove one or more images.
* Usage: `docker image rm [OPTIONS] IMAGE [IMAGE...]`
* Alias: `docker image remove` `docker rmi`
* Removes (and un-tags) one or more images from the host node.
* If an image has multiple tags, using this command with the tag as a parameter only removes the tag.
* If the tag is the only one for the image, both the image and the tag are removed.

## OPTIONS

* Checkout <a href="https://docs.docker.com/reference/cli/docker/image/rm/#options">here</a>

## Example

```bash
$ docker image rm ubuntu
Untagged: ubuntu:latest
Untagged: ubuntu@sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Deleted: sha256:35a88802559dd2077e584394471ddaa1a2c5bfd16893b829ea57619301eb3908
Deleted: sha256:a30a5965a4f7d9d5ff76a46eb8939f58e95be844de1ac4a4b452d5d31158fdea
```

Here, we didn't use any tag as this ubuntu was already the `latest` one. But if we pull some version of ubuntu(like 24.04, etc..) then we must specify the tag as well.

We could have also written the above command with the tag:

```bash
$ docker image rm ubuntu:latest
Untagged: ubuntu:latest
Untagged: ubuntu@sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Deleted: sha256:35a88802559dd2077e584394471ddaa1a2c5bfd16893b829ea57619301eb3908
Deleted: sha256:a30a5965a4f7d9d5ff76a46eb8939f58e95be844de1ac4a4b452d5d31158fdea
```

# `docker image ls`

* List images
* Usage: `docker image ls [OPTIONS] [REPOSITORY[:TAG]]`
* Alias: `docker image list` `docker images`
* An image will be listed more than once if it has multiple repository names or tags. This single image (identifiable by its matching `IMAGE ID`) uses up the `SIZE` listed only once.

## OPTIONS

* Checkout <a href="https://docs.docker.com/reference/cli/docker/image/ls/#options">here</a>

<p align="center">
&#9678; &#9678; &#9678;
</p>
