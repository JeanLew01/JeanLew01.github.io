# 配置与发布

## 当前配置

这是从 al-folio 创建的独立 Git 仓库，默认分支为 `main`。

```yaml
url: https://jeanlew01.github.io
baseurl: ""
```

个人主页使用空 `baseurl`。上游文档里的 `/al-folio` 是主题演示站的路径，不适用于本仓库。

GitHub 远程仓库和线上站点需要完成下列步骤后才会存在。当前目录里的 `origin` 仅配置了目标地址，不代表远程仓库已经创建。

## 1. 创建 GitHub 远程仓库并上传

### 使用浏览器

1. 登录 `JeanLew01`，打开 [GitHub 新建仓库](https://github.com/new)。
2. 仓库名称填写 `JeanLew01.github.io`，可见性选择 **Public**。
3. 创建空仓库：不要勾选初始化 README、`.gitignore` 或许可证，本地已经包含这些文件。
4. 在终端执行：

```bash
cd /home/jixia/JeanLew01.github.io
git push -u origin main
```

HTTPS 推送需要本机可用的 GitHub 身份认证。如果使用 SSH，可先按 GitHub 官方说明配置 SSH，再执行：

```bash
git remote set-url origin git@github.com:JeanLew01/JeanLew01.github.io.git
git push -u origin main
```

### 使用 GitHub CLI

如果已安装 [GitHub CLI](https://cli.github.com/)，执行：

```bash
cd /home/jixia/JeanLew01.github.io
gh auth login --hostname github.com --git-protocol https --web
gh auth setup-git
gh repo create JeanLew01/JeanLew01.github.io --public --description "Academic homepage of Jixian Liu, built with al-folio"
git push -u origin main
```

远程仓库已经存在时，跳过 `gh repo create`。如果其中已有内容，先检查远程历史，不要强制推送覆盖。

## 2. 启用 GitHub Pages

1. 打开仓库的 **Actions**，等待 **Deploy site** 成功；该流程会生成 `gh-pages` 分支。
2. 打开 **Settings → Pages → Build and deployment**。
3. **Source** 选择 **Deploy from a branch**，分支选 **gh-pages**，目录选 **/ (root)**，保存。
4. 等待 Pages 发布完成，访问 <https://jeanlew01.github.io>。

仓库已有部署工作流声明 `contents: write`。如果组织或账号策略限制写权限，按 [al-folio 安装文档](https://github.com/alshedivat/al-folio/blob/main/docs/INSTALL.md) 检查 **Settings → Actions → General → Workflow permissions**。

后续把更新推送到 `main` 后，工作流会重新构建并发布。

## 3. 更新个人资料

- **个人简介**：编辑 `_pages/about.md`，更新单位、研究方向和个人介绍。现有内容来自 2026 年 9 月简历。
- **头像**：添加 `assets/img/profile.jpg`，将 `_pages/about.md` 的 `profile.image` 改为 `profile.jpg`。
- **联系方式**：编辑 `_data/socials.yml`，更新邮箱、Google Scholar ID 等。邮箱已填写为简历中的 `jliu376@jh.edu`。
- **论文**：更新 `_bibliography/papers.bib` 中的 BibTeX。现有 6 篇论文按会议、预印本和期刊分组；4 篇控制与可达性论文已标为首页精选。新增论文需保持作者、年份和发表状态准确。
- **研究概览**：编辑 `_pages/research.md`。
- **教学与服务**：编辑 `_pages/teaching-service.md`，同步更新 `_data/cv.yml` 中的对应记录。
- **项目**：`/projects/` 目前不在导航中。如需启用项目列表，在 `_pages/projects.md` 将 `nav` 改为 `true`，然后在 `_projects/` 创建 Markdown 文件，例如：

```markdown
---
layout: page
title: 项目名称
description: 项目简介
importance: 1
---

项目内容与链接。
```

- **简历**：编辑 `_data/cv.yml`；`assets/json/resume.json` 仅保留同步的联系方式，在线简历以 `_data/cv.yml` 为准。如需 PDF 下载，把文件放到 `assets/pdf/cv.pdf`，将 `_pages/cv.md` 的 `cv_pdf` 设为 `/assets/pdf/cv.pdf`。
- **博客与新闻**：目前入口隐藏，示例内容已清空。需要时可按 `docs/CUSTOMIZE.md` 恢复页面和首页的 `latest_posts` / `announcements` 开关。

示例人物资料、外部博客订阅、演示论文、照片和 CV 已移除。图片自动生成 WebP 的功能暂时关闭；需要时安装 ImageMagick 并启用 `_config.yml` 的 `imagemagick.enabled`。

## 4. 本地预览与检查

### Docker

安装 Docker Engine 和 Compose 插件后：

```bash
cd /home/jixia/JeanLew01.github.io
docker compose up --build
```

访问 <http://localhost:8080/>。停止服务：

```bash
docker compose down
```

### Ruby

安装 Ruby **3.3.5**、Bundler **4.0.6** 和 Node.js 后：

```bash
cd /home/jixia/JeanLew01.github.io
gem install bundler -v 4.0.6
bundle install
npm ci
bundle exec jekyll serve --host 127.0.0.1 --port 4000
```

访问 <http://localhost:4000/>。构建与源码检查：

```bash
npm run lint:prettier
npm run lint:style-contract
bundle exec al-folio upgrade audit --no-fail
JEKYLL_ENV=production bundle exec jekyll build
```

Jekyll 将生成 `_site/`；该目录不会提交到 `main`。上游测试里的演示页面和截图针对 al-folio 演示站，个人网站应检查自身的页面与导航。
