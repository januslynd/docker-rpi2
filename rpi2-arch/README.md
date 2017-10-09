# Archlinux (RPI2)

This is a Docker ArchlinuxARM base image. In order to build the image
and once you are in the `rpi2-arch` directory, the you have to:

- Download the latest ArchARM distro for Raspberry Pi 2 and name it
  `archlinux.tar.gz`

```
curl -L http://archlinuxarm.org/os/ArchLinuxARM-rpi-2-latest.tar.gz -o archlinux.tar.gz
```

- Then execute:

```
./build.sh
```

And after a while (go and grab a coffee cause it could really take a
while :P) you'll have an ArchLinux distro for your rpi2 Docker images.

Based on this blog: http://linucc.github.io/docker-arch-rpi2/
