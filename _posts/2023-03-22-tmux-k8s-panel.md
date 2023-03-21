---
layout: post
title:  "How to setup panel in tmux with current kubernetes cluster and namespace"
date:   2023-03-22 01:29:00 +0400
tags: dotfiles tmux kubernetes
---

### Introduction
Tmux is a powerful tool that requires some configuration to display additional information for everyday use. Today, we will add information about the current Kubernetes cluster and namespace.

### Prerequisites:
kubectl, tmux

### Desired Outcome:

![tmux](/assets/img/posts/2023-03-21-tmux-kubernetes-panel/tmux-panel.png "tmux")

## Setup
That's super-easy. Just add these lines into your tmux config:
```
set-option -ag status-left "#[fg=#2C09E3,bg=default]#[fg=#01BBFF,bg=default]#(kubectl config current-context | cut -d "/" -f2-) "
set-option -ag status-left "#[fg=#01BBFF,bg=default]/ #(kubectl config view --minify -o jsonpath='{..namespace}') "
set -g status-interval 5
```
### What we did?
Let's take a quick look what that's mean:

The command `set-option -ag` is a general instruction that provides various options to tmux.

The instruction `status-left` tells tmux to display the status block.

The custom colors of our status panel are defined as follows: `[fg=#2C09E3,bg=default]#[fg=#01BBFF,bg=default]`. The first color set specifies the foreground and background color of the left side of the panel, while the second set specifies the foreground and background color of the right side.

The `kubectl config current-context --minify -o jsonpath='{..namespace}')` command is used to display the current context and namespace in kubectl.

The option `set -g status-interval 5` specifies that the status block should be refreshed every 5 seconds in tmux.