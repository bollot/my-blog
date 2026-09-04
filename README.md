# 多元志 · Multiverse Blog

基于 **Hugo + GitHub Pages** 搭建的多元化个人博客，支持文章、摄影、项目、笔记四大内容板块，中英文双语，深色模式，站内搜索，推送即部署。

## ✨ 功能特性

| 特性 | 说明 |
|------|------|
| 📝 四大内容板块 | 文章 / 摄影 / 项目 / 笔记，各自独立模板 |
| 🌐 中英文双语 | 一键切换，内容独立管理 |
| 🌙 深色模式 | 支持浅色 / 深色 / 跟随系统 |
| 🔍 站内搜索 | 基于 Fuse.js 的全文搜索 |
| 📑 文章目录 | 自动生成 TOC，支持展开/收起 |
| ⏱️ 阅读时长 | 自动估算阅读时间和字数 |
| 📡 RSS 订阅 | 全站及各分类独立 RSS |
| 🏷️ 分类标签 | 分类 / 标签 / 系列三种归档 |
| 🚀 自动部署 | GitHub Actions 推送即发布 |
| 📱 响应式 | 完美适配手机 / 平板 / 桌面 |

## 🚀 快速开始

### 1. 前置准备

```bash
# 安装 Hugo (extended 版本)
# macOS
brew install hugo

# Windows (Scoop)
scoop install hugo-extended

# 验证
hugo version
```

### 2. 获取项目

```bash
# 方式一：使用这个模板仓库（推荐先 Fork）
git clone https://github.com/yourusername/my-blog.git
cd my-blog

# 方式二：从零创建（参考本项目结构）
hugo new site my-blog
```

### 3. 安装主题

```bash
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git submodule update --init --recursive
```

### 4. 本地预览

```bash
hugo server -D
```

打开浏览器访问 `http://localhost:1313` 即可看到博客。`-D` 参数表示包含草稿文章。

## 📝 如何写内容

### 新建文章

```bash
hugo new posts/my-first-post.md
```

### 新建摄影作品

```bash
hugo new photos/my-photo-set.md
```

### 新建项目展示

```bash
hugo new projects/my-project.md
```

### 新建笔记

```bash
hugo new notes/my-note.md
```

### 内容状态

每篇文章的 front matter 中有 `draft` 字段：
- `draft: true` — 草稿，本地预览可见，线上不发布
- `draft: false` — 正式发布

## 🌐 部署到 GitHub Pages

### 第一步：创建仓库

1. 在 GitHub 创建仓库，命名为 `yourusername.github.io`（个人站点）或任意名称（项目站点）
2. 将本项目推送到仓库

```bash
git remote add origin https://github.com/yourusername/yourusername.github.io.git
git branch -M main
git push -u origin main
```

### 第二步：启用 GitHub Pages

1. 进入仓库 **Settings → Pages**
2. **Source** 选择 **GitHub Actions**
3. 保存

### 第三步：修改配置

编辑 `hugo.toml`，将 `baseURL` 改为你的实际地址：

```toml
# 个人站点
baseURL = "https://yourusername.github.io/"

# 项目站点（仓库名不是 username.github.io 时）
baseURL = "https://yourusername.github.io/repo-name/"
```

同时修改以下占位信息：
- `title` — 博客名称
- `[params].author` — 你的名字
- `[params.socialIcons]` — 社交链接
- `content/about/_index.md` — 关于页面内容

### 第四步：推送部署

```bash
git add .
git commit -m "init: 搭建博客"
git push
```

推送后，GitHub Actions 会自动构建并部署，约 1-2 分钟后即可访问。

## 📂 项目结构

```
my-blog/
├── archetypes/           # 内容模板（新建内容时自动套用）
│   ├── default.md        # 默认模板
│   ├── posts.md          # 文章模板
│   ├── photos.md         # 摄影模板
│   ├── projects.md       # 项目模板
│   └── notes.md          # 笔记模板
├── assets/               # 自定义 CSS/JS
├── content/              # 所有内容
│   ├── posts/            # 📝 文章
│   ├── photos/           # 📷 摄影
│   ├── projects/         # 🛠️ 项目
│   ├── notes/            # 📒 笔记
│   ├── about/            # 关于页面
│   ├── archives.md       # 归档页
│   └── search.md         # 搜索页
├── data/                 # 数据文件
├── layouts/              # 自定义布局
├── static/               # 静态文件（图片等）
│   └── images/           # 图片资源
├── themes/               # 主题（PaperMod）
├── .github/
│   └── workflows/
│       └── hugo.yml      # 自动部署配置
├── hugo.toml             # 站点核心配置
├── .gitignore
└── README.md
```

## ⚙️ 常用自定义

### 修改导航菜单

编辑 `hugo.toml` 中的 `[languages.zh.menu]` 部分。

### 切换默认主题色

```toml
[params]
  defaultTheme = "auto"  # auto(跟随系统) / light / dark
```

### 添加评论系统（Giscus）

在 `hugo.toml` 中启用：

```toml
[params]
  comments = true

[params.giscus]
  dataRepo = "yourusername/yourusername.github.io"
  dataRepoId = "your-repo-id"
  dataCategory = "General"
  dataCategoryId = "your-category-id"
  dataMapping = "pathname"
  dataTheme = "preferred_color_scheme"
```

### 添加网站统计

推荐使用隐私友好的 [Umami](https://umami.is/) 或 [Plausible](https://plausible.io/)，在 `layouts/partials/` 中添加统计代码。

## 🔧 常用命令速查

```bash
hugo server -D              # 本地预览（含草稿）
hugo server --port 8080     # 指定端口
hugo new posts/xxx.md       # 新建文章
hugo --gc --minify          # 生产构建
hugo mod get -u             # 更新主题模块
git submodule update --remote themes/PaperMod  # 更新主题
```

## ❓ 常见问题

**Q: 推送后网站没有更新？**
A: 检查仓库 Settings → Pages 是否选择了 GitHub Actions 作为 Source；查看 Actions 标签页的构建日志。

**Q: 图片不显示？**
A: 图片放在 `static/images/` 目录下，引用路径为 `/images/xxx.jpg`。

**Q: 如何更新主题？**
A: 运行 `git submodule update --remote themes/PaperMod`，然后提交更改。

**Q: 中文排版有问题？**
A: 配置中已设置 `hasCJKLanguage = true`，确保使用 Hugo extended 版本。

## 📄 License

MIT License — 自由使用、修改和分发。

---

> 写下来，是为了更好地思考。
