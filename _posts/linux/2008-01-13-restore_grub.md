---
layout: blog-article
title: Restore grub
meta: Preparing for the contingency plan - how to restore a grub
source:
category: linux
folder: linux
---


Sometimes, you may mess up with your grub and you can not even boot up your system because of the broken grub.

Here is a simple way to restore or re-setup grub.

  * Boot up your system with the first install CD or DVD to go to the rescue mode (e.g., linux rescue)
  * Let the rescue mode mount your linux partition (your root(/) partition) to /mnt/sysimage.
  * chroot /mnt/sysimage
  * grub-install /dev/hda  <= if your grub is not installed/messed up, try to reinstall it 
  * grub
  * root (hd0,1)           <= The first number indicates the disk and second one is for the boot partition
  * setup (hd0)
  * quit
  * And get out of the rescue mode and then boot up your system without your installation CD / DVD

