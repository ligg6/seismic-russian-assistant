# 项目使用说明（完整版）

> 写给未来的自己：忘了怎么用时，从这一页开始。
> 最后更新：2026-07-26（运行 7 之后）｜术语库 223 条｜语料 101 个文件

---

## 〇、这个项目是什么

从 **101 个俄语语料文件**（40 篇期刊论文 + Yilmaz 俄译教材 3 卷 + МГУ 教材 29 章 + 17 部博士论文/自动摘要）中提炼出的一整套**俄语海洋地震论文写作标准**，并做成了四种可用形态：

| 形态 | 在哪里 | 什么时候用 |
|------|--------|-----------|
| ① 公开网页 | **https://ligg6.github.io/seismic-russian-assistant/** | 日常写作首选，手机电脑都能开，无需登录 |
| ② Claude Code skill | `~/.claude/skills/marine-seismic-russian/` | 在任何目录跟 Claude 对话写/改俄语时自动生效 |
| ③ 项目文件 | 本目录 `outputs/`（23 个 .md） | 需要完整细节、证据出处时查原文件 |
| ④ 命令行工具 | 本目录 `scripts/` | 初稿体检、语料更新 |

---

## 一、日常写作：六个最常用场景

### 场景 1：「这个概念俄语怎么说？」
打开网页 → **术语查询** 页签 → 搜索框输入**中文、俄语或英文**均可（如"多次波"/ "миграция" / "deconvolution"）。
每条术语给：变格形式、推荐学术用法、常见搭配、自创例句（带中文）、**证据等级**、来源论文编号。点条目展开全部。
查不到 → 换短关键词；再查不到 → 用场景 5 的翻译助手。

### 场景 2：「我要写某一章/某一节」
网页 → **写作向导** 页签 → 点你要写的部分（期刊摘要/引言/方法/结果/结论、博士绪论/综述/方法章）→ 该章所需句型、段落模板、功能表达一页备齐，逐条可复制。
**写博士论文**先读 `outputs/dissertation_blueprint.md`：全文骨架 + 绪论 14 要素的标准顺序（三部 МГУ 论文实测一致）+ 每要素写法出处。
想看"库怎么组装成完整段落"→ `outputs/model_annotated_sections.md`（3 个逐句注释范文）。

### 场景 3：「中文想法 → 论文级俄语」
网页 → **翻译助手** 页签 → 粘贴中文段落 → 点"生成翻译提示词" → 系统自动匹配库内术语并生成一段带术语约束和写作规则的完整提示词 → 复制 → 粘给 Claude（或任何 AI）→ 得到合规俄语 + 中文回译。
在 Claude Code 里更简单：直接说"帮我把这段中文写成俄语论文表达"，skill 会自动加载全部规则。

### 场景 4：「初稿写完了，帮我检查」
两种方式（同一套 34 条规则）：
- 网页 → **初稿体检** 页签 → 粘贴俄语文本 → 即时分级报告（❌必改 / ⚠️建议改 / ℹ️优化）；
- 命令行：`python3 scripts/09_style_check.py 你的初稿.txt`

检查完再对照 `outputs/final_native_style_checklist.md` 逐项勾选，最后**务必请导师/母语者审校**。

### 场景 5：「背单词」
网页 → 术语查询页签右上角 → **⬇ 导出 Anki 卡组 (TSV)** → Anki 里 文件→导入，字段对应：正面=俄语，背面=中英+例句。

### 场景 6：「在 Claude Code 里写论文」
在**任何目录**打开 claude，只要话题涉及"俄语 + 地球物理"（写、译、润色、纠错、问术语），skill 自动触发。也可明确说"用 marine-seismic-russian 的规则"。skill 内含 20 条内联硬规则 + 17 个参考文件。

---

## 二、23 个输出文件地图（outputs/）

**一级核心**（写作天天用）：
- `seismic_terminology_bank.md` — 223 条术语（§Z 是中文反查索引）
- `collocation_and_government_bank.md` — 格支配与搭配（词和词怎么连）
- `marine_seismic_processing_workflow.md` — 处理流程写法（§18 是方法章八步微结构）
- `processing_qc_expression_bank.md` — 质控表达（§12 前后对比与定量）
- `processing_to_interpretation_bridge.md` — 处理→解释过渡（强/中/弱三级推断纪律）
- `MY_SEISMIC_RUSSIAN_WRITING_RULES.md` — 总规则（可整个贴给 AI 当前置提示词）

**二级**（按需取用）：句型库（§17-bis 学位论文框架句）、段落模板（§38 答辩论点规律、§39 处理步骤段）、图件描述模板、表达库（§25–29 方法论证/综述/局限）、中式俄语纠错、禁用直译、转换库、审校流程、提示词模板（§14–16 学位论文专用）

**三级**：研究分支、术语一致性、评分细则、检查清单、final_report（含历轮增量汇总）
**运行 7 新增**：`dissertation_blueprint.md`（博士蓝图）、`model_annotated_sections.md`（注释范文）

## 三、看懂证据标注（很重要）

每条术语/表达带证据等级——**决定你用它的放心程度**：
- **high**：≥5 篇期刊论文 → 放心用
- **medium**：≥3 篇 → 放心用
- **low**：证据有限 → 可用但留意条目内注记
- **generated**：自创改写 → **必须**经母语者确认后才能进投稿正文
- `(+учебник: NNN)`：教材佐证（不计篇数；Yilmaz 是译著防翻译腔）
- `(+дисс: NNN)`：学位论文佐证（目标文体，可参考使用）
- `textbook_only / dissertation_only`：仅教材/仅学位论文支持，用前确认

三条铁律：不照抄语料原句（只用改写模板）；数值一律占位符不编造；弱证据现象不写成强结论。

---

## 四、往语料库加新论文（增量更新）

```bash
cd /home/usvps/lgg/marine-seismic-russian-writing

# 1. 把新 PDF（或 .doc/.docx）放进 papers_pdf/（可建子文件夹）
# 2. 依次运行（01 只处理新文件，自动续编号）：
python3 scripts/00_backup.py     # 先备份（必须！）
python3 scripts/01_extract_pdf.py
python3 scripts/02_clean_and_metadata.py
python3 scripts/03_corpus_branches_terms.py
python3 scripts/04_collocations.py
python3 scripts/05_derive_term_candidates.py
python3 scripts/06_ngram_discovery.py       # 看有没有新术语盲区
python3 scripts/07_verify_consistency.py    # 必须 0 problems
# 3. 查 analysis/ngram_discovery_report.md 的未覆盖高频词——
#    有价值的新术语让 Claude 帮你按规范写进术语库
# 4. 在 analysis/run_log.md 手动追加一段运行记录
```

依赖若报缺：`pip3 install --user --break-system-packages pymupdf olefile python-docx`
（学位论文放进去会被自动识别为 DIS 层；教材类需在 02 脚本的 textbook_meta 里登记。）

## 五、改完内容后同步所有平台（五步清单）

```bash
cd /home/usvps/lgg/marine-seismic-russian-writing
python3 scripts/08_build_webapp.py                                    # ① 重建网页
cd webapp && git add -A && git commit -m "update" && git push && cd .. # ② 公开网站（约 1 分钟生效）
bash ~/.claude/skills/marine-seismic-russian/scripts/sync_from_project.sh  # ③ skill
# ④ 若新增/删除了 outputs 文件：编辑 skill 同步脚本里的 FILES 清单 + SKILL.md 路由表
# ⑤ 若要更新 claude.ai Artifact：在 Claude Code 里说"重新发布 Artifact"即可（URL 不变）
```

---

## 六、排错 FAQ

| 问题 | 处理 |
|------|------|
| 公开网页打不开 | 双击本地 `webapp/index.html`（内容完全一样，可离线）|
| 网页数据是旧的 | 跑第五节①②；GitHub Pages 生效要等约 1 分钟 |
| skill 没触发 | 明说"用 marine-seismic-russian skill"；或查 `~/.claude/skills/marine-seismic-russian/SKILL.md` 是否在 |
| git push 要登录 | `gh auth login`（账号 ligg6）|
| 管线脚本报错 | 看是哪一步：01 提取失败查 `metadata/extraction_report.csv`；07 报 problems 按提示修术语库 |
| 想回滚 | `archive/` 里有每轮运行前的完整快照（outputs+metadata+analysis），按时间戳整个拷回来即可 |
| 某文件被改坏了 | 同上，从最近的 archive/ 快照恢复单个文件 |
| 忘了整体架构 | 读 `README.md`（简版）→ 本文件（全版）→ `analysis/run_log.md`（7 轮运行全史）|

## 七、几个容易忘的要点

1. **RTM**：101 个语料文件中零出现——俄语文献不惯用此缩写，写作用全称 миграция в обратном времени（首现附 RTM）。
2. **两个假朋友**：свёрточная нейронная сеть（卷积神经网络）≠ сверточная модель трассы（褶积模型）；4C（四分量采集）≠ четырехкомпонентная модель（四项地表一致分解）。
3. **答辩论点**写法先读 `paragraph_templates` §38（两类型/六规律），别自己发挥。
4. 公开网站**任何人可见**；想转私有：GitHub 仓库 Settings → 改 Private（网站会下线，改用本地 index.html）。
5. 人工复核队列 `metadata/human_review_queue.csv`（46 项）——找到母语者时按此清单逐项确认。
6. 语料仍缺的方向：RTM 专题、孔隙压力预测方法学——遇到相关论文优先补充（回第四节流程）。
