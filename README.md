# KayerH.github.io

我的个人博客，使用 Jekyll + GitHub Pages 构建。

## 本地运行

```bash
bundle install
bundle exec jekyll serve
```

访问 http://localhost:4000

## 文章分类

- 📖 学习笔记 (learning)
- 🚀 项目复盘 (project)
- 🐛 踩坑记录 (debug)
- 💡 技术分享 (tech)
- 📚 读书笔记 (reading)

## 写文章

在 `_posts/` 目录下创建 `.md` 文件，命名格式：`YYYY-MM-DD-title.md`

```yaml
---
layout: post
title: "文章标题"
date: YYYY-MM-DD HH:MM:SS +0800
categories: category_name
excerpt: 文章摘要
---
```

Push 到 GitHub 后自动部署。
