# MarxDoctorPaper 安装说明

## 一、技能信息

- **技能名称**：`marx-doctor-paper`
- **仓库地址**：`https://github.com/TZUKWAN/MarxDoctorPaper.git`
- **适用场景**：马克思主义理论及相关人文社科学科博士学位论文的选题、写作、审校与 Word/PDF 交付。
- **默认输出**：Markdown 工作稿 + DOCX + PDF。

## 二、安装方式

### 方式 1：Kimi Code CLI 命令安装（推荐）

```bash
kimi skill install https://github.com/TZUKWAN/MarxDoctorPaper.git
```

### 方式 2：手动克隆

```bash
git clone https://github.com/TZUKWAN/MarxDoctorPaper.git
# Windows: C:\Users\<用户名>\.kimi\skills\marx-doctor-paper
# macOS/Linux: ~/.kimi/skills/marx-doctor-paper
cp -r MarxDoctorPaper/* ~/.kimi/skills/marx-doctor-paper/
```

### 方式 3：Project scope

把仓库内容放入当前项目的 `.codex/marx-doctor-paper/` 目录，CLI 会自动识别为项目级 skill。

## 三、安装后验证

让 AI 读取 `SKILL.md` 确认加载成功，或运行一次快速自检：

```bash
python scripts/footnote_audit.py --help
```

能输出帮助信息即说明脚本链路正常。

## 四、首次使用：零配置

AI 首次调用 CNKI 或 Word 相关脚本时，脚本会自动：

1. 在技能目录下创建隔离虚拟环境 `.venv/`；
2. 安装全部 Python 依赖（python-docx、pywin32、playwright、ddddocr 等）；
3. 下载 Playwright Chromium 浏览器；
4. 切换到虚拟环境继续执行原命令。

首次配置可能需要 3—10 分钟，AI 应提前告知用户。用户不需要手动 `pip install` 或 `playwright install`。

**pandoc 无法自动安装**（Word 交付需要）。若未安装，AI 会提示从 https://pandoc.org/installing.html 安装。

## 五、使用流程

1. 告诉 AI：论文题目、学校规范文件（如有）、工作空间位置；
2. AI 按 `references/dissertation-workflow.md` 推进：规范确认→选题→文献底座→开题结构→分章写作→深化→审校→交付；
3. 中途任何阶段的产物（问题清单、大纲、论证卡、审计报告）都会落盘，可中断可恢复。

## 六、注意事项

1. 博士论文默认正文 17—18 万字，以学校规范为准；
2. 模板个人信息字段不虚构，由用户填写；
3. Windows 上 Word/WPS 交付链最稳定；
4. `.venv/` 已在 `.gitignore` 中排除，不要提交。

## 七、故障排查

| 现象 | 原因 | 处理 |
|---|---|---|
| 缺 Python 依赖 | 自动安装中断 | 重跑任意脚本，会自动补装 |
| 缺 Chromium | 浏览器下载失败 | 重跑脚本或检查网络 |
| Word 生成失败 | 缺 pandoc | 安装 pandoc 并加入 PATH |
| Word 构建静默失败 | 文件被 WPS/Word 占用 | 关闭占用进程后重建 |
| CNKI 被反爬 | 验证码拦截 | 用 `--no-headless` 手动过验证 |

## 八、更新

```bash
kimi skill update marx-doctor-paper
```

或重新克隆覆盖 skill 目录（保留 `.venv/` 避免重复下载）。
