# Creating a container

## `docker container create`

* Command: `docker container create [OPTIONS] IMAGE [COMMAND] [ARG...]`
* Aliases: `docker create`
* Create a new container.

### `OPTIONS`
* Checkout [here](https://docs.docker.com/reference/cli/docker/container/create/#options)

After pulling the image, we can either run a container by specifying its name or we can create a container.

See [`docker container run`](https://github.com/C0DER11101/docker/blob/d0cker/basic.md#docker-container-run).

Let us create a container using this command:

```bash
$ docker container create --name haze --hostname fogbell -i ubuntu:24.04
```

Here, we are creating a container named `haze`.

`--hostname` specifies the container hostname.

Let's say, we run the following command(assume that the container was started first):

```bash
$ docker container exec -it nixZen bash
```

Then we get the following bash prompt:
```
root@1b91b45ad77f:~#
```

That hex string is actually the container ID of the container nixZen which is the hostname of the container.

But if we run the same command for the newly created container(after creating the container, we need to start it):

```bash
$ docker container exec -it haze bash
```

We get the following prompt:

```
root@fogbell:~#
```

Here, the hostname of the container is fogbell.

<p align="center">
&#9678; &#9678; &#9678;
</p>
