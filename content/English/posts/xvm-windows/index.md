---
keywords: ['blog', 'xvm','version manager','nvm','conda','pyenv','gvm']
title: 'xvm: Version Manager on windows for Node.js, Go, Python'
date: 2025-03-28T23:21:09+08:00
lastmod: 2025-03-28T23:21:09+08:00
draft: false
description: 'xvm is an extendable version manager on windows for Node.js, Go, and Python. Learn to manage multiple language versions with this open-source tool.'
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

[xvm-windows](https://github.com/duan0120/xvm-windows) is the Windows version of [xvm](../xvm), and its usage is basically consistent with xvm.

## Installation

```bash
git clone https://github.com/duan0120/xvm-windows.git %USERPROFILE%/.xvm
```

Configure environment variables

```bash
XVM_ROOT=%USERPROFILE%/.xvm
```

Add the following paths to **%PATH%**

```bash
%XVM_ROOT%\versions\node\default
%XVM_ROOT%\versions\go\default\bin
%XVM_ROOT%\versions\python\default
%XVM_ROOT%\versions\python\default\Scripts
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
```

Uninstall specific version

```bash
xvm node uninstall v18.19.1
```

Switch version

```bash
xvm node use v18.19.1
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
# arch: amd64/arm64/386, default arch: amd64
xvm go install go1.13.10 --arch=amd64
```

Uninstall specific version

```bash
xvm go uninstall go1.19.2
```

Switch version

```bash
xvm go use go1.19.2
```

### Python

List available versions

```bash
xvm python ls-remote
xvm python list
```

Install specific version

```bash
xvm python install 3.12.1
# arch: amd64/arm64/386, default arch: amd64
xvm python install 3.12.1 --arch=arm64
```

Create virtual environment

```bash
xvm python alias test 3.12.1
```

Activate virtual environment

```bash
xvm python use test
```

Uninstall specific version

```bash
xvm python uninstall 3.12.1
# remove environment
xvm python uninstall test
```

Switch version

```bash
xvm python use 3.12.1
```
