---
keywords: ['blog', 'git', 'github', 'ssh']
title: '同一个系统上管理多个github账号'
date: 2025-05-07T23:04:09+08:00
lastmod: 2025-05-07T23:04:09+08:00
draft: false
description: '如何在同一个系统上使用ssh方式管理多个github账号？'
author: 'duanhongjin'
tags: ['git']
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

有不少人拥有多个github账号，比如个人账号，用户开源的账号。那如何在同一台电脑上管理多个github账号呢？

## 1. 使用https方式

```bash
git clone https://duanhjlt@github.com/duanhjlt/blog.git
git clone https://duan0120@github.com/duan0120/xvm.git
```

## 2. 使用ssh方式

### 2.1 创建ssh key

```bash
ssh-keygen -t ed25519 -C "duanhjlt@163.com" -f ~/.ssh/id_ed25519_github1
ssh-keygen -t ed25519 -C "duanhjlt@gmail.com" -f ~/.ssh/id_ed25519_github2
```

### 2.2 将ssh公钥添加到对应的github账号

### 2.3 设置ssh

#### 2.3.1 设置配置文件

```bash
# ~/.ssh/config

Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_github2
    
Host github1.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_github1
```

#### 2.3.2 清除当前ssh代理中的密钥

```bash
ssh-add -D
```

#### 2.3.3 添加需要的密钥

```bash
ssh-add ~/.ssh/id_ed25519_github1
ssh-add ~/.ssh/id_ed25519_github2
```

#### 2.3.4 验证加载的密钥

```bash
ssh-add -l
```

#### 2.3.5 测试链接

```bash
ssh -T git@github.com
ssh -T git@github1.com
```

### 2.4 clone 代码

```bash
git clone git@github.com:duanhjlt/blog.git
git clone git@github1.com:duan0120/xvm.git
```
