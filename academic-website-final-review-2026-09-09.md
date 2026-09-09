# 个人学术网站：套瓷前修改意见

核查日期：2026-09-09  
网站：https://chengle-fan.github.io/  
用途：交给执行 agent，完成发送套瓷邮件前的内容修改与最终验收。

## 1. 总体判断与核查边界

网站已有清楚的教育背景、研究方向、个人贡献和实验结果，适合作为套瓷邮件的补充材料。当前最值得修改的是研究信息的展示顺序，以及部分页面过于接近内部工作记录的措辞。优先完成下述 P0、P1 项，无需大规模重做网站。

本次实际读取了首页、Research、Publications、CV、Updates 和 6 个项目详情，共 11 个公开页面；检查的 115 个站内页面及资源 URL 均返回 HTTP 200。页面中公开的联系邮箱一致。首页、CV 和 NTU 项目页关于预计毕业时间、研究组经历及访学日期的表述未发现明显冲突。这是页面之间的一致性检查，不代表独立核实了成绩、经历或科研结论。

外部论文 DOI 能发生跳转，但部分出版社页面要求人机验证或返回 403，不能据此判定 DOI 失效，也不能把这些页面记为已完整通过访问检查。

浏览器可视检查多次超时。本次完成了公开 HTML、链接、资源和部分科研图片检查，**尚未完成桌面端与手机端页面排版、导航交互及深浅色模式的可视验收**。执行 agent 应补做第 7 节的检查。

以下是修改建议与替换文案，线上网站尚未修改。

## 2. P0：发送前应修正

### P0-1 重写 Photonic Time Crystals 页的内部验收式文字

页面：https://chengle-fan.github.io/projects/0_photonic_time_crystals/

问题不在于使用专业术语，而在于正文把版本、测试计数、运行环境和代码审计当作主要成果展示。`Current validation snapshot`、`8/8 package checks`、`12/12 transmission-line checks`、`repository-wide code analysis` 等内容适合代码说明或验证记录。读者需要优先看到研究问题、本人完成的工作和物理结果。

#### A. 将两个原小节合并为一个小节

删除 `Current validation snapshot` 和 `Scope and next steps` 的原正文，合并替换为下面的英文。数值研究的性质、研究来源和后续方向仍然保留。

```markdown
## Results and ongoing work

Using the parameters of Lustig et al. (2018), I reproduced the contrasting dynamics of pulses in a pass band and a momentum gap. The pass-band pulse remains bounded and splits at temporal interfaces, while the momentum-gap pulse is amplified during modulation. I also compared spectra reconstructed from FDTD probe signals with the Floquet bands obtained from temporal transfer matrices. The reconstructed peaks follow the stable bands, and the pulse amplification is consistent with the transfer-matrix calculation.

This project is an ongoing numerical study. I am checking how the spatial and temporal resolution affect these results, and plan to investigate the topology of the Floquet bands and refine the transmission-line model using measured component parameters.
```

这份替换稿依据网站现有描述压缩而成，没有重新运行 MATLAB。执行时应与实际项目进度保持一致；尤其不要把“计划使用实测参数”改写成“已完成实验标定”。

#### B. 同时清理该页前半部分

仅替换末尾两段还不够，前文有相同的内部记录语气：

| 位置 | 修改要求 |
|---|---|
| `Context` 段 | 删除 `developing and auditing`、`making results traceable`、`rather than relying on a single solver` 等验收式表达。使用下方替换稿。 |
| `What I am building` | 标题改为 `Numerical approach`。 |
| `The current V3.1 MATLAB package connects four complementary views...` | 改为 `I use three numerical methods to connect Floquet band structure with pulse dynamics: plane-wave expansion, temporal transfer matrices, and FDTD simulations.` 后接现有方法说明，避免重复。 |
| `per-(k) Gaussian-wavepacket simulations` | 改为 `Gaussian wave-packet simulations with different central wavevectors`，避免公式标记问题。 |
| `Shared numerical kernels...stale copies of the solvers` | 从学术介绍正文移除；若保留，放入代码仓库文档。 |
| `My role: Numerical modeling & scientific validation` | 简化为 `Numerical modeling`。 |
| 图注中的 `Generated from the current V3.1 code in September 2026` | 从图注移除；版本与生成日期可留在代码或图片元数据中。 |

`Context` 后的介绍可替换为：

```text
I am studying pulse propagation in photonic time crystals through numerical modeling. This work connects Floquet band calculations with time-domain simulations of pulse splitting and amplification.
```

保留后面解释时间周期调制、动量守恒和动量带隙的物理背景段。

#### C. 同步修改首页和 Research 列表卡片

两处目前使用 `Developing a Base-MATLAB toolkit...`，与项目页需要同时调整。推荐统一为：

```text
Modeling Floquet bands and pulse dynamics in photonic time crystals using plane-wave expansion, temporal transfer matrices, and FDTD simulations.
```

保留正在进行的状态。`Base-MATLAB`、软件版本和测试信息不必出现在项目摘要中。

### P0-2 修正该页的公式标记

公开 HTML 中出现了 `(0.00565\,\Omega)`、`(0.03466\,\Omega)`、`(\ln(\mathrm{gain})=29.793)`。这些只有普通圆括号，缺少 MathJax 公式定界符；当前配置识别 `$...$` 或 `\(...\)`，不会把上述文本正常识别为公式。

执行要求：

1. 按 P0-1 删除的文字无需继续修补其公式。
2. 对保留的公式检查构建后的 HTML，确保定界符没有被 Markdown 转义处理吃掉。
3. 若精确数字移到技术说明中，可使用 `$0.00565\,\Omega$`、`$\ln(\mathrm{gain})=29.793$` 等正确格式。
4. 在实际浏览器里确认没有直接显示 `\Omega`、`\ln`、`\mathrm` 等源码。

## 3. P1：建议发送前完成

### P1-1 增加可下载的 CV

页面：https://chengle-fan.github.io/cv/

当前 CV 页面是网页简历，没有发现 PDF 下载链接，也没有 PDF 嵌入入口。建议：

- 在 CV 页顶部增加明确的 `Download CV (PDF)` 按钮。
- 首页介绍区域增加一个次要的 `CV (PDF)` 链接，与研究入口并列。
- 优先使用本人确认的最新 PDF；文件名建议为 `Chengle_Fan_CV.pdf`。
- 比对 PDF 与网页中的毕业时间、访学日期、GPA、排名、TOEFL 和论文状态。
- 确保链接无需登录，指向真正的 PDF，下载后可正常打开。

如果执行环境没有最新 PDF，应先报告这一项待补充，不要连接旧版本或制作空占位文件。

### P1-2 按研究成熟度调整展示顺序

页面：首页与 https://chengle-fan.github.io/projects/

目前首页和 Research 列表都把仍标为 `Ongoing research training` 的时间晶体项目放在首位。已有实验结果、约 20 dB 方向传输差异和准备中稿件的手性边缘态项目更适合作为默认首项。

默认建议排序：

1. Pseudospin-locked chiral edge states
2. Terahertz chiral valley edge states
3. Gauge-field-induced duality
4. Photonic time crystals
5. Cavity-tunable topological dipole arrays

首页保留 3 个精选项目即可。若本轮主要联系时间调制光子学导师，可将时间晶体项目放入首页前 3 项；不必为所有导师使用同一种侧重点。

排序应通过项目元数据或模板完成，尽量保留已有项目 URL，避免已有邮件或收藏中的链接失效。

### P1-3 修正两类不自然的角色与图注表述

**手性边缘态项目：**

https://chengle-fan.github.io/projects/1_pseudospin_locked_chiral_edge/

`Full-wave modeling & sample design and experiment` 并列结构不自然，也没有准确区分“主导建模设计”和“参与实验”。在卡片和项目页统一为：

```text
Full-wave modeling, sample design, and experimental characterization
```

正文已有 `I led...` 和 `I also participated...`，应保留这一贡献层级，避免改成全部独立完成。

**腔体偶极阵列项目：**

https://chengle-fan.github.io/projects/4_cavity_dipole_arrays/

图注的 `for the setting labeled...in the research presentation` 暴露了从内部汇报材料转写的过程，可直接写物理参数。建议分别改为：

```text
Experimental dispersion reconstructed from near-field measurements at Lz = 0.3a.
```

```text
Simulated field distribution at Lz = 0.333a.
```

两幅图参数不同，应在图片标签或共同图注中明确。这一点属于必要的科学说明，不能为了简洁而删去，也不要把它们写成同一参数下的实验与仿真对照。

## 4. P2：可顺手优化，不必因此推迟发信

### P2-1 合并内容过少的资助项目页

页面：https://chengle-fan.github.io/projects/5_funded_3d_pti/

当前页面主要重复“获得资助、担任负责人、仍在准备”，没有具体研究问题或结果，而同一项资助已在首页动态与 CV 出现。

建议从主要研究卡片中移除，将资助记录保留在 CV 与 Updates。若已有明确研究问题，可补充 2–3 句具体内容后保留项目页；不要为了补齐页面而编造进展。已有 URL 可以保留为简短说明页。

### P2-2 精简 Publications 页的重复说明

页面：https://chengle-fan.github.io/publications/

当前网站已明确说明唯一列出的稿件处于准备中，未发现把它冒充已发表论文的情况。无需为这一点添加更多解释。

可把正文开头重复的状态说明缩短，保留条目中醒目的 `Manuscript in preparation`。页面标题可选用 `Publications & Manuscripts`，也可暂时保留 `Publications`。不要添加尚不存在的期刊、DOI、投稿或录用信息。

### P2-3 让首页更快说明申请方向

首页目前在底部写到对 graduate research opportunities 感兴趣，身份和预计毕业时间则分散在不同位置。建议将申请意向移到首页介绍附近，便于导师快速判断。

如果本人确认申请目标是 2027 年秋季博士，可使用：

```text
I am seeking PhD opportunities in photonics for Fall 2027.
```

网站只能确定预计 2027 年 6 月毕业，不能据此自动确认学位目标或入学时间。未确认时使用现有的宽泛申请意向，不写具体年份和学位。

### P2-4 优化首页论文预览图

首页的 `/assets/img/publication_preview/concept.jpeg` 约 1.25 MB，作为小幅预览图仍使用原始 JPEG，并设置了 `loading="eager"`。

建议生成适合显示尺寸的 WebP/AVIF 或压缩 JPEG 缩略图，配置响应式图片，并对首屏之外的预览采用懒加载。保留点击查看高清科研图的能力。验收关注加载和缩略图可读性，不要简单降低全部科研图片分辨率。

### P2-5 保留简明、必要的图注

时间晶体的场演化图左右面板使用不同色标，建议图注明确说明，避免读者直接按颜色比较增益。可使用：

```text
FDTD simulations of pulse propagation in a photonic time crystal using the parameters of Lustig et al. (2018). The incident pulses correspond to a pass band (1.4 μm) and a momentum gap (0.93 μm). White brackets mark the modulation interval, 220–340 fs. Color shows ln(|D|/D0); the two panels use different color scales.
```

频谱重构图仍应交代横轴是源的中心波矢、探针数和分析时间窗；这些信息帮助解释图本身。若要展示理论与重构结果的一致性，可从原始数据重新生成带 TMM 参考曲线的叠加图。不要仅靠插值美化现有热图，也不要凭图片手绘理论曲线。

## 5. 全站英文修改原则

- 使用“研究问题 → 我的工作 → 结果”的顺序。
- 用具体贡献动词，例如 modeled、designed、measured、compared；减少 auditing、traceability、validation snapshot 等内部验收用语。
- 区分本人主导、本人参与、合作团队完成以及未来计划。
- 保留数值结果与实验结果的区别、不同图之间的参数差异、未发表稿件状态和必要的文献出处。
- 软件版本、测试通过数量和代码检查记录可进入 README 或技术说明。
- 避免每个项目都以 `This project trained me to...` 或抽象的工作感想收尾；优先用一个具体发现或下一步研究问题结束。
- 保留能帮助读者评价结果的数字，例如实验方向传输差异和工作频率。删除数字应有信息层面的理由，而不是把所有定量结果都视为“不自然”。

## 6. 执行时需要核实的事实

这些事项不能仅凭网页推断，也不必阻止其他文案和格式修改：

- 最新 CV PDF 的来源及其与网页版本的一致性。
- 申请目标是否确实为 Fall 2027 PhD。
- 时间晶体项目是否已有可公开的代码仓库；有则可加一个直接链接，无则不要创建空链接。
- 下一步工作是否仍包括 Floquet 拓扑分析和使用实测参数完善传输线模型。
- 如补充资助项目研究内容，应依据本人已有材料。

不需要额外索取已经在网页中清楚写明、且本次没有发现冲突的信息。

## 7. 最终验收标准

执行 agent 完成修改后，应逐项确认：

- [ ] 时间晶体页两个原小节已合并改写，版本号、测试计数和代码审计不再占据科研正文。
- [ ] 首页、Research 列表和项目详情中的同一项目摘要与角色称谓一致。
- [ ] 公式实际渲染正常，没有裸露的 LaTeX 命令或 `per-(k)`。
- [ ] 成熟项目处于醒目位置，原有项目链接继续有效。
- [ ] CV PDF 有明确入口，内容经核对且能直接下载打开；若缺少源文件，明确记录待补项。
- [ ] 稿件仍标记为准备中，没有擅自升级成果状态或个人贡献。
- [ ] 电脑宽度约 1440 px、手机宽度约 390 px 下，首页、Research、CV 和时间晶体详情无横向溢出、标题遮挡、文字重叠或邮箱越界。
- [ ] 手机菜单能展开、关闭并完成导航；深浅色模式下文字与科研图注可读。
- [ ] 关键图片可打开，图中文字足够清晰，图片参数与正文和图注一致。
- [ ] 所有站内导航、CV 下载和联系链接正常；邮箱链接目标拼写正确，不需要发送测试邮件。
- [ ] 最终报告列出实际修改页面、完成的检查和仍需本人补充的事项，不把未完成的浏览器检查写成已通过。

## 8. 推荐执行顺序

先处理 P0 的时间晶体文案与公式，再处理 P1 的 CV 入口、项目顺序和明显措辞问题，最后做浏览器验收。P2 作为顺手优化，不必扩大成全站重新设计。
