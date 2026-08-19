---
title: Obsidian 笔记同步
description: 用绿联 NAS、Remotely Save 和节点小宝，实现 Obsidian 局域网与外网同步。
pubDate: 2026-08-19
tags: [笔记]
---

## 前期准备

1. 绿联 NAS
2. 节点小宝
3. Remotely Save 插件（Obsidian 社区插件，可用 WebDAV 把笔记库同步到 NAS）

## 局域网同步

1. 查看绿联 NAS 的网络 IP 地址。
2. 打开绿联 NAS 的 WebDAV 服务。

> 控制面板 → 文件服务 → WebDAV

![绿联 NAS WebDAV 设置](/images/blog/obsidian-sync/01-webdav-settings.png)

3. 记住 WebDAV 中的端口号（后面要用）。
4. 在 Remotely Save 插件中，选择 **WebDAV** 远程服务，并设置 Server Address、Username、Password。
   - **Server Address**：填写 `http://网络IP地址:5005/存在Obsidian仓库的目录`
   - **Username**：填写绿联 NAS 的账户
   - **Password**：填写绿联 NAS 的密码

## 外网同步

1. 在绿联 NAS 中注册并登录节点小宝账户。

![节点小宝账户](/images/blog/obsidian-sync/02-jiedianxiaobao-account.png)

2. 打开异地组网功能，并记住这个异地组网 IP 地址。

![异地组网 IP](/images/blog/obsidian-sync/03-remote-network-ip.png)

3. 在使用 Obsidian 的设备上也安装节点小宝，并打开节点小宝的异地组网功能。
4. 在 Remotely Save 插件中，选择 **WebDAV** 远程服务，并设置 Server Address、Username、Password。
   - **Server Address**：填写 `http://异地组网IP地址:5005/存在Obsidian仓库的目录`
   - **Username**：填写绿联 NAS 的账户
   - **Password**：填写绿联 NAS 的密码

> 也可以用内网穿透功能：打开后会得到一串域名来访问绿联 NAS，不过内网穿透并不是免费的。
