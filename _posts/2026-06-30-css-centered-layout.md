---
layout: post
title: "CSS 居中布局方案汇总"
date: 2026-06-30 16:00:00 +0800
categories: debug
excerpt: 前端开发中最常见的需求之一：居中。汇总各种场景下的居中方案，再也不怕搞混了。
---

## 前言

"如何居中一个元素" 是前端开发中被问到最多的问题之一。不同场景需要不同的方案，这里做一个系统性的汇总。

## 水平居中

### 内联元素

```css
.parent {
  text-align: center;
}
```

### 块级元素（定宽）

```css
.child {
  width: 300px;
  margin: 0 auto;
}
```

### 块级元素（不定宽）

```css
.child {
  display: table;
  margin: 0 auto;
}

/* 或用 Flexbox */
.parent {
  display: flex;
  justify-content: center;
}
```

## 垂直居中

### 单行文本

```css
.parent {
  height: 60px;
  line-height: 60px;
}
```

### 多行文本 / 块级元素

```css
/* 方案一：Flexbox（推荐） */
.parent {
  display: flex;
  align-items: center;
}

/* 方案二：Grid */
.parent {
  display: grid;
  align-items: center;
}
```

## 水平垂直居中（最常用）

### Flexbox 方案（推荐）

```css
.parent {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

### Grid 方案

```css
.parent {
  display: grid;
  place-items: center;
}
```

> `place-items: center` 是 `align-items: center` 和 `justify-items: center` 的简写，非常简洁！

### 绝对定位 + Transform（兼容性好）

```css
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

### 绝对定位 + Margin（需知宽高）

```css
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: 200px;
  height: 100px;
  margin: auto;
}
```

## 方案对比

| 方案 | 优点 | 缺点 | 推荐场景 |
|------|------|------|----------|
| Flexbox | 灵活、语义清晰 | IE 部分支持 | 现代项目首选 |
| Grid | 代码最简洁 | IE 不支持 | 现代浏览器项目 |
| Transform | 兼容性好 | 可能影响渲染 | 需要兼容旧浏览器 |
| Margin auto | 最古老方案 | 需要知道尺寸 | 简单场景 |

## 常见踩坑

### 坑 1：Flexbox 中图片变形

```css
/* 错误：图片会被拉伸 */
.parent {
  display: flex;
  align-items: center;
}

/* 正确：给图片加 min-height: 0 或包裹一层 */
img {
  min-height: 0;
}
```

### 坑 2：Transform 导致文字模糊

使用 `transform` 居中后，部分浏览器可能导致子元素文字模糊，可以用 `will-change: transform` 或升级到 Flexbox/Grid 方案。

---

总结：**现代项目直接用 Flexbox 或 Grid，老项目用 Transform**。大部分场景一个 Flexbox 就搞定了。
