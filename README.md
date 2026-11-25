<div align="center">

<img src="docs/preview.png" alt="我花的博客" width="100%" />

<br />
<br />

# 我花

一个用 Hugo 搭建的极简博客 · **[wohuaai.com](https://www.wohuaai.com)**

[![Hugo](https://img.shields.io/badge/Hugo-0.170-FF4088?logo=hugo&logoColor=white)](https://gohugo.io/)
[![Vercel](https://img.shields.io/badge/Deployed%20on-Vercel-000000?logo=vercel&logoColor=white)](https://vercel.com/)
[![License](https://img.shields.io/badge/License-MIT%20%2B%20CC%20BY--NC--SA-3DA639)](#许可)
[![Last Commit](https://img.shields.io/github/last-commit/wohuaai/mywebsite?color=blue&label=last%20commit)](https://github.com/wohuaai/mywebsite/commits/main)

写点读书笔记、技术折腾，和一些没头没尾的想法。

</div>

---

## 这是什么

一个**纯静态**的个人博客。没有数据库、没有后端、没有后台管理系统：

```
Markdown 文件  →  Hugo 编译  →  静态 HTML  →  Vercel CDN
```

- **内容**：`content/cn/` 下的 Markdown，Git 就是数据库
- **外观**：Hugo 主题 [hugo-ht](https://github.com/hongtaoh/hugo-ht)，固化在 `themes/` 里
- **部署**：推送到 `main` → Vercel 自动构建 → 约 1 分钟上线
- **评论**：giscus（数据存在 GitHub Discussions）

## 技术栈

| 层 | 选型 |
|---|---|
| 静态站点生成 | [Hugo](https://gohugo.io/) ≥ 0.147.9 |
| 主题 | [hugo-ht](https://github.com/hongtaoh/hugo-ht)（MIT） |
| 托管 / CDN | [Vercel](https://vercel.com/) Hobby |
| 域名 / DNS | 阿里云 + Cloudflare |
| 评论 | [giscus](https://giscus.app/zh-CN) |
| 版本管理 | Git / GitHub |

## 本地开发

```bash
# 确认 Hugo 版本
hugo version

# 预览（含草稿）
hugo server -D
# → http://localhost:1313/

# 只构建，验证有没有错误
hugo --quiet
```

## 写一篇新文章

```bash
hugo new content/cn/posts/2026-12-01-my-post.md
```

头部字段：

```yaml
---
title: "文章标题"
date: 2026-12-01          # 决定 URL，发布后不要改
author: "我花"
slug: "my-post"           # 留空则用文件名
draft: false              # true = 只在本地可见
toc: false                # true = 显示右侧目录
tags: ["随笔", "Hugo"]
---
```

发布：

```bash
git add .
git commit -m "新增：文章标题"
git push
```

## 目录结构

```text
content/cn/            文章与页面
├── _index.md          首页正文
├── about/             关于页
└── posts/             文章

layouts/               模板覆盖（优先于主题）
├── _default/          列表页
└── partials/          评论、<head>

static/
├── css/custom.css     自定义样式
└── media/             logo、favicon

themes/hugo-ht/        主题本体（不要直接改）
config.toml            站点配置
```

## 部署配置

Vercel 项目设置里两项关键配置：

| 项 | 值 |
|---|---|
| 环境变量 `HUGO_VERSION` | `0.170.1` |
| Build Command | `hugo --gc --minify` |

`baseURL` 写在 `config.toml` 里（`https://www.wohuaai.com`），构建命令不再传 `-b`。

## 许可

- **代码**（模板、样式、脚本）：MIT
- **文章内容**：[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh-hans) — 署名 · 非商业性使用 · 相同方式共享

---

<div align="center">
<sub>Built with Hugo · Deployed on Vercel</sub>
</div>
