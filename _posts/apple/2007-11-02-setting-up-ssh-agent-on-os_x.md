---
layout: blog-article
title: Setting up ssh-agent on OS X
meta: Using a passwordless ssh access without any passphrases could be a dangerous security hole. If you really care about this, you may want to setup your ssh key with a certain passphrase. The troublesome of using the ssh key with the passphrase is you have to type in the passphrase everytime you use the ssh key (e.g., when you login to the remote machine with the ssh access). Setting up the ssh-agent would be a good solution to avoid this trouble.
source:
category: apple
folder: apple
---

It is very important to make the environment variable **SSH_AUTH_SOCK** available all the time in order to set up successfully ssh-agent on your OS X.
The way to save the **SSH_AUTH_SOCK** variable is simple. Just create the following directory and file on your $HOME.
{% highlight bash %}
cd $HOME
mkdir .MacOSX
cd .MacOSX
{% endhighlight %}
And then create a file **environment.plist** in it
{% highlight bash %}
[15:02] halfrunt:~/.MacOSX % cat environment.plist 
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
        <key>SSH_AUTH_SOCK</key>
        <string>/tmp/dikim_ssh-agent.socket</string>
</dict>
</plist>
{% endhighlight %}

After that, follow up with the normal ssh-agent configuration on linux.
  - if **SSH_AUTH_SOCK** is not defined, setup the value with my specific null file(e.g., /tmp/dikim_ssh-agent.socket)
  - Otherewise, just use the value of **SSH_AUTH_SOCK**
  - check to see if ssh-agent process is running
  - if not, start it like this {% highlight bash %}ssh-agent -a /tmp/dikim_ssh-agent.socket{% endhighlight %}
  - And then add your ssh private key to your running ssh-agent (e.g., ssh-add ${HOME}/.ssh/id_dsa mostly)

I wrote a simple shell script to run all the boring processes and then put the script to my customized shell configuration(e.g., .tcshrc, .cshrc, or .bashrc) to make my ssh-agent configuration always work whenever I login.\\
Here is my shell script to configure my ssh_agent.
{% highlight bash %}
#!/bin/sh
#
# Check that the ssh-agent is running, and if not, kick it off
#

# default TTL = 8 hours
TTL=28800

if [[ -z $SSH_AUTH_SOCK ]]; then
   SOCKETFILE=/tmp/dikim_ssh-agent.socket
else
   SOCKETFILE=${SSH_AUTH_SOCK}
fi

/bin/ps -wU ${USER} | grep "[s]sh-agent" > /dev/null
if [[ $? -gt 0 ]]; then
   rm -f ${SOCKETFILE}
   ssh-agent -a ${SOCKETFILE}
   chmod 600 ${SOCKETFILE}
   ssh-add ${HOME}/.ssh/id_dsa
fi
{% endhighlight %}

