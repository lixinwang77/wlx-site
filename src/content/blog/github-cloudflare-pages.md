---
title: GitHub + Cloudflare 建站
description: 用 GitHub 存源码、Cloudflare Pages 构建部署，把静态网站快速发布上线。
pubDate: 2026-08-13
tags: [建站, GitHub, Cloudflare]
---

## 为什么是这套组合

- GitHub：存源码、版本管理
- Cloudflare Pages：免费、快、自动构建部署
- 适合：博客、作品站、文档站等静态站（Astro / Hugo / Vite 等）

## GitHub 导入网站源码

1. 打开 [https://github.com](https://github.com)，登录你的账号
2. 右上角 **+** → **New repository**

![右上角新建仓库入口](/images/blog/github-cloudflare/00-new-repository-menu.jpeg)

3. 填写仓库信息：
   - **Repository name**：比如 `wlx-site`（或你想要的名字）
   - **Description**：可选，比如「个人博客与作品站」
   - **Public / Private**：按你需求选
   - 如果本地已经有网站源码和提交了，不要勾选 **Add a README**、**Add .gitignore**、**Choose a license**（勾了之后再推本地代码，容易冲突）
4. 点 **Create repository**，创建后会看到如何把本地代码 push 上去的指南

![创建仓库后的推送指引](/images/blog/github-cloudflare/00-after-create-repo.jpeg)

5. 按页面提示，把本地网站源码推到刚建好的仓库。推送完成后，在 GitHub 仓库页面应能看到 `package.json`、`src/` 等源码文件。

## Cloudflare 构建部署网站

1. Cloudflare 新建应用

![Cloudflare 新建应用](/images/blog/github-cloudflare/01-create-app.png)

2. 连接 GitHub

![连接 GitHub](/images/blog/github-cloudflare/02-connect-github.png)

![授权 Cloudflare 访问 GitHub](/images/blog/github-cloudflare/03-connect-github-auth.png)

3. 导入现有的 git 仓库。

![导入现有 Git 仓库](/images/blog/github-cloudflare/04-import-repo.png)

![选择要部署的仓库](/images/blog/github-cloudflare/05-select-repo.png)

4. 填写网站构建参数。

- Build command 需要填 `npm run build`
- Build output directory 需要填 `dist`

注意：如果连接的 GitHub 仓库里是 `dist`，那么就不用填 Build command 和 Build output directory。

![填写构建参数](/images/blog/github-cloudflare/06-build-config.png)

5. 等待几分钟，看到这个界面就是创建成功了。域名是 https://wlx-site.pages.dev/

![部署成功](/images/blog/github-cloudflare/07-deploy-success.png)
