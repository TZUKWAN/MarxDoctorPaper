# MarxDoctorPaper

马克思主义理论博士毕业论文生产技能。以 EMARX v7.5 为内核，针对博士学位论文的篇幅、章节体系、学校模板和盲审场景加固，覆盖选题、文献底座、开题结构、分章写作、论述深化、全稿审校到 Word/PDF 交付的全流程。

## 适用场景

- 马克思主义理论一级学科（0305）博士学位论文：马克思主义基本原理、马克思主义中国化研究、思想政治教育、国外马克思主义研究、马克思主义发展史、中国近现代史基本问题研究；
- 党史党建、政治学、历史学等相邻学科的纯文字性学位论文也可参照使用；
- 典型对象：人物思想研究、理论问题研究、思想史研究、概念谱系研究。

## 默认规格

- 正文 **17—18 万字**（以学校规范为准）；
- 绪论 + 4—6 章主体 + 结语，中英文摘要，目录缓存写回打开即见；
- 页下注圈码 ①②③ 每页重编号，GB/T 7714 著录；
- 学校模板套用，个人信息占位字段不虚构。

## 核心特性

### 博士论文专用

- **章节系统**：绪论五件事、章下小引言禁止自指、各章功能边界（形成条件/思想演进/核心内容/理论分析/历史评价各司其职）、段落硬规则（段首禁指代词、一句话一个脚注）；
- **苏格拉底式深化**：字数不足时围绕核心对象做中介问题追问（转化链/实践链/关系链/评价尺度/断裂与连续），禁止空话凑字数；
- **绝对化表述门槛**："第一次""填补空白""源头"必须有同期比较和传播证据；"二百余篇""绝大多数"必须有篇目表和统计口径；
- **学位论文文献库**：[D] 引用逐条溯源改引到原始文献，禁止同题替换，正文禁出现身份括注；
- **学校模板交付**：模板字段占位管理、目录缓存写回、批注修订清零、PDF 逐页抽查。

### 继承自 EMARX

- 先读工作空间真实资料、锚定精读、来源到论点映射；
- 三重 subagent 逻辑审查（大纲/小节论证卡/段落）；
- 内置 CNKI：文献不足自动触发检索，候选文献功能绑定后才可引用；
- 经典文本向量检索：马恩全集与治国理政向量库，核验原句卷页、找理论源头、政治合规核验；
- 审计先行两阶段 + 版本回退机制；
- 脚注工程化：一注一证、闭环对账、语义归并、书级著录；
- AI 痕迹控制与保真编辑规则、政治合规协议；
- 零配置环境：首次运行脚本自动创建隔离 venv、装依赖、下载浏览器。

## 安装

### Kimi Code CLI

```bash
kimi skill install https://github.com/TZUKWAN/MarxDoctorPaper.git
```

### 手动

```bash
git clone https://github.com/TZUKWAN/MarxDoctorPaper.git
# Windows: 复制到 C:\Users\<用户名>\.kimi\skills\marx-doctor-paper
# macOS/Linux: 复制到 ~/.kimi/skills/marx-doctor-paper
```

首次使用时脚本自动完成环境配置（约几分钟）。唯一需要手动安装的外部程序是 pandoc（https://pandoc.org/installing.html）。

详见 `INSTALL.md`。

## 快速开始

把技能交给 AI，说明论文题目、学校规范和工作空间位置即可。AI 会按 `references/dissertation-workflow.md` 推进：

```bash
# 文献缺口诊断（不足时自动触发 CNKI）
python scripts/emarx_literature_gap.py --workspace workspace --topic "论文题目"

# 脚注工程化审计
python scripts/footnote_audit.py --paper paper.md --output footnote-audit.json

# Word 交付 + 后处理
python scripts/emarx_build_docx.py paper.md paper.docx
python scripts/emarx_finalize_docx.py paper.docx --update-toc
```

## 目录结构

```text
marx-doctor-paper/
├── SKILL.md                        # 技能总入口
├── README.md / INSTALL.md
├── requirements.txt
├── references/                     # 协议库（6 个博士专用 + 17 个 EMARX 内核）
│   ├── dissertation-workflow.md
│   ├── chapter-system-protocol.md
│   ├── socratic-deepening-protocol.md
│   ├── absolute-claims-gate.md
│   ├── meta-discourse-audit.md
│   ├── school-template-protocol.md
│   └── ...
├── scripts/                        # 审计/交付/CNKI 脚本（含内置 cnki 模块）
└── agents/                         # 15 个逻辑审查 subagent
```

## 边界

MarxDoctorPaper 组织研究逻辑、生产论文草稿、生成 Word 并做格式审计，但不保证所有事实、政策、案例、页码自动为真。涉及最新事实、政策法规、直接引语、页码和学校格式细则时，必须回到来源和学校规范文件核验。学位论文的学术责任由作者本人承担。
