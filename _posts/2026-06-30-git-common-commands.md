---
layout: post
title: "Git 常用命令速查"
date: 2026-06-30 14:00:00 +0800
categories: learning
excerpt: 整理 Git 日常开发中最常用的命令，方便随时查阅。
---

## 基本配置

```bash
# 设置用户名和邮箱
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# 查看配置
git config --list
```

## 仓库操作

### 创建仓库

```bash
# 初始化新仓库
git init

# 克隆远程仓库
git clone <url>
```

### 查看状态

```bash
# 查看工作区状态
git status

# 查看提交历史
git log --oneline --graph --all

# 查看简洁日志
git log --oneline -10
```

## 暂存与提交

```bash
# 添加文件到暂存区
git add <file>          # 添加指定文件
git add .               # 添加所有修改

# 提交
git commit -m "commit message"

# 修改最后一次提交
git commit --amend
```

## 分支管理

```bash
# 查看分支
git branch              # 本地分支
git branch -r           # 远程分支
git branch -a           # 所有分支

# 创建分支
git branch <branch-name>

# 切换分支
git checkout <branch-name>
# 或使用新命令
git switch <branch-name>

# 创建并切换分支
git checkout -b <branch-name>
# 或
git switch -c <branch-name>

# 删除分支
git branch -d <branch-name>    # 已合并的分支
git branch -D <branch-name>    # 强制删除

# 合并分支
git merge <branch-name>
```

## 远程操作

```bash
# 查看远程仓库
git remote -v

# 添加远程仓库
git remote add origin <url>

# 推送到远程
git push origin <branch-name>
git push -u origin main     # 首次推送并设置上游

# 拉取远程更新
git pull origin main
git pull --rebase origin main

# 获取远程更新（不合并）
git fetch origin
```

## 撤销操作

```bash
# 撤销工作区修改
git checkout -- <file>
# 或
git restore <file>

# 撤销暂存区
git reset HEAD <file>
# 或
git restore --staged <file>

# 回退版本
git reset --soft HEAD~1     # 保留修改
git reset --hard HEAD~1     # 丢弃修改
```

## 暂存工作区

```bash
# 暂存当前修改
git stash

# 查看暂存列表
git stash list

# 恢复暂存
git stash pop               # 恢复并删除记录
git stash apply              # 恢复但不删除
```

## 实用技巧

### 别名设置

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.st status
git config --global alias.lg "log --oneline --graph --all"
```

### .gitignore 示例

```
# 依赖
node_modules/
vendor/

# 构建产物
dist/
build/

# 环境变量
.env
.env.local

# 系统文件
.DS_Store
Thumbs.db
```

---

掌握这些命令，日常开发基本够用了。建议收藏，随时查阅！
