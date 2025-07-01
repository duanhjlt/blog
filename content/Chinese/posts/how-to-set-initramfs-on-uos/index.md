---
keywords: ['blog']
title: '在uos（统信）系统上设置initramfs'
date: 2025-07-01T22:44:59+08:00
lastmod: 2025-07-01T22:44:59+08:00
draft: false
description: '以lsm驱动test_lsm.ko为例'
author: 'duanhongjin'
tags: ['uos']
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

## 将驱动放到响应的目录，并更新模块依赖

```bash
sudo cp test_lsm.ko /lib/modules/4.19.0-arm64-desktop/kernel/security/test_lsm/
sudo depmod -a 4.19.0-arm64-desktop
```

## 将模块添加到 initramfs
### 编辑 initramfs 的模块配置文件
```bash
sudo vim /etc/initramfs-tools/modules
```

### 在文件末尾增加模块名称(不含.ko后缀)
```ini
test_lsm
```

### 更新initramfs

```bash
sudo update-initramfs -u -k 4.19.0-arm64-desktop
```

## 更新GRUB配置
```bash
sudo update-grub
```

## 重启

```bash
sudo reboot
```
