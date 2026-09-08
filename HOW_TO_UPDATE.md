# 网站维护速查（HOW TO UPDATE）

这个网站的内容全部是**数据/内容文件驱动**的——日常更新基本不需要碰任何 HTML/CSS/配置。改完 `git add -A && git commit -m "..." && git push`，GitHub Actions 会自动重新构建并发布（约 2–5 分钟生效）。

## 常见操作

### 添加一条 News（首页动态）
在 `_news/` 下新建一个 `.md` 文件，文件名随意（建议 `YYYY-MM-简短描述.md`），内容模板：

```markdown
---
layout: post
date: 2026-09-01 09:00:00+0800
inline: true
related_posts: false
---

一句话动态内容，可以带[链接](https://example.com)。
```

首页最多显示 5 条（在 `_pages/about.md` 的 `announcements.limit` 里改）。

### 添加一个研究项目
1. 把项目图片放到 `assets/img/projects/<项目短名>/`（保持现有目录约定）。
2. 在 `_projects/` 下新建 `.md` 文件，参考现有 5 个项目文件。头部字段：
   - `title` / `description`：卡片上显示的标题和一句话简介
   - `img`：卡片封面图路径
   - `importance`：排序权重，数字越小越靠前
   - `category: research`：保持不变（如新增类别，需同步 `_pages/projects.md` 的 `display_categories`）
3. 正文用 Markdown 写，插图用：
   ```
   {% include figure.liquid path="assets/img/projects/xxx/fig.png" title="fig" class="img-fluid rounded z-depth-1" %}
   ```

### 添加一篇论文/出版物
编辑 `_bibliography/papers.bib`，追加一条 BibTeX 条目即可，Publications 页会自动按年份分组渲染。常用可选字段：
- `selected = {true}`：让该文出现在首页 "selected publications"
- `preview = {projects/xxx/fig.jpeg}`：配图（放在 `assets/img/` 下的相对路径）
- `abbr = {PRL}`：期刊缩写徽章（配色在 `_data/venues.yml` 里定义）
- `pdf = {...}` / `arxiv = {...}` / `html = {...}`：生成对应链接按钮
- 想让合作者名字变成链接：编辑 `_data/coauthors.yml`

### 更新 CV
- 网页版 CV：编辑 `_data/cv.yml`（结构化 YAML，仿照现有条目增删）。
- PDF 版 CV：用新的 PDF 覆盖 `assets/pdf/CV_general.pdf`（文件名不变就不用改任何配置）。

### 更换头像
把自己的照片命名为 `prof_pic.jpg` 放进 `assets/img/`，覆盖占位图。方形、≥800×800 像素效果最佳。

### 修改个人简介 / 研究兴趣
编辑 `_pages/about.md` 的正文部分。

### 添加学术链接（Google Scholar / ORCID / LinkedIn）
编辑 `_data/socials.yml`，取消注释并填入对应 ID 即可，图标会自动出现在首页底部。

## 本地预览（可选）

不装本地环境也能维护——改完 push 即可。但本地预览更快：

1. 安装 [RubyInstaller](https://rubyinstaller.org/)（Ruby 3.x，带 MSYS2）。
2. 在 `site/` 目录运行：
   ```bash
   bundle install
   bundle exec jekyll serve
   ```
3. 浏览器打开终端里显示的地址（通常是 http://localhost:4000）。

## 注意事项

- **不要**把 `_config.yml` 里的 `baseurl` 改成非空——本站部署在根路径。
- 新增插件需要同时改 `Gemfile` 和 `_config.yml` 的 `plugins:` 列表（两处必须一致）。
- 构建产物 `_site/` 已被 `.gitignore` 排除，不用管。
- 模板官方更新：仓库保留了 `upstream` 远程（https://github.com/alshedivat/al-folio），需要时可 `git fetch upstream` 后手动挑选合并。
