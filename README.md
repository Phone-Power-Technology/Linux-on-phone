# Linux-on-phone

## Simple installation Guide

take Ubuntu for example

1.Create a disk image
```
dd if=/dev/zero of=ubuntu_base.img bs=1G count=5
mkfs.ext4 ubuntu_base.img
```

2.Mount
```
sudo mkdir /mnt/loopback
sudo mount -o loop ubuntu_base.img /mnt/loopback
```
3.Prepare
```
wget -C https://cdimage.ubuntu.com/ubuntu-base/releases/21.10/release/ubuntu-base-21.10-base-arm64.tar.gz
sudo tar -xpvf ubuntu-base-21.10-base-arm64.tar.gz -C /mnt
sudo cp /etc/resolv.conf /mnt/etc/

```
4.chroot
```
sudo apt install qemu-user-static
```
```
sudo mount -v --bind /dev /mnt/dev
sudo mount -vt devpts devpts /mnt/dev/pts -o gid=5,mode=620
sudo mount -vt proc proc /mnt/proc
sudo mount -vt sysfs sysfs /mnt/sys
sudo mount -vt tmpfs tmpfs /mnt/run
chroot /mnt

```
