---
layout: post
title: "Run Ubuntu in background on VirtualBox in Headless Mode"
category: posts
---

* Install Ubuntu Server on VirtualBox. While setting up, you have to provide VM name(I have used VM name as UbuntuServer). Keep this name in mind as it will be used later. Also, tick OpenSSH checkbox while installing Ubuntu Server. We will connect to server using SSH. If you forgot to tick OpenSSH checkbox, install it separately after installing Ubuntu Server.

* After installing, run these commands:
{% highlight bash %}
$ vboxmanage modifyvm UbuntuServer --nic1 nat
$ vboxmanage modifyvm UbuntuServer --natpf1 "guestssh,tcp,,2222,,22"
$ vboxmanage modifyvm UbuntuServer --natdnshostresolver1 on
{% endhighlight %}

* Now, start Ubuntu from terminal:
{% highlight bash %}
$ vboxmanage startvm UbuntuServer --type headless
{% endhighlight %}
This command will start Ubuntu Server in virtualbox in background.

* Connect to our server using SSH:
{% highlight bash %}
ssh -p 2222 aishwary@localhost
{% endhighlight %}