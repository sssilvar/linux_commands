# How to increase the root partition size on Fedora

Boot up with an Fedora Live USB stick.

1. Run `vgs` to check if there's any space:
```shell
$ sudo vgs
  VG     #PV #LV #SN Attr   VSize    VFree
  fedora   1   3   0 wz--n- <237.28g    0 
```
2. If there is you can just run:
```shell
lvresize -L +5G --resizefs /dev/mapper/fedora-root
```
**NB:** Remember to check where your fedora `root` and `home` partition is mounted by running `fdisk -l`.

3. If you don't have any free `VFree` space, you can shrink your `home` partition 
and then extend your `root` partition afterwards.


To scrink your `home` partition run:
```shell
lvresize -L -10G --resizefs /dev/mapper/fedora-home
```

And then to extend your `root` partition run:
```shell
lvresize -L +10G --resizefs /dev/mapper/fedora-root
```
