# Claude Code 生态系统动态

> 每日自动聚合，最新内容在最前。

---

## 2026-04-08

### 版本发布：v2.1.89 – v2.1.94

- **v2.1.94（4月7日）** 新增 Amazon Bedrock Mantle 支持（通过 `CLAUDE_CODE_USE_MANTLE=1` 启用），API Key、Bedrock、Vertex 等用户的默认 effort 级别提升至 `high`，插件技能名称现统一使用 frontmatter `name` 字段以保证稳定调用名。[来源](https://code.claude.com/docs/en/changelog)

- **v2.1.92（4月4日）** 新增 Bedrock 设置向导（交互式 AWS 认证与模型绑定配置），`/cost` 命令新增按模型和缓存命中的费用明细，Remote Control 会话名称默认使用主机名前缀。[来源](https://code.claude.com/docs/en/changelog)

- **v2.1.91（4月2日）** MCP 工具结果持久化存储，可通过 `_meta["anthropic/maxResultSizeChars"]` 设置最大 500,000 字符，解除大文件/日志读取限制；插件支持在 `bin/` 目录中打包可执行文件；深度链接支持最多 5,000 字符的多行提示。[来源](https://code.claude.com/docs/en/changelog)

- **v2.1.90（4月1日）** 新增 `/powerup` 命令，提供带动画演示的交互式功能学习课程；`.husky` 目录加入受保护目录列表，防止 acceptEdits 模式下误修改 git hooks。[来源](https://code.claude.com/docs/en/changelog)

- **v2.1.89（4月1日）** 新增 PreToolUse hook 的 `"defer"` 延迟权限决策选项，适用于无头会话；新增 `PermissionDenied` hook 事件，支持自动模式分类器拒绝时的重试逻辑；新增 `CLAUDE_CODE_NO_FLICKER=1` 环境变量消除渲染闪烁。[来源](https://code.claude.com/docs/en/changelog)

### Skills 与插件生态系统

- Skills 现遵循 [AgentSkills.io](https://agentskills.io) 开放标准，可跨 Claude Code、Codex、Gemini CLI、Cursor 等多个 AI 工具复用；Custom Commands 已完全合并进 Skills 系统，旧路径向后兼容。插件可通过 `bin/` 目录分发可执行文件，扩展能力进一步增强。[来源](https://code.claude.com/docs/en/skills)

- 社区生态快速成长：GitHub 上已有 340+ 插件、1,367+ 代理技能可用；[claudemarketplace.com](https://claudemarketplace.com) 已收录 150+ 精选技能，提供评分与安装统计。[来源](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4)

### 订阅政策变更：第三方工具需单独付费

- 自 2026 年 4 月 4 日中午（太平洋时间）起，Claude Code 订阅者使用 OpenClaw 等第三方接入工具时，不再消耗订阅限额，需改用独立的按量付费方式。这标志着 Anthropic 开始区分官方渠道与第三方 harness 的计量边界。[来源](https://techcrunch.com/2026/04/04/anthropic-says-claude-code-subscribers-will-need-to-pay-extra-for-openclaw-support/)

---

## 2026-03（历史回顾）

### Claude Code Channels：接入 Discord 与 Telegram

- Anthropic 发布 Claude Code Channels，支持通过 Discord 或 Telegram 直接向 Claude Code 发送消息并委托编程任务，无需打开终端即可随时随地管理代码工作。这被视为对 OpenClaw 等第三方聊天接入工具的官方替代方案。[来源](https://venturebeat.com/orchestration/anthropic-just-shipped-an-openclaw-killer-called-claude-code-channels)

### Computer Use 与 Remote Control

- Claude Code 新增 **Computer Use** 功能：通过截图识别屏幕内容，并发出鼠标/键盘指令操作图形界面，支持网页应用自动化和表单填写等场景。**Remote Control** 功能允许任务启动后离开终端，随时从其他设备接管或检查运行中的会话。[来源](https://www.builder.io/blog/claude-code-updates)

### Cloud Auto-Fix：云端自动处理 PR 反馈

- 网页版与移动端会话现在可在 Anthropic 管理的云端基础设施上自动跟进 Pull Request、修复 CI 失败并回应代码审查评论，无需开发者持续守候，返回即可得到一个就绪的 PR。[来源](https://www.builder.io/blog/claude-code-updates)

### 多代理团队（Agent Teams）与检查点（Checkpoints）

- Claude Code 新增 **Agent Teams** 研究预览功能，可并行启动多个协调运作的代理，适合可拆分为独立只读子任务的大规模代码审查等场景。**Checkpoint** 系统在每次变更前自动保存代码状态，按两次 Esc 或执行 `/rewind` 即可回退，降低大规模重构风险。[来源](https://www.anthropic.com/news/enabling-claude-code-to-work-more-autonomously)

### Claude Code 安全扫描功能（研究预览）

- Anthropic 推出 Claude Code Security，可对代码库进行安全漏洞扫描并生成针对性补丁建议供人工审核，能发现传统静态分析工具难以捕获的漏洞类型，目前以限量研究预览形式开放。[来源](https://www.anthropic.com/news/claude-code-security)
