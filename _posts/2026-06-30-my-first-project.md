---
layout: post
title: "我的第一个项目复盘：个人博客搭建"
date: 2026-06-30 18:00:00 +0800
categories: project
excerpt: 从零开始搭建个人博客的完整过程复盘，包含技术选型、遇到的问题和解决方案。
---

## 项目背景

一直想要一个属于自己的博客平台，既能记录学习过程，也能分享技术经验。与其使用现成的博客平台，不如自己动手搭建一个，顺便学习一些新技术。

## 技术选型

### 为什么选择 Jekyll + GitHub Pages？

| 方案 | 优点 | 缺点 |
|------|------|------|
| Jekyll + GitHub Pages | 免费托管、自动部署、Markdown 编写 | 动态功能有限 |
| WordPress | 功能强大、插件丰富 | 需要服务器、维护成本高 |
| 纯手写 HTML/CSS | 完全自定义 | 维护文章不方便 |

最终选择 Jekyll + GitHub Pages，原因：

1. **免费** — GitHub Pages 提供免费托管
2. **简单** — 用 Markdown 写文章，专注内容
3. **自动化** — Push 代码后自动构建部署
4. **版本控制** — 所有内容都在 Git 中管理

## 项目结构

```
KayerH.github.io/
├── _config.yml          # Jekyll 配置
├── _layouts/            # 布局模板
│   ├── default.html     # 默认布局
│   ├── home.html        # 首页布局
│   └── post.html        # 文章布局
├── _includes/           # 可复用组件
├── _posts/              # 文章（Markdown）
├── assets/              # 静态资源
│   └── css/style.css    # 自定义样式
├── index.html           # 首页
├── about.md             # 关于页
└── blog.md              # 博客列表
```

## 关键设计决策

### 1. 响应式设计

使用 CSS Grid 和 Flexbox 实现响应式布局，通过媒体查询适配不同屏幕：

```css
@media (max-width: 768px) {
  .post-grid {
    grid-template-columns: 1fr;
  }
}
```

### 2. 分类系统

通过 Jekyll 的 `categories` 字段实现文章分类，在 Front Matter 中声明：

```yaml
---
categories: learning
---
```

### 3. 配色方案

- 主色：`#3273dc`（蓝色）
- 背景：`#ffffff` / `#f8f9fa`
- 文字：`#2c3e50`

## 遇到的问题

### 问题 1：本地预览

Windows 环境下配置 Ruby 和 Jekyll 比较麻烦，最终选择直接 Push 到 GitHub 看效果。

> **解决方案**：利用 GitHub Pages 的自动构建能力，省去本地环境的配置。

### 问题 2：中文文件名

Jekyll 默认对中文文件名支持不够好。

> **解决方案**：文章文件名使用英文 + 日期格式，如 `2026-06-30-hello-world.md`。

## 下一步计划

- [ ] 添加评论系统（Giscus）
- [ ] 添加搜索功能
- [ ] 优化 SEO
- [ ] 添加文章标签云
- [ ] 完善 RSS 订阅

## 总结

这次博客搭建让我学到了：

1. Jekyll 的基本用法和 Liquid 模板语法
2. GitHub Pages 的部署流程
3. 响应式设计的实践
4. 项目规划与执行的方法论

虽然只是一个简单的博客，但"麻雀虽小，五脏俱全"。动手做，比只看教程收获大得多。
