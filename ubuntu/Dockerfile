FROM ubuntu

MAINTAINER Kamesh Sampath, kamesh.sampath@hotmail.com

# Update the APT cache
RUN apt-get update  -y
RUN apt-get upgrade -y 

# Install and setup project dependencies
RUN apt-get install -y curl unzip wget supervisor openssh-server rsyslog
RUN mkdir -p /var/run/sshd
RUN mkdir -p /var/log/supervisor

#Set root password
RUN echo 'root:root' | chpasswd

#Edit SSH congiuration to allow root login
RUN sed -ri 's/PermitRootLogin without-password/PermitRootLogin yes/g' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
RUN sed -ri 's/#UsePAM no/UsePAM no/g' /etc/ssh/sshd_config

EXPOSE 22

