---
keywords: ['blog']
title: '为 Docker 配置 HTTP/HTTPS 代理'
date: 2025-07-01T22:30:06+08:00
lastmod: 2025-07-01T22:30:06+08:00
draft: false
description: 
author: 'duanhongjin'
tags: ['docker']
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
## 🔧 1. 确认你的代理本地端口
假设你本地代理端口是：

- HTTP(S) 代理地址：127.0.0.1:7890（Clash 默认）

- 或 SOCKS5 代理地址：127.0.0.1:1080（Shadowsocks 默认）

我们以下以 HTTP 代理为例。

## 🛠️ 2. 创建 Docker 的代理配置文件

```bash
sudo mkdir -p /etc/systemd/system/docker.service.d
sudo nano /etc/systemd/system/docker.service.d/http-proxy.conf
```

内容如下
```ini
[Service]
Environment="HTTP_PROXY=http://127.0.0.1:7890"
Environment="HTTPS_PROXY=http://127.0.0.1:7890"
Environment="NO_PROXY=localhost,127.0.0.1,::1"
```

## 🔄 3. 重新加载并重启 Docker 服务

```bash
sudo systemctl daemon-reexec
sudo systemctl daemon-reload
sudo systemctl restart docker
```

## ✅ 4. 验证代理是否生效

- 查看代理环境变量是否生效：

```bash
systemctl show --property=Environment docker
```

- 查看 Docker 拉镜像报错日志：

```bash
journalctl -u docker.service -n 100 --no-pager
```