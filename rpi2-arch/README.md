# Archlinux ARM (RPI2)

This is a Docker ArchlinuxARM base image. In order to build the image
you have to :

- Download the latest ArchARM distro for Raspberry Pi 2 `tar.gz`
- Rename it to `archlinux.tar.gz` distribution
- Execute:

    docker build -t rpi2-arch .

And after a while (it could really take a while :P) you'll have the
base image for anything you want.
