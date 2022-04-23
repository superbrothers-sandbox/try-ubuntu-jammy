# try-ubuntu-dammy

```
$ wget https://cloud-images.ubuntu.com/releases/jammy/release-20220420/ubuntu-22.04-server-cloudimg-amd64.img
$ qemu-img resize ubuntu-22.04-server-cloudimg-amd64.img 50G
$ cloud-localds user-data.img cloud.cfg
$ sudo virt-install \
    --name jammy \
    --os-type linux \
    --os-variant ubuntu20.04 \
    --memory 2048 \
    --vcpu 2 \
    --noautoconsole \
    --disk path=${PWD}/ubuntu-22.04-server-cloudimg-amd64.img \
    --disk path=${PWD}/user-data.img,device=cdrom \
    --network default \
    --import
$ virsh domifaddr jammy
 Name       MAC address          Protocol     Address
-------------------------------------------------------------------------------
 vnet0      52:54:00:d0:a5:8b    ipv4         192.168.122.243/24
$ ssh ubuntu@192.168.122.243
```
