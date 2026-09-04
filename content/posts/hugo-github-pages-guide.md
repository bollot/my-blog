---
title: "用 Hugo + GitHub Pages 搭建个人博客的完整指南"
date: 2026-09-01T10:00:00+08:00
draft: false
categories: ["技术"]
tags: ["Hugo", "GitHub Pages", "博客搭建"]
series: ["博客搭建系列"]
summary: "从零开始，用 Hugo 静态站点生成器和 GitHub Pages 免费搭建一个属于自己的个人博客，包含主题选择、自动部署和自定义配置。"
cover:
  image: "/images/blog-cover.jpg"
  alt: "Hugo + GitHub Pages"
  caption: "Hugo + GitHub Pages = 免费个人博客"
  relative: false
---

## 为什么选择 Hugo？

在众多静态站点生成器中，Hugo 有几个显著优势：

- **构建速度极快**：即使上千篇文章也能在几秒内完成构建
- **单二进制部署**：无需复杂的运行环境，一个二进制文件搞定
- **主题生态丰富**：PaperMod、Stack、LoveIt 等优质主题可选
- **GitHub Pages 友好**：通过 Actions 可以实现推送即部署

## 准备工作

1. 注册 GitHub 账号
2. 安装 Git
3. 安装 Hugo（推荐 extended 版本）

```bash
# macOS
brew install hugo

# Windows (Scoop)
scoop install hugo-extended

# 验证安装
hugo version
```

## 创建站点

```bash
hugo new site my-blog
cd my-blog
git init
```

## 安装主题

以 PaperMod 为例：

```bash
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

## 配置自动部署

在 `.github/workflows/` 下创建 `hugo.yml`，推送到 main 分支后自动构建并发布到 GitHub Pages。

## 常用命令

```bash
hugo server -D          # 本地预览（含草稿）
hugo new posts/my-post.md  # 新建文章
hugo                    # 构建生产版本
```

## 小结

Hugo + GitHub Pages 的组合完全免费、速度快、维护成本低，非常适合个人博客。接下来你只需要专注于写作本身。
