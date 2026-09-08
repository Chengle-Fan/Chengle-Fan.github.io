# 网站维护速查（HOW TO UPDATE）

这个网站的内容全部是**数据/内容文件驱动**的——日常更新基本不需要碰任何 HTML/CSS/配置。改完 `git add -A && git commit -m "..." && git push`，GitHub Actions 会自动重新构建并发布（约 2–5 分钟生效）。

## 常见操作

### 添加一条 Update（首页动态）

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

首页最多显示 3 条（在 `_pages/about.md` 的 `announcements.limit` 里改）。

### 添加一个研究项目

1. 把项目图片放到 `assets/img/projects/<项目短名>/`（保持现有目录约定）。
2. 在 `_projects/` 下新建 `.md` 文件，参考现有 5 个项目文件。头部字段：
   - `title` / `description`：卡片上显示的标题和一句话简介
   - `img`：卡片封面图路径
   - `short_title`：首页与研究列表的简短标题
   - `summary`：面向读者的一句话研究概述
   - `platform` / `role` / `status`：研究平台、个人贡献、当前进展
   - `layout: research`：使用统一的项目详情排版
   - `importance`：排序权重，数字越小越靠前；首页自动展示前三个项目
   - `category: research`：保持不变
3. 正文用 Markdown 写，插图用：
   ```
   {% include figure.liquid path="assets/img/projects/xxx/fig.png" title="fig" class="img-fluid rounded z-depth-1" %}
   ```

### 添加一篇论文/出版物

编辑 `_bibliography/papers.bib`，追加一条 BibTeX 条目即可，Publications 页会自动按年份分组渲染；当前页面明确标注稿件仍在准备中且尚未投稿，投稿、接收或发表后需同步更新该说明与首页章节标题。常用可选字段：

- `selected = {true}`：让该文出现在首页 "selected publications"
- `preview = {fig.jpeg}`：配图（放在 `assets/img/publication_preview/` 下的相对路径）
- `abbr = {PRL}`：期刊缩写徽章（配色在 `_data/venues.yml` 里定义）
- `pdf = {...}` / `arxiv = {...}` / `html = {...}`：生成对应链接按钮
- 想让合作者名字变成链接：编辑 `_data/coauthors.yml`

### 更新 CV

- 网页版 CV：编辑 `_data/cv.yml`（结构化 YAML，仿照现有条目增删）。
- 网站不提供 PDF 下载；对外联系时单独附上最新 CV。

### 更换头像

把自己的照片命名为 `prof_pic.jpg` 放进 `assets/img/`，替换现有照片。建议使用清晰竖版照片；手机端会以方形裁切显示。

### 修改个人简介 / 研究兴趣

编辑 `_pages/about.md` 的正文部分。

### 添加学术链接（Google Scholar / ORCID / LinkedIn）

编辑 `_data/socials.yml`，取消注释并填入对应 ID 即可，图标会自动出现在首页底部。

## 本地预览（可选）

不装本地环境也能维护——改完 push 即可。但本地预览更快：

1. 安装 Ruby 3.3 或更新版本、Bundler 4.0.6、Node.js 20 和 ImageMagick。Windows 可使用 RubyInstaller；macOS 可使用 Homebrew 或 Ruby 版本管理器。
2. 在仓库根目录运行：
   ```bash
   bundle install
   bundle exec jekyll build
   bundle exec jekyll serve
   ```
3. 浏览器打开终端里显示的地址（通常是 http://localhost:4000）。

## 注意事项

- **不要**把 `_config.yml` 里的 `baseurl` 改成非空——本站部署在根路径。
- 新增插件需要同时改 `Gemfile` 和 `_config.yml` 的 `plugins:` 列表（两处必须一致）。
- 构建产物 `_site/` 已被 `.gitignore` 排除，不用管。
- 模板更新：在 `Gemfile` 中调整已固定的主题 gem 版本，并同步 `Gemfile.lock`；不要复制主题内部文件覆盖整套主题。

## 本站样式与布局扩展

- `assets/css/main.scss`：有意覆盖主题的 Sass 入口，继续导入 `al_folio_core` 1.0.15 的原有 partials，随后添加本站排版、蓝色主题、深色模式与响应式规则。升级主题时需要核对入口导入列表。
- `_layouts/home.liquid`：新增首页布局，继承主题 `default`，提供首页内容容器与跳至正文链接。
- `_layouts/research.liquid`：新增研究详情布局，继承主题 `page`，自动显示项目摘要和其他项目链接。
- 未覆盖主题的 `_includes/` 或 `_sass/`。导航、搜索、论文渲染继续使用固定版本的主题 gems。
- 科研封面使用现有 ImageMagick 管线生成的 WebP 响应式版本，原始图保留供详情页使用。
- 投稿、接收、正式发表需要分别更新，不要把 `Manuscript in preparation` 写成已投稿或已发表论文。
- `_layouts/cv.liquid`：有意覆盖主题 CV 布局，继续读取 `_data/cv.yml`。主题 1.0.2 的 CV 渲染器仅识别少数固定节名，原有 Research Experience、Research Grant、Leadership and Activities 的内容及教育 score 会被静默遗漏；本站布局按字段渲染这些内容，不再提供 PDF 下载，并保留章节目录。
- 模板残留 `_pages/plugins.md` 已从构建排除，避免插件介绍混入学术网站。
