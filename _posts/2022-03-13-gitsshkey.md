---
layout: post
author: mjbronarz
title:  "Using git with a specific ssh key"
date:   2022-03-13 12:41 +0200
categories: blog linux ssh git
---

Quick and dirty way to use a specific ssh key with git:
GIT_SSH_COMMAND='ssh -i /home/user/.ssh/otherkey' git pull

