---
keywords: ['blog', 'xvm',]
title: 'X Version Manger for Windows'
date: 2025-03-28T23:21:06+08:00
lastmod: 2025-03-28T23:21:06+08:00
draft: false
description: '版本管理工具'
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

[**xvm-windows**](https://github.com/duan0120/xvm-windows) 是 [**xvm**](../xvm) 的 windows 版本，使用方式和 **xvm** 基本一致。

## 安装方式

```bash
git clone https://github.com/duan0120/xvm-windows.git %USERPROFILE%/.xvm
```

配置环境变量

```bash
XVM_ROOT=%USERPROFILE%/.xvm
```

将下面路径加入到**%PATH%**中

```bash
%XVM_ROOT%\versions\node\default
%XVM_ROOT%\versions\go\default\bin
%XVM_ROOT%\versions\python\default
%XVM_ROOT%\versions\python\default\Scripts
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
# 查看已发布版本
xvm node ls-remote
# 查看已发布 lts 版本
xvm node ls-remote --lts
# 查看本地已安装版本
xvm node list
```

安装指定版本

```bash
xvm node install v18.19.1
```

卸载指定版本

```bash
xvm node uninstall v18.19.1
```

切换版本

```bash
xvm node use v18.19.1
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
# 指定架构，amd64/386/arm64, 默认为amd64
xvm go install go1.13.10 --arch=amd64
```

> 如果需要指定下载地址，可以在 **%XVM_ROOT%/.xvm/scripts/go-scripts/proxy** 文件中指定，如 [https://golang.google.cn](https://golang.google.cn/)

卸载指定版本

```bash
xvm go uninstall go1.19.2
```

切换版本

```bash
xvm go use go1.19.2
```

### Python

查看版本

```bash
xvm python ls-remote
xvm python list
```

安装指定版本

```bash
xvm python install 3.12.1
# 指定架构，amd64/386/arm64, 默认为amd64
xvm python install 3.12.1 --arch=arm64
```

创建虚拟环境

```bash
xvm python alias test 3.12.1
```

激活虚拟环境

```bash
xvm python use test
```

卸载指定版本

```bash
xvm python uninstall 3.12.1
# 删除虚拟环境
xvm python uninstall test
```

切换版本

```bash
xvm python use 3.12.1
```
