---
layout: post
title: Ignore .DS_Store globally in Git
category: posts
---

# Ignore .DS\_Store Globally in Git

I have couple of git repositories on my system. Everytime I push contents to the repository, .DS\_Store also gets pushed to the repository. Previously, I periodically deleted .DS\_Store file. This was cumbersome.

Next, I thought to add `.DS_Store` to `.gitignore` of the repository. But, the problem with this approach is that I have to add that line in every git repository on my system. This is cumbersome too.

Git provides global `.gitignore` also. Puff! Finally!

I did following commands to stop .DS\_Store from joining the git party:

Mission Accomplished!

