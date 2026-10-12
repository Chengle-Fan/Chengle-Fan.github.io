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
- `pdf = {...}` / `arxiv = {...}` / `html = {...}`：生成对应链接按钮
- 首页和 Publications 共用 `_layouts/bib_cv.liquid`，按 CV 排成“完整作者名单，‘题目’，稿件状态”。只将 Chengle Fan 的姓名加粗（700），无下划线、无斜体；其他作者正常字重，状态统一斜体。不折叠作者、不重复单列年份，不展示作者链接或期刊徽章。
- 共一作者：在 BibTeX 姓氏后加 `*`，例如 `Fan*, Chengle and Shi*, Kaizhou`；通讯作者用 `†`。标记上标显示，与姓名加粗分开处理，并与 CV 保持一致。
- 当前自定义模板用于三篇准备中的稿件。论文接收或发表后，除更新 `note` 外，还需扩展模板显示期刊、卷页与年份，或恢复主题的 `bib` 模板。

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
- 未覆盖主题的 `_includes/` 或 `_sass/`。导航、搜索继续使用固定版本的主题 gems。
- `_layouts/bib_cv.liquid`：有意新增共享论文模板，由 `_config.yml` 的 `scholar.bibliography_template` 指定。首页和 Publications 页直接读取同一份 BibTeX；完整作者名单、题目与状态按 CV 顺序显示，姓名仅加粗，避免主题默认 `<em>` 的下划线样式。
- 保留的科研封面沿用 ImageMagick 管线生成 WebP 响应式版本；本次决定暂不展示的结果图也从部署目录移除，避免仍可通过静态文件地址访问。
- 投稿、接收、正式发表需要分别更新，不要把 `Manuscript in preparation` 写成已投稿或已发表论文。
- `_layouts/cv.liquid`：有意覆盖主题 CV 布局，继续读取 `_data/cv.yml`。主题 1.0.2 的 CV 渲染器仅识别少数固定节名，原有 Research Experience、Research Grant、Leadership and Activities 的内容及教育 score 会被静默遗漏；本站布局按字段渲染这些内容，提供原始 CV PDF 的打开入口，并保留章节目录。
- `assets/js/theme.js`：有意覆盖 `al_folio_core` 1.0.15 的同路径脚本，保留高亮、图表、搜索等主题联动。默认跟随系统，按钮按当前实际显示的模式单击切换到相反模式，明确选择的明暗偏好在换页或刷新后保留。`assets/css/main.scss` 中的图标规则按实际明暗显示太阳／月亮，不显示系统模式的半日半月图标。升级主题时需核对上游脚本并保留这一切换策略。
- 模板残留 `_pages/plugins.md` 已从构建排除，避免插件介绍混入学术网站。

## 研究图片公开范围

2026-10-12 针对 PRL、Nature Photonics、Nature Physics、Nature Communications 和 Science Advances 核对官方政策。以下区分期刊明文政策与本站的内容选择；“物理示意图”不是自动豁免类别，也没有期刊对本站逐张图片作出批准。

| 期刊 | 可核实的政策 | 对本站的判断 |
| --- | --- | --- |
| Physical Review Letters | [PRL 作者指南](https://journals.aps.org/prl/authors)说明 APS 投稿通常没有 embargo，具体稿件可另行约定；[投稿指南](https://journals.aps.org/authors/web-submission-guidelines-physical-review)支持从 arXiv 提交；[版权协议](https://journals.aps.org/authors/transfer-of-copyright-agreement)保留作者在个人网站使用文章全部或部分内容的权利。该版权协议主要规定转让后的权利，不单独决定投稿前的新颖性。 | 根据这些规则，作者网站展示原稿结构示意一般不构成投稿障碍；如稿件有专门 embargo，以具体约定为准。这是政策适用判断。 |
| Nature Photonics | [本刊预印本政策](https://www.nature.com/nphoton/editorial-policies/preprints-conference-proceedings)明确包括作者个人网站，允许审稿期间发布预印本，且不将其视为先前发表。 | 个人网站学术展示有依据；不将此解释为对每张图片的单独批准。 |
| Nature Physics | [本刊预印本政策](https://www.nature.com/nphys/editorial-policies/preprints-conference-proceedings)采用相同规则。 | 同上。 |
| Nature Communications | [本刊预印本政策](https://www.nature.com/ncomms/editorial-policies/preprints-conference-proceedings)采用相同规则。 | 同上。 |
| Science Advances | 本次访问[现行编辑政策](https://www.science.org/content/page/science-journals-editorial-policies)与[作者指南](https://www.science.org/content/page/science-advances-information-authors)受阻，未能直接核实全文；2017 年官方社论 [Preprint ecosystems](https://www.sciencemagazinedigital.org/sciencemagazine/29_september_2017?pg=7)支持非营利预印本服务器，但这不能替代现行个人网站政策。 | **尚未完全核实**。不能写成 Science Advances 已明确允许本站展示未发表原稿图；拟投此刊时需重新核对当前条款。 |

Nature 三刊要求披露预印本发布情况，并遵守[媒体宣传与禁发政策](https://www.nature.com/nphoton/editorial-policies/press-and-embargo-policies)，包括保密审稿过程。作者接受稿、出版社版本与普通预印本的共享规则应分别核对。期刊政策也不代替团队已有的图件公开安排。

下表是本站根据用户明确指定范围作出的编辑选择；保留示意、暂缓核心结果，是披露程度的选择，并非上述期刊强制要求所有未发表结果图一律删除。

| 项目 | 当前展示 | 当前不展示 |
| --- | --- | --- |
| Chiral edge | `concept.jpeg`：概念对比及示意色散，caption 说明性质 | 实验综合图、相图、器件实测结果 |
| Gauge-field duality | `symmetry_duality_concept.png`：概念示意，附理论背景文献 | 具体实现、能带、全波结果及谱图 |
| Cavity Dirac / refraction | `cavity_schematic.png`：结构概览；`refraction_candidate.png`：初步数值探索 | Dirac 论文完整的实验和能带结果 |
| THz valley | 恢复五张原始仿真图：3D、2D/3D supercell、早期设计模式及容差分析；用户明确说明这些不是最终论文图片 | 不增加实验结果或“已验证器件”的表述 |
| Photonic time crystals | 三张数值训练图，分别说明已发表问题复现、TMM计算和有限脉冲FFT响应 | 不将训练结果包装成已发表的新发现 |
| Cavity transport | 原稿 Fig. 1(g–i) 传播现象示意，单独 g 面板作为封面 | 能带、参数曲线、实验场图 |
| Cavity EP | 原稿 Fig. 1(a) 理论共振器链与腔结构示意 | EP 谱图、实验数据和修订过程材料 |

Transport / EP 保持排在研究列表末尾。两图 caption 标明来自合作稿件；EP 的 ±iγ 明确是理论模型的增益／损耗项，不能据此推断个人完成了增益实验。Transport 示意不表示三个阶段在相同频率下的实测传播。

新增图件来源与复现记录（仅从原 PDF 渲染裁取完整面板，没有重画或改变科学内容）：

- `manuscript_2026-10-10_V1.pdf`，PDF 第 5 页 Fig. 1(g–i)：300 dpi，裁取 `(x=350, y=1840, W=1790, H=375)`；封面 Fig. 1(g) 为 `(350,1840,635,375)`。g 图 Ls 下方的向上箭头属于腔高尺寸标注，应保留。
- `PRL Manuscript_20260618-1811.pdf`，PDF 第 2 页 Fig. 1(a)：300 dpi，裁取 `(x=221, y=207, W=1005, H=452)`。
- THz 五张图片从原网站备份恢复，未改变像素内容。图注区分早期设计和后续优化，并将容差结论限制为所扫描范围内的带隙重叠。

折射图是正在探索的候选条件：射线来自能带与等频线分析，不代表已验证的波束强度或功率分配。页面需保留 preliminary / candidate 的表述；同一入射场的耦合、模式一致性及波束功率仍待验证。

更换为正式发表图片时，核对最终许可、作者身份和图源，补上论文链接。已出现在公开 Git 历史中的旧图片，不会因为从当前版本移除而被历史记录自动删除。

## 字体与排版

2026-10-12：标题、姓名及首页引导句使用 Source Serif 4；正文、导航、CV 条目及论文长标题使用 Inter。两款字体以 WOFF2 自托管，包含常规／斜体、400–700 可变字重及 Latin / Latin Extended 子集。来源与 SIL Open Font License 保存在 `assets/fonts/`。字体使用 `font-display: swap`，加载前有系统字体回退；Google Fonts 链接只保留搜索组件所需的 Material Icons。

字体规则集中在 `assets/css/main.scss`，同时调整桌面／手机字号、行高和标题间距。首页引导句为 “I explore how structure shapes light, turning physical insight into photonic design.”；职业目标段落已删除。
