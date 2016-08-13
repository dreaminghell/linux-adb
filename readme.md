The ramdisk image for rockchip opensource linux.  
(Chaining to real filesystem is not supported, this ramdisk image is only used to update system)

### Usage ###
apt-get install genext2fs  
sh ./mk-initrd.sh

If you are using u-boot's distro supporrt, adding initrd option to extlinux.conf and copying initrd.img to your boot partition will make board booted in ramdisk.

```
label kernel-4.4
  kernel /zImage
  fdtdir /
  initrd /initrd.img
  append  earlyprintk console=ttyS2,115200n8 rw root=/dev/ram0 rootfstype=ext4 init=/sbin/init ramdisk_size=49152 
```

### Feature ###

This ramdisk is used to update images from USB-disk or SD-card to eMMC.  
It will search and execute update/update.sh in connected USB-disk or SD-card.  
Please check update/update.sh and customize it for you board.  
