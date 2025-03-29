---
keywords: ['blog','xvm','version manager','nvm','conda','pyenv','gvm']
title: 'X Version Manager'
date: 2025-03-28T16:00:23+08:00
lastmod: 2025-03-28T16:00:23+08:00
draft: false
description: 'x version manager'
author: 'duanhongjin'
tags: ['xvm']
categories: []
tocLevels: ["h2", "h3", "h4"]
comments: true # 本页面是否显示评论
reward: true # 打赏
showToc: true # 显示目录
TocOpen: true # 自动展开目录
hidemeta: false # 是否隐藏文章的元信息，如发布日期、作者等
disableShare: true # 底部不显示分享栏
showbreadcrumbs: true #顶部显示路径
---

As a full-stack engineer, we often install various tools on the same computer. However, due to different requirements, we may need to use different versions of these tools, making version management extremely important.

We use **nvm** to manage Node.js;  
We use **gvm** to manage Go (Golang);  
We use **pyenv** or **Conda** to manage Python.

These tools are all very powerful, but their usage differs significantly. After a period of not using them, we have to re-familiarize ourselves with how each one works. More importantly, this adds several extra pieces of software to our system for no apparent reason.

After reinstalling my system one time, I finally reached my breaking point… In reality, my needs are simple, and I don’t require the advanced features of these version managers. I just need a lightweight version manager with a unified management approach and consistent commands.

Thus, [**xvm**](https://github.com/duan0120/xvm) was born—a version management tool that integrates support for **Node.js**, **Go**, **Python**, and more. While it may not be as powerful as specialized tools, it’s compact and offers a uniform command structure.

> xvm is a version management tool for Linux and macOS, while on Windows, you can use [xvm-windows](../xvm-windows).

## Installation

```bash
curl -o- https://raw.githubusercontent.com/duan0120/xvm/main/install.sh | bash
```

or

```bash
git clone https://github.com/duan0120/xvm.git ~/.xvm
```

Add the following code to **~/.bashrc** or **~/.zshrc**, and source it again:

```bash
export XVM_ROOT=~/.xvm
[ -s "$XVM_ROOT/xvm" ] && source "$XVM_ROOT/xvm"
```

## Usage

Check version

```bash
xvm -v
```

Get help

```bash
xvm -h
xvm help node
```

### Node.js

List available versions

```bash
xvm node ls-remote
xvm node ls-remote --lts
xvm node list
```

Install specific version

```bash
xvm node install v18.19.1
# Install the specified version and set it as the default.
xvm node install v18.19.1 --default
```

Uninstall specific version

```bash
xvm node uninstall v18.19.1
```

Switch version

```bash
xvm node use v18.19.1
# switch to the specified version and set it as the default
xvm node use v18.19.1 --default
```

Check default version

```bash
xvm node default
```

### Go

List available versions

```bash
xvm go ls-remote
xvm go list
```

Install specific version

```bash
xvm go install go1.19.2
xvm go install go1.19.2 --default
# arch: amd64/arm64/386 and the default arch is amd64
xvm go install go1.13.10 --default --arch=amd64
```

Uninstall specific version

```bash
xvm go uninstall go1.19.2
```

Switch version

```bash
xvm go use go1.19.2
# switch to the specified version and set it as the default
xvm go use go1.19.2 --default
```

Check default version

```bash
xvm go default
```

### Python

Install dependencies Source code compilation installation, please refer to [https://devguide.python.org/getting-started/setup-building/](https://github.com/duan0120/xvm/blob/master)

Check version

```bash
xvm python ls-remote
xvm python list
```

Install specific version

```bash
xvm python install 3.12.0
# Install the specified version and set it as the default.
xvm python install 3.12.0 --default
```

Switch version

```bash
xvm python use 3.12.0
# switch to the specified version and set it as the default
xvm python use 3.12.0 --default
```

Check default version

```bash
xvm python default
```

Create virtual environment

```bash
xvm python alias 3.12.0 venv
```

Activate virtual environment

```bash
xvm python activate venv
```

Deactivate virtual environment

```bash
xvm python deactivate
```

Uninstall specific version

```bash
xvm python uninstall 3.12.0
# remove the virtual environment
xvm python uninstall venv
```
