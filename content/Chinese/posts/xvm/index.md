---
keywords: ['blog','xvm','version manager','nvm','conda','pyenv','gvm']
title: 'XVM：Node.js、Go、Python版本管理器X Version Manger'
date: 2025-03-28T16:00:20+08:00
lastmod: 2025-03-28T16:00:20+08:00
draft: false
description: 'XVM是可扩展的版本管理器，支持Node.js、Go和Python。学习使用此开源工具管理多语言版本。' 
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

作为一名全干工程师，我们会在同一个电脑上安装各种工具，然而又会因为各种原因，需要使用这些工具的不同版本，版本管理就变的十分重要。

我们会使用 **nvm** 来管理 Node.js；

我们会使用 **gvm** 来管理 Go；

我们会使用 **pyenv** 或者 **Conda** 来管理 Python；

这些工具都十分强大，但使用方式却各不相同，一段时间不使用，就不得不重新熟悉每个工具的使用方式。重要的是，平白无故又多了好几个软件。

在一次重装系统之后，终于忍无可忍... 其实我的需求很简单，也用不到版本管理器的那些高级功能，我只是需要一个小巧的版本管理器，使用统一的管理方式，统一的命令。

因此 [**xvm**](https://github.com/duan0120/xvm) 应运而生，融合了 **Node.js**， **Go**， **Python** 等的版本管理工具，虽然没有专业的工具那么强大，但小巧且命令统一。

> xvm 是 linux 和 macos 上的版本管理工具，windows 上可以使用 [xvm-windows](../xvm-windows)

## 安装方式

```bash
curl -o- https://raw.githubusercontent.com/duan0120/xvm/main/install.sh | bash
```

或者

```bash
git clone https://github.com/duan0120/xvm.git ~/.xvm
```

将下面代码放到 **~/.bashrc** 或者  **~/.zshrc** 中，并重新 source

```bash
export XVM_ROOT=~/.xvm
[ -s "$XVM_ROOT/xvm" ] && source "$XVM_ROOT/xvm"
```

## 使用方式

查看版本 

```bash
xvm -v
```

获取帮助

```bash
xvm -h
xvm help node
```

### Node.js

查看版本

```bash
# 查看发布版本
xvm node ls-remote
# 查看 lts 版本
xvm node ls-remote --lts
# 查看已安装版本
xvm node list
# 查看默认版本
xvm node default
```

安装指定版本

```bash
# 安装指定版本
xvm node install v18.19.1
# 安装指定版本，并设置为默认版本, 重启terminal或者source生效
xvm node install v18.19.1 --default
```

卸载指定版本

```bash
xvm node uninstall v18.19.1
```

切换版本

```bash
# 临时切换指定版本
xvm node use v18.19.1
# 临时切换指定版本，并设置为默认
xvm node use v18.19.1 --default
```

### Go

查看版本

```bash
xvm go ls-remote
xvm go list
```

安装指定版本

```bash
xvm go install go1.19.2
# 安装并设置为默认版本
xvm go install go1.19.2 --default
# 
xvm go install go1.13.10 --default --arch=amd64
```

> 如果需要指定下载地址，可以在 **~/.xvm/scripts/go-scripts/proxy** 文件中指定，如 [https://golang.google.cn](https://golang.google.cn/)

卸载指定版本

```bash
xvm go uninstall go1.19.2
```

切换版本

```bash
# 临时切换指定版本
xvm go use go1.19.2
# 临时切换指定版本，并设置为默认
xvm go use go1.19.2 --default
```

查看默认版本

```bash
xvm go default
```

### Python

xvm 也支持管理虚拟环境，并且操作很简单

安装依赖 

Python使用的是源码编译安装，需要安装依赖，请参考 [https://devguide.python.org/getting-started/setup-building/](https://github.com/duan0120/xvm/blob/master)

查看版本

```bash
xvm python ls-remote
xvm python list
```

安装指定版本

```bash
xvm python install 3.12.0
# 安装并设置为默认版本
xvm python install 3.12.0 --default
```

切换版本

```bash
# 临时切换指定版本
xvm python use 3.12.0
# 临时切换指定版本，并设置为默认
xvm python use 3.12.0 --default
```

查看默认版本

```bash
xvm python default
```

创建虚拟环境

```bash
xvm python alias 3.12.0 venv
```

激活虚拟环境

```bash
xvm python activate venv
```

撤销虚拟环境

```bash
xvm python deactivate
```

卸载指定版本

```bash
xvm python uninstall 3.12.0
# 删除虚拟环境
xvm python uninstall venvxVM：Node.js、Go、Python版本管理器
```
