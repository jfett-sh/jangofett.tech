---
layout: post
title:  "[WIP] Terminal setup on Macos (alacritty + tmux)"
date:   2023-03-21 01:56:42 +0400
tags: dotfiles tmux terminal
---

### Introduction
In this post, I will illustrate how to set up Alacritty with Tmux on MacOS.

### Purpose
A terminal multiplexer is a very useful tool if you spend a lot of time in the terminal.

### Why use Alacritty? Why not use the default iTerm?
Alacritty has a flexible YAML configuration where you can customize it according to your preferences.

### Prerequisites:
MacOS, Homebrew, Alacritty, Tmux, and some technical know-how.

### Desired Outcome:

![Alacritty](/assets/img/posts/2023-03-21-terminal-setup/alacritty-complete.png "Alacritty")
Something similar to the image shown above.

## 1. Installing the Required Software
First, we need to install [Homebrew](https://brew.sh) to install Alacritty and Tmux. 
Run the following command if you have not installed Homebrew yet:

We need  to install alacritty and tmux. Go to get it, if you still didn't install it:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

To install Alacritty:
```bash
brew install --cask alacritty
```

To install Tmux:
```bash
brew install tmux
```

### Install tmuxp:
If you desire to have pre-defined workspaces with pre-created windows, panes, and environment variables, then consider utilizing [tmuxp](https://github.com/tmux-python/tmuxp):
```bash
brew install tmuxp
```

Now that we have finished installing the necessary software, let's proceed with the setup.

### Setup Tmuxp
Insert the following lines of YAML to the tmuxp configuration file located at `~/.config/tmuxp/dev.yaml`:
```yaml
session_name: dev
windows:
- window_name: dev
  options:
    automatic-rename: true
```

### Setup Alacritty

In this step we change default shell to run tmuxp with our configured tmuxp

Add (or replace if you have already configured `.shell`) the following lines of configuration to your Alacritty configuration file located at `~/.config/alacritty/alacritty.conf`:
```yaml
shell:
  program: /bin/zsh # You may replace it with your preferred shell.
  args:
    - -l
    - -c
    - "tmuxp load ~/.config/tmuxp/dev.yaml || tmux"
```

### Setup Tmux
Ensure that you have already installed the Tmux configuration. If you have not done so, you may use my own.

