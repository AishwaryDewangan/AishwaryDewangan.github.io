---
layout: post
title: "Remove all Docker Images and Containers"
category: posts
---

There are times when you wanted to start docker with clean state. Below are the commands that
removes all docker images and containers.

## List all Containers

{% highlight bash %}
$ docker container ls
{% endhighlight %}

It lists different informations related to all the containers. We need only container id's for removing them.

{% highlight bash %}
$ docker container ls | awk '{print $1}'
{% endhighlight %}

Below is much simpler command:

{% highlight bash %}
$ docker ps -aq
{% endhighlight %}

## Removing Containers

First we need to stop all the containers that are running.

{% highlight bash %}
$ docker stop $(docker ps -aq)
{% endhighlight %}

Now, remove all the containers.

{% highlight bash %}
$ docker rm $(docker ps -aq)
{% endhighlight %}

## Removing Images


{% highlight bash %}
$ docker rmi $(docker images -q)
{% endhighlight %}