FROM       ubuntu:18.04
MAINTAINER Baba Orhum "https://github.com/Elrondo46"

RUN apt update
RUN apt -y  dist-upgrade
RUN apt install -y openssh-server ffmpeg
RUN mkdir /var/run/sshd

RUN echo 'root:root' |chpasswd

RUN sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

RUN mkdir /root/.ssh
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN useradd -m -d /home/peerenc peerenc -s /bin/bash
RUN echo 'peerenc:peerenc' |chpasswd

EXPOSE 22

CMD    ["/usr/sbin/sshd", "-D"]
