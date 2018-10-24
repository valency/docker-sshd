FROM centos:7
MAINTAINER Ye Ding "https://github.com/valency/docker-sshd"
 
RUN yum -y install openssh-server passwd initscripts sudo
RUN sshd-keygen

RUN useradd -m admin
RUN usermod -aG wheel admin
RUN echo 'admin:screencast' | chpasswd

ENV container docker
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == \
systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;
VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
