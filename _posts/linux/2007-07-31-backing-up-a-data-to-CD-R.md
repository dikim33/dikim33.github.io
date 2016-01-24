---
layout: blog-article
title: Backing up a data to CD-R
meta: One of the ways to back up data, CD-R
source:
category: linux
folder: linux
---

{% highlight bash %}
mkisofs -T -r -o /tmp/mycd.iso  /data
cdrecord -v -eject -fs=4M speed=8 dev=0,0,0 /tmp/mycd.iso
{% endhighlight %}
Run "cdrecord -scanbus" to search for the CD burner on your machine.

{% highlight bash %}
mkisofs -T -r /data | cdrecord -v -eject -fs=4M speed=8 dev=0,0,0 -
{% endhighlight %}

If you prefer to use "tar" to backup your data to CD-R, here is another trick.
{% highlight bash %}
tar -czf - /data | cdrecord -v -eject -fs=4M speed=8 dev=0,0,0 -
{% endhighlight %}
This won't be mountable as a normal CD, and you won't be able to put it in a Windows system, but it works fine on Linux.

