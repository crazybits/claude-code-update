# Claude Code 生态系统资讯聚合

> 每日自动聚合最新 Claude Code 动态，内容按日期倒序排列（最新在前）。

---

## 2026-04-08

### 安全能力：Claude Code Security 发布研究预览

Anthropic 推出 **Claude Code Security**，现可通过 Claude Code on the Web 访问（限量研究预览阶段）。该功能可自动扫描代码库中的安全漏洞，并为人工审核提供针对性的补丁建议，能够识别传统工具常常遗漏的安全问题。[来源](https://www.anthropic.com/news/claude-code-security)

### 新模型：Claude Opus 4.6 与 Claude Sonnet 4.6 正式发布

Anthropic 发布 **Claude Opus 4.6** 与 **Claude Sonnet 4.6**。Claude Sonnet 4.6 在 GDPval-AA Elo 榜单以 1,633 分领先，实现了接近 Opus 级别的性能却以 Sonnet 价格提供。Claude Opus 4.6 进一步提升了推理深度和代码生成质量。[来源](https://www.anthropic.com/news/claude-opus-4-6)

### 预览：Claude Mythos — 万亿参数旗舰模型

Anthropic 在 red.anthropic.com 公布 **Claude Mythos** 预览版，参数规模达 10 万亿，目标是在推理、多步骤代理任务和科学研究场景大幅超越现有前沿模型。这是 Anthropic 迄今为止最大规模的模型预告。[来源](https://red.anthropic.com/2026/mythos-preview/)

### MCP 生态里程碑：97M 次安装，10,000+ 服务器

**Model Context Protocol（MCP）** 月安装量突破 9,700 万次，已有超过 10,000 个活跃服务器，覆盖 GitHub、Slack、Figma、PostgreSQL、Notion 等主流平台。MCP 已成为 AI 代理接入外部工具的事实标准，被 Cursor、VS Code Copilot、LangChain 等广泛采用。[来源](https://modelcontextprotocol.io/)

### 自主能力升级：Auto Mode 与沙盒安全机制

Claude Code 推出 **Auto Mode**，由模型分类器接管权限审批决策，介于人工确认与完全无守卫之间，在安全性和效率之间取得新平衡。同期上线的沙盒机制提供文件系统与网络双重隔离，大幅减少权限弹窗。[来源](https://www.anthropic.com/engineering/claude-code-auto-mode)

### 重大事故：Claude Code 源代码意外泄露

2026 年 3 月 31 日 00:21 – 03:29 UTC，Anthropic 在 npm 包中意外附带了 **512,000 行 Claude Code 完整源代码**，持续约 3 小时。Anthropic 随后确认了该事件，已紧急处理并审查影响范围。这是 Claude Code 迄今最受关注的安全事件之一。[来源](https://medium.com/data-and-beyond/claude-code-leak-2026-agentic-ai-architecture-db5adcebbe69)

### 版本发布速览：v2.1.89 – v2.1.96

| 版本 | 日期 | 亮点 |
|------|------|------|
| v2.1.96 | 4月8日 | 修复 Bedrock 鉴权 403 热修复 |
| v2.1.94 | 4月7日 | Amazon Bedrock Mantle 支持，默认 effort 提升至 `high` |
| v2.1.92 | 4月4日 | Bedrock 设置向导，`/cost` 费用明细 |
| v2.1.91 | 4月2日 | MCP 工具结果持久化（最大 500K 字符），`bin/` 目录打包 |
| v2.1.90 | 4月1日 | `/powerup` 交互式学习命令 |
| v2.1.89 | 4月1日 | PreToolUse hook `defer` 选项，`PermissionDenied` 事件 |

[完整更新日志](https://github.com/anthropics/claude-code/releases)

### Skills 与插件生态系统持续壮大

**Skills** 现遵循 [AgentSkills.io](https://agentskills.io) 开放标准，可跨 Claude Code、Codex CLI、Gemini CLI、Cursor 等工具复用。GitHub 上已汇聚 **340+ 插件 + 1,367+ 代理技能**，`/feature-dev` 插件安装量超 89,000 次，成为最受欢迎的开发工作流工具。[来源](https://github.com/hesreallyhim/awesome-claude-code)

### 第三方工具计费政策调整

自 2026 年 4 月 4 日起，使用 **OpenClaw** 等第三方接入工具时，不再消耗订阅限额，需改用独立的按量付费方式。Anthropic 表示订阅计划未针对此类使用模式设计，需可持续管理用量增长。[来源](https://techcrunch.com/2026/04/04/anthropic-says-claude-code-subscribers-will-need-to-pay-extra-for-openclaw-support/)

---

> 数据来源：Anthropic 官网、GitHub Releases、TechCrunch、MCP 官网、社区整理
