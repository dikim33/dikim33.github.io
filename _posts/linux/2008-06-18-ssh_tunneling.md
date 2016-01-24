---
layout: blog-article
title: SSH Tunneling
meta: A Secure Shell (SSH) tunnel consists of an encrypted tunnel created through an SSH protocol connection. Users may set up SSH tunnels to transfer unencrypted traffic over a network through an encrypted channel.
source:
category: linux
folder: linux
---

This is a very useful thing to remember when I need to run a remote X application on a local machine.
Especially, when I need to test a web server which is not open to the public. \
Before using ssh-tunneling, I had to setup ssh X-forward which is not safe at all and then run the web browser on the ssh-connected machine. :-( This causes a really heavy traffic.

{% highlight bash %}
ssh -C -o CompressionLevel=9 -L 5901:localhost:5901 USER@hostname
{% endhighlight %}

Where
  * USER needs to be replaced with your real username available on the server which you try to connect
  * hostname is the hostname of your server. Of course, it can be just an IP address.
  * 5901 can be any other ports to tunnel. 5901 is used for VNC 

There is another good example to do ssh-tunneling for accessing the secondary remote host so that we don't have to do "ssh" twice (e.g., first ssh to the first remote host and then second ssh to the second remote host).
{% highlight bash %}
ssh oscar.osl.iu.edu -L 10000:192.168.0.101:22 -g
{% endhighlight %}
After setting up the ssh-tunneling like this, run the following command to access the second host directly.
{% highlight bash %}
ssh -p 10000 localhost
{% endhighlight %}

