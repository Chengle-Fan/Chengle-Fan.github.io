# 网站维护速查（HOW TO UPDATE）

这个网站的内容全部是**数据/内容文件驱动**的——日常更新基本不需要碰任何 HTML/CSS/配置。改完后，明确选择本次修改的文件执行 `git add <文件路径>`，再提交并推送，GitHub Actions 会自动重新构建并发布（约 2–5 分钟生效）。

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

1. 经内容审查后，把适合公开的项目图片放到 `assets/img/projects/<项目短名>/`。未发表不等于禁止放图；具体取舍见下方“研究图片公开范围”。
2. 在 `_projects/` 下新建 `.md` 文件，参考现有项目文件。头部字段：
   - `title` / `description`：卡片上显示的标题和一句话简介
   - `img`：可选的卡片封面图路径；没有合适公开的图片时省略，列表自动使用文字排版
   - `short_title`：首页与研究列表的简短标题
   - `summary`：面向读者的一句话研究概述
   - `platform` / `role` / `status`：研究平台、个人贡献、当前进展
   - `layout: research`：使用统一的项目详情排版
   - `importance`：排序权重，数字越小越靠前；首页自动展示前三个项目
   - `listed: false`：可选；保留项目详情页 URL，但从首页精选、Research 列表和详情页底部导航中隐藏（当前用于 `_projects/5_funded_3d_pti.md` 资助页）
   - `category: research`：保持不变
3. 正文用 Markdown 写，插图用：
   ```
   {% include figure.liquid path="assets/img/projects/xxx/fig.png" title="fig" class="img-fluid rounded z-depth-1" %}
   ```

### 添加一篇论文/出版物

编辑 `_bibliography/papers.bib`，追加一条 BibTeX 条目即可，Publications 页会自动按年份分组渲染；每条稿件的当前状态由 `note` 标注，投稿、接收或发表后需同步更新论文列表与网页版 CV。常用可选字段：

- `selected = {true}`：让该文出现在首页 "selected publications"
- Publications 和首页 Manuscripts 均保持纯文字；不要添加 `preview`。`_config.yml` 中 `enable_publication_thumbnails: false`。
- `abbr = {PRL}`：期刊缩写徽章（配色在 `_data/venues.yml` 里定义）
- `pdf = {...}` / `arxiv = {...}` / `html = {...}`：生成对应链接按钮
- 想让合作者名字变成链接：编辑 `_data/coauthors.yml`
- 共一作者：在 BibTeX 姓氏后加 `*`，例如 `Fan*, Chengle and Shi*, Kaizhou`。主题会显示上标，Publications 页说明 `*` 表示同等贡献；在 `note` 中写明 Chengle 的共一作者排序，并与 CV 保持一致。

### 更新 CV

- 网页版 CV：编辑 `_data/cv.yml`（结构化 YAML，仿照现有条目增删）。
- PDF 版：替换 `assets/pdf/CV_Chengle_Fan.pdf`。`_pages/cv.md` 的 `cv_pdf` 指向该文件，CV 页顶部提供 `Open CV (PDF)` 入口。请同步更新网页数据与 PDF。
- 旧文件 `assets/pdf/CV_general.pdf` 已被构建排除，避免同时提供旧 CV。

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
- 保留的科研封面沿用 ImageMagick 管线生成 WebP 响应式版本；本次决定暂不展示的结果图也从部署目录移除，避免仍可通过静态文件地址访问。
- 投稿、接收、正式发表需要分别更新，不要把 `Manuscript in preparation` 写成已投稿或已发表论文。
- `_layouts/cv.liquid`：有意覆盖主题 CV 布局，继续读取 `_data/cv.yml`。主题 1.0.2 的 CV 渲染器仅识别少数固定节名，原有 Research Experience、Research Grant、Leadership and Activities 的内容及教育 score 会被静默遗漏；本站布局按字段渲染这些内容，提供原始 CV PDF 的打开入口，并保留章节目录。
- `assets/js/theme.js`：有意覆盖 `al_folio_core` 1.0.15 的同路径脚本，保留高亮、图表、搜索等主题联动。默认跟随系统，按钮按当前实际显示的模式单击切换到相反模式，明确选择的明暗偏好在换页或刷新后保留。`assets/css/main.scss` 中的图标规则按实际明暗显示太阳／月亮，不显示系统模式的半日半月图标。升级主题时需核对上游脚本并保留这一切换策略。
- 模板残留 `_pages/plugins.md` 已从构建排除，避免插件介绍混入学术网站。

## 研究图片公开范围

2026-10-12 核对的官方政策支持有条件的提前学术交流，并非“论文未发表就不能放图片”：

- [Nature Portfolio 自存档政策](https://www.nature.com/nature/editorial-policies/self-archiving-and-license-to-publish)允许在作者网站及预印本服务器发布预印本，且不将其视为此前正式发表；[Nature Photonics 编辑政策](https://www.nature.com/nphoton/editorial-policies)采用该系列的共同政策。
- [APS 作者版权 FAQ](https://journals.aps.org/copyrightFAQ.html)说明作者在个人网站和免费预印本平台的共享权利；使用时区分作者版本与出版社版本，并遵守适用的引用要求。
- [Optica 的预印本政策](https://opg.optica.org/content/author/portal/item/review-copyright-permissions/)允许投稿前及审稿期间在预印本服务器发布稿件，接收/发表后的版本及署名要求另有规定。

下表是针对本站图片内容的编辑选择，并非期刊逐张批准或禁止的清单。

| 项目 | 本次保留 | 本次不展示 |
| --- | --- | --- |
| Chiral edge | `concept.jpeg`：概念对比及示意色散，caption 明确其性质 | 实验综合图、相图、器件实测结果 |
| Gauge-field duality | `symmetry_duality_concept.png`：作者绘制的概念示意，附理论背景文献 | 具体实现、能带、全波结果及谱图 |
| Cavity Dirac / refraction | `cavity_schematic.png`：结构概览；`refraction_candidate.png`：初步数值探索 | Dirac 论文完整的实验和能带结果 |
| THz valley | 文字说明建模与优化贡献 | 现有图片包含能带、带隙、参数与模式结果，暂不作为概念封面 |
| Photonic time crystals | 三张数值训练图：分别说明已发表问题复现、TMM计算和有限脉冲FFT响应 | 不将训练结果包装成已发表的新发现 |
| Cavity transport / EP | 文字说明实验贡献，排在后面 | 不从未发表稿件新增结果图 |

折射图是正在探索的候选条件：射线来自能带与等频线分析，不代表已验证的波束强度或功率分配。页面需保留 preliminary / candidate 的表述；同一入射场的耦合、模式一致性及波束功率仍待验证。

更换为正式发表图片时，核对最终许可、作者身份和图源，补上论文链接。已经出现在公开 Git 历史中的旧图片，不会因为从当前版本移除而被历史记录自动删除。
