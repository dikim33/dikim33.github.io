---
layout: blog-article
title: Install OSCAR on PlayStation3
meta: Research for expanding OSCAR's portability to Play Station 3 (PS3)
source:
category: linux
folder: linux
---


![OSCAR on PS3]({{ site.url }}/images/linux/oscar_on_ps3.png)
<h3> Requirements </h3>
  * OSCAR 5.1
  * 2 x PS3 machines or more
  * USB key
  * OtherOS Installer
  * HDMI-DVI connector
  * YellowDogLinux(YDL)5.0 (PPC) DVD
  * USB Keyboard and USB mouse
  * Network

<h3> Install </h3>
<strong> Step 1. Install YDL5.0 on PS3 </strong>

  * Download the OtherOS installer specially built for OSCAR
  * Save it to the USB key (FAT format) and then hook it up to the PS3
  * Power on PS3 on the game mode
     * Settings Menu -> System Settings -> A partition setting for hard disk: custom
        * 60GB = 10GB(Game) + 50GB(Linux)
     * Settings Menu -> System Settings -> Install Other OS
        * Click on OK to start the installation
     * Settings -> System Settings -> Default System and select "Other OS”

  * Insert YDL5.0 DVD
  * Restart PS3 to boot with Other OS
  * Type in “install” at the kboot prompt
  * Do the YDL5.0 installation


<strong> Step 2. Install OSCAR </strong>

  * Once YDL5.0 is fully installed and up, download OSCAR 5.1
  * Follow the ordinary OSCAR installation instruction
     * After oscarimage is created at the oscar installation Step 4, there is one thing to modify the image manually. Just remove the systemconfig.conf file at the oscarimage built
     * At the OSCAR installation step 6. “Setup Networking…”, prepare PS3 client nodes to boot up with OtherOS like we did it on the head node PS3 at the above Step 1.
       {% highlight bash %}
        chroot /var/lib/systemimager/images/oscarimage
        cd /etc/systemconfig
        mv systemconfig.conf systemconfig.conf.bak
       {% endhighlight %} 
  * Finish up the OSCAR installation


For the updated instruction, please refer to the <a href="http://oscar-cluster.github.io/oscar/wiki/OSCAR_on_PS3">wiki page</a> that I wrote on the OSCAR web site.

