---
layout: post
title: "Ignore .DS_Store globally in Git"
category: posts
---

I have couple of git repositories on my system. Everytime I push contents to the repository, .DS_Store also gets pushed to the repository. Previously, I periodically deleted .DS_Store file. This was cumbersome.

Next, I thought to add `.DS_Store` to `.gitignore` of the repository. But, the problem with this approach is that I have to add that line in every git repository on my system. This is cumbersome too.

Git provides global `.gitignore` also. Puff! Finally!

I did following commands to stop .DS_Store from  joining the git party:

{% highlight bash %}
$ git config --global core.excludesfile ~/.gitignore
$ echo .DS_Store >> ~/.gitignore
{% endhighlight %}

Mission Accomplished!