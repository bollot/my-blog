---
title: "多元志博客系统"
date: 2026-09-01T14:00:00+08:00
draft: false
categories: ["项目"]
tags: ["Hugo", "博客", "开源"]
tech: ["Hugo", "PaperMod", "GitHub Actions", "GitHub Pages"]
status: "已完成"
repo: "https://github.com/yourusername/my-blog"
demo: "https://yourusername.github.io/"
summary: "基于 Hugo 和 GitHub Pages 搭建的多元化个人博客，支持文章、摄影、项目、笔记四大内容板块，中英文双语。"
cover:
  image: "/images/project-cover.jpg"
  alt: "多元志博客"
  caption: "博客首页预览"
  relative: false
---

## 项目简介

多元志是一个支持多种内容类型的个人博客系统。不同于传统博客只有"文章"一种形式，它将内容分为**文章**、**摄影**、**项目**、**笔记**四个独立板块，每种类型有专属的模板和元数据字段。

## 技术栈

| 层级 | 技术 |
|------|------|
| 静态生成 | Hugo (extended) |
| 主题 | PaperMod |
| 部署 | GitHub Pages |
| CI/CD | GitHub Actions |
| 版本控制 | Git + GitHub |

## 核心功能

- ✅ 四大内容板块，各自独立的模板
- ✅ 中英文双语切换
- ✅ 深色 / 浅色 / 自动三种主题模式
- ✅ 站内全文搜索
- ✅ 文章目录、阅读时长、字数统计
- ✅ RSS 订阅
- ✅ 分类、标签、系列三种归档方式
- ✅ 推送即部署的自动化流程

## 项目结构

```
my-blog/
├── archetypes/     # 内容模板
├── content/        # 内容（posts/photos/projects/notes）
├── static/         # 静态资源
├── layouts/        # 自定义布局
├── hugo.toml       # 站点配置
└── .github/        # CI/CD 配置
```

## 后续计划

- [ ] 接入评论系统（Giscus）
- [ ] 添加相册瀑布流布局
- [ ] 接入网站统计（Plausible / Umami）
- [ ] 优化 SEO 和结构化数据
