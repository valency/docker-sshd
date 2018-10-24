# SSH Daemon in Docker

## Installation

### Ubuntu

Ubuntu SSHD is based on 18.04.

Build:

```bash
cd Ubuntu
docker build . --tag ubuntu-sshd:18.04
```

Run:

```bash
docker run -dti -p 22 ubuntu-sshd:18.04
```

### CentOS

CentOS SSHD is based on 7.

Build:

```
cd CentOS
docker build . --tag centos-sshd:7
```

Run:

```bash
docker run -dti -p 22 -v /sys/fs/cgroup:/sys/fs/cgroup:ro centos-sshd:7
```

## Usage

```bash
ssh -p <port> admin@localhost
```

The default password is `screencast`.

