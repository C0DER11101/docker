# Pushing an image to [Docker Hub](https://hub.docker.com/)

So, I pulled an image from docker hub, `ubuntu:24.04`.

I created a container `nixZen`. I used the container for some work, created some files, folders and what not.
Now, I don't want to lose all the modifications that I made in it. I want to save these modifications into another image
so that when I pull that image from docker hub, I am able to get those modifications in the container(s) which I will
create from that image.

Now, in order to be able to pull the image, I must push it to docker hub and that to be able to push, I must have a repo in
docker hub.

Go to docker hub, and move to the `Repositories` tab:

<img src="https://github.com/C0DER11101/docker/blob/d0cker/dockerHub.png" width="60%" height="60%">

Some commands that one must know:

## `docker container commit`

* Usage: `docker container commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]`
* Aliases: `docker commit`
* Create a new image from a container's changes.

### `OPTIONS`

* Checkout <a href="https://docs.docker.com/reference/cli/docker/container/commit/#options">here</a>

## `docker image tag`

* Usage: `docker image tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]`
* Aliases: `docker tag`
* Create a tag `TARGET_IMAGE` that refers to `SOURCE_IMAGE`.

Once in the `Repository` tab, create a repository with any name.
**NOTE:** <em>You must be logged in first</em>

I created a repository:

<img src="https://github.com/C0DER11101/docker/blob/d0cker/repo.png" width="60%" height="60%">

Now that we have created a repo in our docker hub. We can move to use the aforementioned commands.

## First: Create an image from the container's changes

* Move to [Docker Desktop](https://www.docker.com/products/docker-desktop/) and copy the container ID of the desired container.

<img src="https://github.com/C0DER11101/docker/blob/d0cker/containerID.png" width="60%" height="60%">

```bash
$ docker container commit 1b91b45ad77f8e3a74bb52350a4fbf278888c780b5748e7398be6ecbf86de7bb testub:v0
```

Here `testub` is any name for the image that I want to create.

`v0` is any tag that I have given to the image.

## Second: Create a tag that refers to the newly created image

```bash
$ docker image tag testub:v0 zen11101/ubtrix:v0
```

We are creating a new tag `zen11101/ubtrix:v0` for the newly created image `testub:v0`.

`zen11101` is the username, `ubtrix` is the repository name.

## Push

```bash
$ docker image push zen11101/ubtrix
```

Now, that the image has been pushed into docker hub, I or anyone can pull it and create a container from it and that container will
contain all the modifications that I had made.

<p align="center">
&#9678; &#9678; &#9678;
</p>
