# ubuntu-sshd-ffmpeg

Dockerized FFMpeg service with ssh direct access for remote FFMpeg commands

## Image tags
- sshd-ubuntu-ffmpeg:16.04 (xenial)
- sshd-ubuntu-ffmpeg:latest:18.04 (bionic)
- sshd-ubuntu-ffmpeg:latest (xenial)

## Installed packages

Base:

- [Xenial (16.04) minimal](http://packages.ubuntu.com/xenial/ubuntu-minimal)
- [Bionic (18.04) minimal](http://packages.ubuntu.com/bionic/ubuntu-minimal)

Forked image from: rastasheep/ubuntu-sshd: 

- Docker Hub: https://hub.docker.com/r/rastasheep/ubuntu-sshd/
- Github: https://github.com/rastasheep/ubuntu-sshd

Image specific:
- [openssh-server](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
- FFMpeg

Config:

  - `PermitRootLogin no`
  - `UsePAM no`
  - exposed port 22
  - default command: `/usr/sbin/sshd -D`
  - Passwords are not defined 

## Run example

```bash
$ sudo docker run -d -p portyouwant:22/tcp --name containername tuxnvape/tuxnvape/sshd-ubuntu-ffmpeg:latest
$ sudo docker exec -ti peerenc-mod passwd peerenc
$ sudo docker exec -ti peerenc-mod passwd root

$ ssh root@localhost -p 49154
root@test_sshd $

USER PREIMPLEMENT
$ ssh peerenc@localhost -p 49154
peerenc@test_sshd $
```

