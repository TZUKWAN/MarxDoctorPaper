---
name: marx-doctor-paper
description: "MarxDoctorPaper 马克思主义理论博士毕业论文生产技能。用于马克思主义理论及相关人文社科学科博士学位论文的选题、文献底座、开题结构、分章写作、论述深化、全稿审校与 Word 交付。默认规格：正文 17—18 万字、绪论+4—6 章+结语、页下注圈码每页重编号、GB/T 7714。核心要求：先读工作空间真实资料并回到原文精读；脚注一注一证、闭环对账；审计先行两阶段修改；苏格拉底式中介问题深化，不用空话凑字数；政治合规与 AI 痕迹控制贯穿全程。首次使用脚本时 AI 必须自动完成环境配置，无需用户手动操作。"
---

# MarxDoctorPaper

MarxDoctorPaper 是马克思主义理论一级学科（含思想政治教育、党史党建、马克思主义中国化等方向）博士学位论文的生产技能，不是论文模板或提示词集合。它以 EMARX v7.5 为内核，针对博士论文的篇幅、章节体系、学校模板和盲审场景加固。

目标：产出问题意识明确、结构递进、概念稳定、论证有史料和机制支撑、语言平实有学术质感、格式经得起学校审查的博士论文全稿，默认交付 Markdown 工作稿 + Word + PDF。

## 一、总原则

1. **先读本次工作空间，再使用既有语料规律**。旧报告和工具输出只作索引，不替代当次原文精读。
2. **结构由研究对象内部关系生长**：绪论+4—6 章+结语，各章功能边界清楚，一级标题递进，能通过互换测试。
3. **以小节为准入单元、以段落为推进单元**：论证卡→subagent 审查→逐段生成→段落审查→过门进入下一节。
4. **脚注工程化**：一注一证；脚注定义数==正文引用数==编号连续；同一文献首次完整著录、后续短引；文集类原始文献书级著录。详见 `references/footnote-engineering-protocol.md`。
5. **审计先行**：修改已有成稿必须先只读审计出量化清单，再逐项修复，最后回归审计。大规模改写前建基线备份，处理过度立即回退并声明作废版本。详见 `references/audit-then-fix-protocol.md`。
6. **深化靠追问不靠凑字**：字数不足时用苏格拉底式中介问题补实质分析，禁止空话凑数。详见 `references/socratic-deepening-protocol.md`。
7. **一切数字以最终文件实测为准**：字数、脚注数、参考文献数、页数都从最终交付文件实测，不引用中间版本数字。
8. **政治合规是第一位**：涉及党的创新理论、党史、民族、宗教、港澳台、国际关系等议题，必须回到权威原文。详见 `references/political-compliance-protocol.md`。
9. **主动控制 AI 痕迹与查重**：去 AI 味修改遵守保真编辑规则，禁止按词频表机械替换。详见 `references/ai-trace-mitigation-protocol.md`。
10. **学位论文当文献库不当靠山**：[D] 引用逐条溯源改引到原始文献，禁止同题替换，正文不得出现学位论文身份括注。详见 `references/dissertation-source-mining-protocol.md`。

## 二、博士论文默认规格

| 项 | 默认 | 说明 |
|---|---|---|
| 正文字数 | 17—18 万字 | 以学校规范为准；口径（是否含脚注）交付时写明 |
| 结构 | 绪论+4—6 章+结语 | 见 `references/chapter-system-protocol.md` |
| 摘要 | 中文摘要+关键词，英文 Abstract+Keywords | |
| 目录 | 条目可见、页码正确、缓存写回 | 不依赖 F9 |
| 引注 | 页下注，圈码 ①②③，每页重编号 | 脚注文字宋体 9pt 或按学校规范 |
| 著录 | GB/T 7714 | 文集/全集书级著录 |
| 参考文献 | 编号连续，与脚注可追溯 | 按学校要求决定是否保留文末书目 |
| 模板 | 学校模板，占位字段不虚构 | 见 `references/school-template-protocol.md` |

## 三、首次使用：零配置

脚本（CNKI 检索、Word 交付、审计等）需要 Python 依赖和 Playwright 浏览器。AI 直接调用目标脚本即可：脚本开头会自动创建技能目录下的隔离虚拟环境 `.venv/`、安装依赖、下载浏览器，再切换进虚拟环境执行。首次配置可能需要几分钟，AI 应告知用户正在自动配置。用户不需要手动执行 `pip install` 或 `playwright install`。

注意：pandoc 是 Word 交付的外部程序，不是 Python 包，无法自动安装。未检测到 pandoc 时，提示用户从 https://pandoc.org/installing.html 安装。

## 四、优先读取文件

### 必读（博士论文任务）

- `references/dissertation-workflow.md`：博士论文主流程（学校规范确认→选题→文献底座→开题结构→分章写作→深化→审校→交付）。
- `references/chapter-system-protocol.md`：章节系统——绪论构成、章下小引言禁令、各章功能边界、段落硬规则、结语、字数分配。
- `references/footnote-engineering-protocol.md`：脚注一注一证、闭环对账、短引、语义归并、书级著录。
- `references/citation-fact-protocol-v7.md`：引用贴句、事实分级、来源优先级、GB/T 7714。
- `references/audit-then-fix-protocol.md`：审计先行两阶段与版本回退。
- `references/socratic-deepening-protocol.md`：中介问题追问与字数扩展纪律。
- `references/dissertation-source-mining-protocol.md`：学位论文文献库方法。
- `references/absolute-claims-gate.md`：绝对化表述与统计结论证据门槛。
- `references/meta-discourse-audit.md`：元话语与符号量化审计。
- `references/school-template-protocol.md`：模板、目录、批注、交付检查。
- `references/political-compliance-protocol.md`：政治合规。
- `references/ai-trace-mitigation-protocol.md`：AI 痕迹控制与保真编辑规则。
- `references/style-protocol.md`、`references/wording-expression-protocol.md`：语言与表达纪律。
- `references/classic-text-reading-protocol.md`、`references/marxist-classics-index.md`：经典文本精读。
- `references/concept-ledger-protocol.md`：概念台账。

### 按需读取

- `references/ten-writing-methods.md`、`references/writing-method-selector.md`：十种论证方法与选择。
- `references/logical-chain-protocol.md`：逻辑推理链。
- `references/scholarliness-protocol.md`：学理性。
- `references/cnki-integration-protocol.md`：CNKI 集成。
- `references/peer-review-response-protocol.md`：盲审/外审意见回应。

## 五、生产流程概要

完整流程见 `references/dissertation-workflow.md`。概要：

1. **学校规范确认**：字数口径、引注体例、模板文件、查重红线；
2. **选题与问题域**：五个理论问题 + 理论增量判断 + 文献缺口诊断（不足时自动触发 CNKI）；
3. **文献底座**：原始文献 / 经典文本 / 研究文献 / 学位论文文献库四层；
4. **开题结构**：章节功能边界 + 标题链递进 + 大纲 subagent 群审查；
5. **分章写作**：论证卡→审查→逐段生成→段落审查；
6. **深化扩展**：中介问题追问，字数实测管理；
7. **全稿审校**：两阶段审计 + 六项专项审计；
8. **交付**：模板套用→build_docx→finalize（批注清理+目录缓存）→DOCX 审计→PDF 抽查。

## 六、语言规则

目标语体：平实、清楚、稳健、有分寸、有判断、有学术质感。

在 EMARX 语言纪律基础上，博士论文额外强调：

- 段首第一句禁止指代词起句（"这一""这种""其""该""由此"），必须明确主语；
- 正文段落原则上不用双破折号"——"；
- 不用引号包装作者临时拟制的概念；
- 不设问导语、不导游、不章节自指；
- 一句话一个脚注，不堆叠。

## 七、脚本工具

```bash
# 文献缺口诊断与 CNKI 自动触发
python scripts/emarx_literature_gap.py --workspace workspace --topic "论文题目" --min-local-sources 10 --min-relevant-sources 3

# CNKI 手动命令
python scripts/cnki_cli.py search "关键词" --pages 3 --output workspace/cnki_results.json
python scripts/cnki_cli.py read-batch --results workspace/cnki_results.json --output-dir workspace/summaries --limit 10
python scripts/cnki_cli.py import --results workspace/cnki_results.json --summaries-dir workspace/summaries --output-dir workspace --top-k 10

# CNKI 文献功能绑定
python scripts/emarx_bind_cnki_sources.py --sources workspace/sources.json --outline workspace/outline.md --output workspace/source-claim-map.json

# 资料与锚定
python scripts/scan_workspace_sources.py --root workspace --output sources.json
python scripts/select_anchor_papers.py --topic "论文题目" --workspace-root workspace --output anchor-papers.md --top-k 5
python scripts/build_research_brief.py --topic "论文题目" --sources sources.json --output research-brief.md

# 审计
python scripts/footnote_audit.py --paper paper.md --output footnote-audit.json
python scripts/citation_audit.py --paper paper.md --output citation-audit.json
python scripts/citation_position_audit.py --paper paper.md --output citation-position-audit.json
python scripts/ai_trace_audit.py --paper paper.md --output ai-trace-audit.json
python scripts/bad_draft_audit.py --paper paper.md --output bad-draft-audit.json
python scripts/scholarliness_audit.py --paper paper.md --output scholarliness-audit.json

# Word 交付
python scripts/emarx_build_docx.py paper.md paper.docx
python scripts/emarx_finalize_docx.py paper.docx --update-toc
python scripts/audit_docx.py --docx paper.docx --output docx-audit.json
```

脚本用于索引、审计和交付，不等于最终事实判断。语义支撑必须由主模型回到来源复核。

## 八、逻辑审查 subagent 群

三个节点运行，每个 agent 只从自己定位出发挑问题，主模型综合裁决，subagent 不直接改正文：

- **大纲完成后**：`agents/outline-reviewers/`（结构递进、问题意识、概念一致性、材料可行性、期刊/学科适配）；
- **小节生成前**：`agents/section-card-reviewers/`（承接关系、问题链、方法匹配、文献功能、转出必要性）；
- **小节写完后**：`agents/paragraph-reviewers/`（段落推进、论-据-证闭环、语言风格、引用位置、收束质量）。

## 九、交付标准

博士论文交付必须包含并如实报告：

- Markdown 工作稿、DOCX、PDF 路径；
- 字数实测（口径写明：正文/含脚注/总字符）；
- 章节结构与各章字数；
- 脚注闭环对账结果（定义数/引用数/编号连续性）；
- 参考文献数量与 GB/T 7714 状态；
- 各专项审计状态（元话语、绝对化表述、AI 痕迹、政治合规、学位论文处理）；
- 模板字段已填/待填清单；
- 目录缓存写回状态、批注修订清零状态；
- 版本回退记录（如有，作废版本不得引用其数字）；
- 查重与 AIGC 预检状态；
- 残余风险与待用户确认事项。

没有生成 Word 不能说已生成；没有审计不能说已审计；没有核验来源不能说事实可靠。质量以真实产物和证据为准。
