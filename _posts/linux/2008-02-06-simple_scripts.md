---
layout: blog-article
title: Simple Scripts
meta: I would like to share my simple scripts that I found useful while working for the Center for Research in Extreme Scale Technologies (CREST) as a System Administrator
source:
category: linux
folder: linux
---

<h3> lsof </h3>
Sometimes my system is in trouble with the high loadaverage of the web server because of the attack of some malicious IPs.\\
I have tried to look for a command to get the IPs which make this kind of trouble by looking into its pid.
{% highlight bash %}
      lsof -nP -w -T -i tcp | grep httpd | grep <PROCESS_ID_TO_CHECK>
{% endhighlight %}

<h3> diff </h3>
Sometimes I want to find the diffs between my local file and remote file or between remote files. Here is a simple trick.
{% highlight bash %}
      diff <LOCAL_FILE <(ssh remote_host_1 cat REMOTE_FILE)
      diff <(ssh remote_host_1 cat REMOTE_FILE_1)  <(ssh remote_host_2 cat REMOTE_FILE_2)
{% endhighlight %}
(Note, where remote_host_1 and remote_host_2 should be setup with your ssh-key stuff and you should not need to put your password or passphrase. Unfortunately, this works only on bash)

<h3> dump and restore </h3>
dump and restore are a sysadmin's friend. They really make it easy for sysadmin to handle the backup of a system. There may be some applications to replace the command dump and restore but I would like to be stuck with them untli I find something better than them.\\ Do you know that we can simply dump the whole partition and restore it on the remote machine? So, we can migrate the whole system with a following simple script using dump and restore
{% highlight bash %}
      ssh remote_host(_IP) -n dump 0cf - / | restore xf -
{% endhighlight %}
I found this tip when <a href="http://www.cs.indiana.edu/~shei">Bruce</a>, the CS sysadmins at IU, helped to migrate one of the very important servers of the OSL. I would like to give special thanks to Bruce.

**Note**

  * The target machine where you want to migrate a system should be clean(or empty) to take the whole system of the remote machine assuming it has enough space to restore the dump file.
  * Reboot your target machine to go to a single-user mode. (e.g., I usually do with my linux installation CD)
  * Run the above script at the target machine.
  * Of course, the ssh-key stuff should be setup without having to put your password or passphrase.

<h3> Mount ISO file </h3>
{% highlight bash %}
mount -o loop -t iso9660 file.iso /mnt/test
{% endhighlight %}


