# Docker with GPU and SSH Access

## Ubuntu SSHD

https://hub.docker.com/repository/docker/uiewy/ubuntu-sshd

Ubuntu SSHD is based on 24.04.

Build:

```bash
cd Ubuntu
docker build . --tag ubuntu-sshd:24.04
```

Run:

```bash
docker run -dti --privileged -p 22 ubuntu-sshd:24.04
```

Usage:

```bash
ssh -p <port> admin@localhost
```

The default password is `screencast`.

## CUDA SSHD

https://hub.docker.com/repository/docker/uiewy/cuda-sshd

CUDA SSHD is based on [nvidia/cuda:12.2.0-devel-ubuntu22.04](https://hub.docker.com/r/nvidia/cuda).

Build:

```shell
cd CUDA
docker build . --tag cuda-sshd:12.2.0
```

Run:
```shell
docker run -dti --privileged -p 22 --gpus '"device=all"' cuda-sshd:12.2.0
```

Usage:

```bash
ssh -p <port> admin@localhost
```

The default password is `screencast`.

## CUDA WeTTY

https://hub.docker.com/repository/docker/uiewy/cuda-wetty

CUDA WeTTY is based on [nvidia/cuda:12.2.0-devel-ubuntu22.04](https://hub.docker.com/r/nvidia/cuda) and [butlerx/wetty](https://github.com/butlerx/wetty) with [NGINX](https://nginx.org/) enabled.

Build:

```shell
cd WeTTY
docker build . --tag cuda-wetty:12.2.0
```

Run:
```shell
docker run -dti --privileged -p 80 --gpus '"device=all"' cuda-wetty:12.2.0
```

Usage:

```plain
http://localhost:<port>/
http://localhost:<port>/wetty
```

The default user and password of WeTTY are `admin` and `cephalon`.

