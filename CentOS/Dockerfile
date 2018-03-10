FROM centos:7
 
RUN yum -y update && yum -y install openssh-server passwd initscripts
RUN sshd-keygen
RUN echo 'root:screencast' | chpasswd
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
