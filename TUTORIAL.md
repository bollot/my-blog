# 多元志博客搭建完整教程

> 技术栈：Hugo + PaperMod + Sveltia CMS + Netlify
> 预计耗时：20-30 分钟
> 费用：完全免费

---

## 目录

1. [准备工作](#1-准备工作)
2. [获取项目代码](#2-获取项目代码)
3. [修改个人配置](#3-修改个人配置)
4. [推送到 GitHub](#4-推送到-github)
5. [部署到 Netlify](#5-部署到-netlify)
6. [启用 Sveltia CMS 后台](#6-启用-sveltia-cms-后台)
7. [使用后台写文章](#7-使用后台写文章)
8. [本地预览与开发](#8-本地预览与开发)
9. [常见问题](#9-常见问题)

---

## 1. 准备工作

你需要准备以下账号和工具：

### 必需账号
- [GitHub](https://github.com) 账号（免费注册）
- [Netlify](https://netlify.com) 账号（免费注册，可用 GitHub 登录）

### 可选工具（本地写文章时需要）
- [Git](https://git-scm.com/downloads)（版本控制）
- [Hugo](https://gohugo.io/installation/) extended 版本（本地预览）

> 如果只想用后台网页写文章，不需要安装任何工具，全部在浏览器里完成。

---

## 2. 获取项目代码

### 方式一：下载压缩包（最简单）

1. 下载 `my-blog.zip` 并解压到本地
2. 解压后得到 `my-blog` 文件夹

### 方式二：用 Git 克隆（如果你熟悉 Git）

```bash
git clone <你的仓库地址> my-blog
cd my-blog
git submodule update --init --recursive
```

---

## 3. 修改个人配置

打开 `my-blog/hugo.toml` 文件，修改以下占位信息：

### 3.1 基本信息

```toml
# 第 8 行左右：改成你的 Netlify 站点地址（部署后会得到）
baseURL = "https://你的站点名.netlify.app/"

# 第 11 行：博客标题
title = "你的博客名"

# 找到 [params] 部分，修改作者和描述
[params]
  author = "你的名字"
  description = "你的博客描述"
```

### 3.2 社交链接

找到 `[[params.socialIcons]]` 部分，改成你的实际链接：

```toml
[[params.socialIcons]]
  name = "github"
  url = "https://github.com/你的GitHub用户名"

[[params.socialIcons]]
  name = "email"
  url = "mailto:你的邮箱@example.com"
```

### 3.3 关于页面

打开 `content/about/_index.md`，修改为你自己的介绍内容。

### 3.4 后台配置

打开 `static/admin/config.yml`，修改站点地址：

```yaml
site_url: https://你的站点名.netlify.app/
display_url: https://你的站点名.netlify.app/
```

> 这一步也可以等 Netlify 部署完成、拿到域名后再回来改。

---

## 4. 推送到 GitHub

### 4.1 创建 GitHub 仓库

1. 登录 GitHub，点击右上角 **+** → **New repository**
2. Repository name 填 `my-blog`（或任意名字）
3. 选择 **Public**（公开，Netlify 免费版需要公开仓库）
4. **不要**勾选 "Add a README file"
5. 点击 **Create repository**

### 4.2 上传代码

在 `my-blog` 文件夹内打开终端（Windows 用 Git Bash，Mac 用终端），执行：

```bash
cd my-blog

# 初始化 Git（如果还没有）
git init
git branch -M main

# 添加主题子模块
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod

# 提交代码
git add .
git commit -m "init: 多元志博客"

# 关联远程仓库（地址换成你自己的）
git remote add origin https://github.com/你的用户名/my-blog.git
git push -u origin main
```

> 如果下载的 zip 里已经包含 themes/PaperMod，跳过 `git submodule add` 那一步，直接 `git add .` 即可。

---

## 5. 部署到 Netlify

### 5.1 导入项目

1. 登录 [Netlify](https://app.netlify.com)
2. 点击 **Add new site** → **Import an existing project**
3. 选择 **GitHub**
4. 授权 Netlify 访问你的 GitHub 账户
5. 选择刚才创建的 `my-blog` 仓库

### 5.2 配置构建

在部署设置页面，填写：

| 字段 | 值 |
|------|-----|
| Branch to deploy | `main` |
| Build command | `hugo --gc --minify` |
| Publish directory | `public` |

然后点击 **Show advanced** → **New variable**，添加一个环境变量：

| Key | Value |
|-----|-------|
| `HUGO_VERSION` | `0.149.0` |

> 这一步很重要，Netlify 默认的 Hugo 版本可能太低，会导致构建失败。

点击 **Deploy site** 开始部署。

### 5.3 等待部署完成

第一次部署约 1-2 分钟。部署成功后，Netlify 会给你一个随机域名，比如 `random-name-123.netlify.app`。

### 5.4 修改站点名（可选但推荐）

1. 进入站点 → **Site configuration** → **Change site name**
2. 改成你喜欢的名字，比如 `my-blog`
3. 你的站点地址就变成 `https://my-blog.netlify.app`

### 5.5 绑定自定义域名（可选）

如果你有自己的域名：
1. **Site configuration** → **Domain management** → **Add a domain**
2. 输入你的域名，按提示在域名服务商处配置 DNS
3. Netlify 会自动签发 HTTPS 证书

---

## 6. 启用 Sveltia CMS 后台

### 6.1 启用 Identity

1. 进入 Netlify 站点 → **Site configuration** → 左侧菜单找到 **Identity**
2. 点击 **Enable Identity**

### 6.2 设置注册方式

1. 在 Identity 页面，找到 **Registration** → **Edit settings**
2. 选择 **Invite only**（仅邀请），这样只有你能注册
3. 保存

### 6.3 邀请自己

1. 在 Identity 页面，点击 **Invite users**
2. 输入你的邮箱
3. 点击 **Send**
4. 去邮箱查收邀请邮件，点击邮件中的链接完成注册（设置密码）

### 6.4 启用 Git Gateway

1. **Site configuration** → **Services** → **Git Gateway**
2. 点击 **Enable Git Gateway**
3. 按照提示连接 GitHub（授权 Netlify 访问你的仓库）

### 6.5 登录后台

访问 `https://你的站点.netlify.app/admin/`，用刚才注册的邮箱和密码登录。

登录成功后，你会看到四个内容分类：文章、摄影、项目、笔记。

---

## 7. 使用后台写文章

### 7.1 新建文章

1. 登录后台后，点击左侧 **文章**
2. 点击右上角 **New 文章**
3. 填写表单：
   - **标题**：文章标题
   - **发布日期**：自动填充当前时间，可修改
   - **草稿**：关闭表示直接发布，开启表示仅保存草稿
   - **分类**：如「技术」「生活」
   - **标签**：多个标签用回车分隔
   - **摘要**：文章列表页显示的简介
   - **封面图**：上传一张封面图片
   - **正文**：富文本编辑器，支持图片、代码块、列表等

4. 点击右上角 **Publish**（发布）

发布后，Netlify 会自动重新构建部署，约 30 秒后文章就会出现在博客上。

### 7.2 上传图片

在正文中点击图片图标，或直接拖拽图片到编辑器，图片会自动上传到 GitHub 仓库的 `static/images/uploads/` 目录。

### 7.3 编辑已有内容

在后台列表中点击任意文章即可编辑，修改后点击 **Publish** 会自动提交到 GitHub 并重新部署。

### 7.4 四种内容类型

| 类型 | 专属字段 | 用途 |
|------|----------|------|
| 文章 | 分类、标签、系列 | 深度长文 |
| 摄影 | 拍摄地点、相机、镜头 | 摄影作品 |
| 项目 | 技术栈、状态、仓库/演示链接 | 项目展示 |
| 笔记 | 无额外字段 | 碎片思考 |

---

## 8. 本地预览与开发

如果你想在本地预览效果或用 Markdown 直接写文章：

### 8.1 安装 Hugo

```bash
# macOS
brew install hugo

# Windows (用 Scoop)
scoop install hugo-extended

# 验证
hugo version
```

### 8.2 启动本地服务器

```bash
cd my-blog
hugo server -D
```

打开浏览器访问 `http://localhost:1313`，修改内容后页面会自动刷新。

### 8.3 用命令新建内容

```bash
hugo new posts/我的新文章.md
hugo new photos/摄影集.md
hugo new projects/项目名.md
hugo new notes/笔记标题.md
```

然后用任意 Markdown 编辑器打开生成的文件编写。

### 8.4 推送到线上

```bash
git add .
git commit -m "新增文章：xxx"
git push
```

推送后 Netlify 自动部署。

---

## 9. 常见问题

### Q: 部署失败怎么办？

A: 进入 Netlify 站点 → **Deploys**，点击失败的部署查看日志。最常见的原因是 `HUGO_VERSION` 环境变量没设置。

### Q: 后台登录提示 "Git Gateway is not enabled"？

A: 回到 Netlify → **Site configuration** → **Services** → **Git Gateway**，确认已启用并连接了 GitHub。

### Q: 收不到邀请邮件？

A: 检查垃圾邮件文件夹。如果还是没有，在 Identity 页面重新发送邀请。

### Q: 文章发布后网站没更新？

A: Netlify 构建需要 30 秒到 1 分钟。可以在 **Deploys** 页面查看构建状态，确认显示 "Published" 后再刷新网站。

### Q: 图片不显示？

A: 检查图片路径。通过后台上传的图片路径是 `/images/uploads/xxx.jpg`，确保 `static/admin/config.yml` 中的 `public_folder` 设置正确。

### Q: 如何修改导航菜单？

A: 编辑 `hugo.toml` 中的 `[languages.zh.menu]` 部分，增删菜单项。

### Q: 如何切换深色/浅色模式？

A: 博客右上角有主题切换按钮。默认是跟随系统，可在 `hugo.toml` 中修改 `defaultTheme` 为 `light` 或 `dark`。

### Q: Netlify 免费额度够用吗？

A: 个人博客完全够用。免费版 300 credits/月，个人博客通常消耗不到 100 credits/月。

### Q: 想换回 GitHub Pages 部署？

A: 项目里已经包含 `.github/workflows/hugo.yml`，推送到 GitHub 后在仓库 Settings → Pages 选择 GitHub Actions 即可。但 GitHub Pages 方式下 Sveltia CMS 需要额外配置 OAuth 代理。

---

## 10. 下一步

- [ ] 写第一篇真正的文章
- [ ] 替换示例内容（项目里自带了 4 篇示例，可删除）
- [ ] 配置自定义域名
- [ ] 接入评论系统（Giscus）
- [ ] 添加网站统计（Umami / Plausible）
- [ ] 配置 SEO 优化

> 有任何问题，参考项目根目录的 `README.md`，或在 Netlify / GitHub 文档中查找。
