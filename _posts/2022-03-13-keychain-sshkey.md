---
layout: post
author: mjbronarz
title:  "Using MacOS X Keychain with ssh-agent"
date:   2022-03-13 12:54 +0200
categories: blog macos unix ssh ssh-agent keychain
---

If you want to store your ssh-key password in Apple Keychain do the following:


Edit .ssh/config and add:

```
Host *
    UseKeychain yes
    AddKeysToAgent yes
```

Save the file and add the key to ssh-agent: **ssh-add .ssh/id_ed25519**


And that's all folks.
