FROM nvidia/cuda:12.2.0-devel-ubuntu22.04
MAINTAINER Ye Ding "https://github.com/valency/docker-sshd"

RUN sed -i -e 's/\(archive\|security\).ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list
ENV TZ=Asia/Hong_Kong
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update; exit 0
RUN apt-get install -y openssh-server sudo
RUN mkdir /var/run/sshd
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

RUN useradd -m admin
RUN usermod -s /bin/bash admin
RUN usermod -aG sudo admin
RUN echo 'admin:screencast' | chpasswd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
