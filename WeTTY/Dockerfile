FROM nvidia/cuda:12.2.0-devel-ubuntu22.04

RUN sed -i -e 's/\(archive\|security\).ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list
ENV TZ=Asia/Hong_Kong
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get update; exit 0
RUN apt-get install -y sudo curl
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
RUN apt-get install -y nodejs
RUN useradd -m admin
RUN usermod -s /bin/bash admin
RUN usermod -aG sudo admin
RUN echo 'admin:cephalon' | chpasswd

RUN npm i -g wetty@2.5.0

EXPOSE 80
CMD ["wetty", "-p", "80", "--ssh-user", "admin"]

