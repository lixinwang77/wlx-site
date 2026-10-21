---
title: 成刻
description: Android 待办应用 Tempo：用 AI 从文本、图片或语音建日程，可选云同步，并接入系统日历与提醒。
pubDate: 2026-08-17
tags: [Android 应用]
cover: /images/works/tempo/cover.png
links:
  - label: 下载 APK
    href: https://tempo-api.wanglix.com/update/latest.apk
---

这是我做的 Android 待办应用「成刻」（Tempo）：把琐事记下来、排进日程，并在该提醒时提醒你。也可完全离线使用；需要时再登录做云同步。

## 能做什么

- 用 AI 从文本、图片或语音创建日程
- 系统分享与快捷设置磁贴，快速提取待办
- 系统日历同步与提醒
- 可选云同步（Google 登录）；不登录也能完整离线用
- 通过 MCP 接入 Cursor、Claude Desktop 等工具

## 下载说明

- 点击上方 **下载 APK** 获取安装包
- 安装时如系统提示「未知来源」，在设置里允许本次安装即可

## 用 MCP 连接 Agent

Tempo MCP 让 Cursor / Claude 等 Agent 在你的账号里创建、列表、更新、完成、删除待办与重复日程（与 App 同一份数据）。

- 端点：`https://tempo-api.wanglix.com/mcp`（Streamable HTTP）
- 认证：OAuth + Google（与 App 云同步同一账号）；普通用户不要粘贴 `TEMPO_API_KEY`
- 发现：
  - `https://tempo-api.wanglix.com/.well-known/oauth-protected-resource`
  - `https://tempo-api.wanglix.com/.well-known/oauth-authorization-server`

连接后可用：`list_todos`、`get_todo`、`create_todo`、`update_todo`、`complete_todo`、`delete_todo`、`list_groups`、`create_group`、`list_repeat_rules`；重复日程用 `repeatFrequency`（`Daily` / `Weekly` / `Monthly` / `Yearly`）。

### 复制给 Agent 的提示词

把下面整段粘贴给 Cursor / Claude（或任意能改 MCP 配置的 Agent）：

```text
请把 Tempo MCP 服务器加到我的 Cursor / Claude Desktop 配置里，并完成 OAuth，让我能在对话里管理 Tempo 待办。

服务器
- 名称：tempo
- URL：https://tempo-api.wanglix.com/mcp
- 传输：Streamable HTTP（远程 URL；不是 stdio / npx）
- 认证：OAuth 2.1 + Google（由 tempo-api 提供，PKCE + 动态客户端注册）。不要向我要 TEMPO_API_KEY，也不要在 mcp.json 里写 API key — 那是仅供机器人/脚本的管理员密钥。

发现端点（tempo-api 是授权服务器；Google 只负责身份）
- https://tempo-api.wanglix.com/.well-known/oauth-protected-resource
- https://tempo-api.wanglix.com/.well-known/oauth-authorization-server

连接成功后应有的工具
- list_todos、get_todo、create_todo、update_todo、complete_todo、delete_todo
- list_groups、create_group
- list_repeat_rules
- 重复日程：create_todo / update_todo 使用 repeatFrequency = Daily | Weekly | Monthly | Yearly
  （可选：repeatInterval、repeatWeekdays、repeatMonthDays、repeatMonths、repeatEndDate、repeatMaxOccurrences；update 时 clearRepeat=true 可清除重复）

验证
1. 按提示完成 Google OAuth 弹窗（使用与 Tempo 云同步相同的 Google 账号）。
2. 调用 list_todos，再用 create_todo 建一条短测试标题（可选 repeatFrequency "Daily"）。
3. 在 Tempo Android 应用：设置 → AI → MCP Agents 应能看到该客户端绑定。
```

### 手动配置与验证

- **Cursor：** 设置 → MCP → 添加远程服务器，URL 填 `https://tempo-api.wanglix.com/mcp` → Google 登录
- **Claude Desktop：** 在 MCP 配置里加 `"tempo": { "url": "https://tempo-api.wanglix.com/mcp" }`，重启后完成 OAuth

验证：让 Agent 列出待办并创建一条测试项；打开 App → **设置 → AI → MCP Agents**，应能看到该客户端绑定。

## 功能展示

![应用界面](/images/works/tempo/app-ui.png)
