# SSH Daemon in Docker

## Installation

### Ubuntu

Ubuntu SSHD is based on 20.04.

Build:

```bash
cd Ubuntu
docker build . --tag ubuntu-sshd:20.04
```

Run:

```bash
docker run -dti --privileged -p 22 ubuntu-sshd:18.04
```

### CentOS

CentOS SSHD is based on 7. This version of CentOS does not support `systemctl`.

Build:

```bash
cd CentOS
docker build . --tag centos-sshd:7
```

Run:

```bash
docker run -dti --privileged -p 22 --cap-add=SYS_ADMIN -v /sys/fs/cgroup:/sys/fs/cgroup:ro centos-sshd:7
```

### Cuda

Cuda SSHD is based on `nvidia/cuda:11.1-devel-ubuntu20.04`.

Build:

```shell
cd Cuda
docker build . --tag cuda-sshd:11.1
```
Run:
```shell
docker run -dti --privileged -p 22 --gpus 'all,"capabilities=compute,graphics,utility,video"' cuda-sshd:11.1
```

## Usage

```bash
ssh -p <port> admin@localhost
```

The default password is `screencast`.

