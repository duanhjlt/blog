---
keywords: ['git', 'mirror', 'bare', '迁移', 'blog']
title: 'Git 仓库迁移'
date: 2024-01-06T12:20:23+08:00
lastmod: 2024-01-06T12:20:23+08:00
draft: false
description: 
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
git 仓库迁移，一般分为两种情况，从仓库 **A** 迁移到仓库 **B** 和从本地直接上传到仓库 **B**。  

## 从仓库 **A** 迁移到仓库 **B**  
这种方式比较常见，也有很多 web 端直接支持镜像的方式，但批量的迁移还是要使用命令的，如下：

```bash
$ git clone --bare http://a.com/crazykids.git
$ git push --mirror http://b.com/crazykids.git
```

### 从本地直接上传到仓库 **B**
有的时候需要将本地仓库直接全部 push 到仓库 **B**，比如仓库 **A** 真的的挂了，或者你有多仓库备份的习惯。一般 push 命令只能将当前 branch 或者已经 checkout 出来的分支 push 的远端。

#### 增加仓库 **B** 地址

```bash
$ git remote add B http://b.com/crazykids.git
```

#### 方式1，checkout 所有分支

```bash
$ git fetch origin

$ git branch -r | grep origin | grep -v HEAD|while read rb;do lb=$(echo ${rb}|cut -d/ -f 2-);git checkout -b $lb $rb;done

$ git branch -r | grep origin | grep -v HEAD|while read rb;do lb=$(echo ${rb}|cut -d/ -f 2-);git push -f B $lb;done

$ git push --tags
```

不但命令麻烦，如果遇到分支差异比较大的，还经常出现问题。

#### 方式2

```bash
$ git fetch origin

$ git push B 'refs/remotes/origin/*':'refs/heads/*' 'refs/tags/*':'refs/tags/*'
```
