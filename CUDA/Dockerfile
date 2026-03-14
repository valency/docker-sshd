FROM nvidia/cuda:13.1.1-cudnn-devel-ubuntu24.04

RUN sed -i -e 's/\(archive\|security\).ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list.d/ubuntu.sources
RUN apt-get update && apt-get install -y openssh-server sudo
RUN mkdir /var/run/sshd
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

RUN useradd -m admin
RUN usermod -s /bin/bash admin
RUN usermod -aG sudo admin
RUN echo 'admin:screencast' | chpasswd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
