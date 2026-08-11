# wlx-site

个人博客 + 作品站，暖色杂志感，准备部署到 **GitHub + Cloudflare Pages**。

## 本地开发

```bash
npm install
npm run dev
```

## 内容怎么写

- 博客：`src/content/blog/*.md`
- 作品：`src/content/works/*.md`
- 站点信息与社交链接：`src/data/site.ts`

## 已实现

- 顶部胶囊导航（博客 / 作品 / 关于）
- 首页简介下的社交图标栏
- 博客与作品分栏
- Collection / Works / GitHub 三入口
- 标签筛选、RSS、基础 SEO
- 克制动效（入场淡入、悬停）

## 部署到 Cloudflare Pages

1. 把仓库推到 GitHub
2. Cloudflare Pages 连接该仓库
3. 构建命令：`npm run build`
4. 输出目录：`dist`
