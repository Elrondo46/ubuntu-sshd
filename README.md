# ubuntu-sshd-ffmpeg

Dockerized FFMpeg service with ssh direct access for remote FFMpeg commands

## Image tags
- ubuntu-sshd:16.04 (xenial)
- ubuntu-sshd:18.04 (bionic)

## Installed packages

Base:

- [Xenial (16.04) minimal](http://packages.ubuntu.com/xenial/ubuntu-minimal)
- [Bionic (18.04) minimal](http://packages.ubuntu.com/bionic/ubuntu-minimal)

Image specific:
- [openssh-server](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
- FFMpeg

Config:

  - `PermitRootLogin no`
  - `UsePAM no`
  - exposed port 22
  - default command: `/usr/sbin/sshd -D`
  - root password: `root`
  - peerenc password: peerenc

## Run example

```bash
$ sudo docker run -d -P --name test_sshd rastasheep/ubuntu-sshd:14.04
$ sudo docker port test_sshd 22
  0.0.0.0:49154

$ ssh root@localhost -p 49154
# The password is `root`
root@test_sshd $

USER PREIMPLEMENT
$ ssh peerenc@localhost -p 49154
# The password is `peerenc`
peerenc@test_sshd $
```

## Security

If you are making the container accessible from the internet you'll probably want to secure it bit.
You can do one of the following two things after launching the container:

- Change the password of peerenc user or create another user and set a complex password

```bash
$ docker exec test_sshd passwd -d root
$ docker exec test_sshd passwd -d peerenc
```
