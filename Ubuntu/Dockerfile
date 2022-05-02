FROM ubuntu:22.04
MAINTAINER Ye Ding "https://github.com/valency/docker-sshd"

RUN sed -i -e 's/\(archive\|security\).ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list
RUN apt-get update && apt-get install -y openssh-server sudo
RUN mkdir /var/run/sshd
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

RUN useradd -m admin
RUN usermod -s /bin/bash admin
RUN usermod -aG sudo admin
RUN echo 'admin:screencast' | chpasswd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
