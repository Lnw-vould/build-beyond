# BUILD BEYOND 使用与部署说明

## 先看这里

本包沿用原模板的极简双语设计，已填入 lnw-vould/build-beyond 的网址配置。
原 ZIP 在检查时可完整解压，没有发现损坏。新包重新用标准 ZIP/Deflate 打包，另附已解压目录。
如果 Windows 的“全部解压缩”仍失败，直接使用交付的 build-beyond-site 文件夹即可。
不要通过双击 index.html 判断网站是否正常；它是 Jekyll 源模板，须经 GitHub Pages 构建。

## 保留现有文章

检查时 main 分支为 4302c162ac99d5234734413aec33024206dae571。
仓库已有 README.md 和 articles/freedom-before-wealth.md。
交付包不包含这两个路径，部署时不应替换、删除它们，也不要用整个文件夹覆盖仓库。
新增 _posts/2026-10-09-freedom-before-wealth.md 是原文的完整副本，只在前面增加 Jekyll 元数据。
正文逐字节一致；日期取自该文章的 GitHub 提交时间，并非推测的原始写作时间。
原文开头的标题、作者、“13 minutes ago”等来源文本也完整保留，未做编辑。
原模板的短演示文章未纳入交付包，避免冒充原文。

## 上传到 GitHub

1. 先备份当前仓库。将本包目录内的文件加入仓库根目录；不要上传外层 build-beyond-site 文件夹。
2. 根目录应能直接看到 _config.yml、index.html、_layouts、_posts、assets、about.md、archive.html 等。
3. 建议新建分支并提交 Pull Request，核对差异中没有删除、修改 articles/ 或 README.md。
4. 合并前重新读取 main，检查新增文件路径有无冲突。发生冲突时保留仓库版本，逐项合并，不强制覆盖。
5. 核对并授权后，合并到 main。在 Settings → Pages 中确认 Source 为 Deploy from a branch，Branch 为 main，Folder 为 /(root)。截图显示曾设置此项，但这不是当前设置的实时确认。
6. 等待 Actions 中 Pages 构建部署成功，再打开 https://lnw-vould.github.io/build-beyond/ 。
7. 检查首页、Essays、About、文章页以及移动设备上的样式是否正常。

不要添加 .nojekyll，否则会绕过 Jekyll 处理。若仓库已有 .nojekyll，先核查其用途后再调整。

## 需要用户授权的动作

- 创建远程分支、上传本包文件、创建 Pull Request：会写入 GitHub 仓库，但不会自动发布到 main。
- 合并 Pull Request 或直接提交 main：若 Pages 已启用，会触发公开发布。
- 调整 Pages 来源或 Actions 开关：改变仓库发布设置，需要相应管理权限。

目前只读取仓库并在本地准备交付，未执行上述远程写入或发布动作。

## 后续发布文章

在 _posts 中新增 YYYY-MM-DD-english-slug.md，文件开头使用：

```yaml
---
layout: post
title: "你的文章标题"
date: 2026-10-09 16:00:00 +0800
category: Essays
---
```

在下方写 Markdown 正文。实际日期改为你的发布日期；未来日期的文章默认不会展示。

## 本地预览（可选）

安装 Ruby 和 Bundler 后，在此目录运行 bundle install，再运行 bundle exec jekyll serve。
打开 http://127.0.0.1:4000/build-beyond/ 。部署到 GitHub Pages 不要求你的电脑安装 Ruby。

## 已完成的检查与限制

原压缩包的全部文件通过 CRC 校验和完整解压；19 个下载副本的 SHA-256 相同。
新包通过 Python ZIP CRC 校验及 Windows .NET 解压；所有解压后文件与交付目录的字节一致。
检查了 UTF-8 编码、主要文件、布局引用、路径配置以及文章正文与 GitHub blob 的一致性。
本机没有 Ruby/Jekyll，所以尚未运行真正的 Jekyll 构建，也未验证线上 Pages 发布。
GitHub 上的构建与页面检查应在获得远程写入授权后完成。

官方说明：https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll
发布来源：https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
