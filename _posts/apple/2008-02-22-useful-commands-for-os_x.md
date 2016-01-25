---
layout: blog-article
title: Useful commands for OS X
meta: Some useful commands - ioreg, pmset, chflg, fsaclctl, and system_profiler
source:
category: apple
folder: apple
---

  * **ioreg** shows I/O Kit registry. I usually use this to check the capacity of a battery in my powerbook
{% highlight bash %}
ioreg -p IODeviceTree -n "battery" -w 0 | grep IOBatteryInfo
{% endhighlight %} 
  * If the above command does not work with the newer version of OSX, try to use the following instead:
{% highlight bash %}
pmset -g batt
{% endhighlight %}
  * **hdiutil** manipulates disk images: I usually use this to merge several dmg files to one iso file.
{% highlight bash %}
hdiutil makehybrid -iso -o /path/to/make/your/iso/file.iso /directory/of/the/source/dmg/files/
{% endhighlight %}

  * **chflags** change file flags: I usually use this to lock/unlock files with uchg/nouchg and do something else with some other flags (e.g., nodump, ...).   
      The option, nouchg clears the user immutable flag.
{% highlight bash %}
sudo find . -flags uchg -exec chflags nouchg {} \;
  or
sudo chflags -R nouchg .
{% endhighlight %}

  * **fsaclctl** controls the ACL on the specific path.
{% highlight bash %}
usage:  fsaclctl -p path | -a  [-e enable] [-d disable] [-v]
                -p              path to filesystem mount point
                -a              operate on all relevant volumes
                -e              enable access control lists on this filesystem
                -d              disable access control lists on this filesystem
                -v              print version
{% endhighlight %} 


  * **system_profiler** displays system information of OSX
{% highlight bash %}
system_profiler SPHardwareDataType SPNetworkDataType
{% endhighlight %}
