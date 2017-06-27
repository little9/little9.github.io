---
layout: post
title:  git cherry-pit  
author: Jamie Little
---

I love `git cherry-pick`, which lets you apply a sigle commit to you current branch. Today I needed to do the
oppisite of that -- remove a single commit from my branch. [Seth Robertson has a technique](https://sethrobertson.github.io/GitFixUm/fixup.html) that he calls `cherry-pit` that does this:

```
git rebase -p --onto SHA^ SHA
```
