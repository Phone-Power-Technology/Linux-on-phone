# Linux-on-phone

## Simple installation Guide

take Ubuntu for example

1.Create a disk image
```
dd if=/dev/zero of=ubuntu_base.img bs=1G count=5
mkfs.ext4 ubuntu_base.img
```
