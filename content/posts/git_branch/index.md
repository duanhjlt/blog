---
keywords: []
title: 'git 分支操作常用命令'
date: 2024-01-04T22:35:39+08:00
lastmod: 2024-01-04T22:35:39+08:00
draft: false
description: 
author: 'duanhongjin'
tags: 
    - 'blog'
    - 'git'
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

## 查看所有分支

```bash
$ git branch -a
```

## 查看远程分支

```bash
$ git branch -r
```

## 查看本地分支所关联的远程分支

```bash
$ git branch -vv
```

## 重命名本地分支

```bash
$ git branch -m old_branch new_branch
```

## 删除远程分支

```bash
$ git branch -d -r origin/old_branch
$ git push origin :old_branch
```

## 推送新的分支

```bash
$ git push -u origin new_branch
```

## 设置关联

```bash
$ git branch --set-upstream-to=origin/branch branch
```
