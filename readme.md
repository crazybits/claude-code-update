# Claude Code 生态系统动态

> 每日自动聚合，最新内容在最前。

---

## 2026-04-09

### Auto Mode：基于模型分类器的权限自动审批

- Anthropic 发布 **Auto Mode**，允许将工具调用权限审批委托给模型分类器，介于「逐次手动确认」与「无任何限制」之间，适合自动化流水线场景。这是对现有沙盒机制的补充，提升了无人值守任务的安全性与便捷性。[来源](https://www.anthropic.com/engineering/claude-code-auto-mode)

### 沙盒隔离：文件系统与网络双重隔离

- Claude Code 推出**沙盒（Sandboxing）**新功能，建立文件系统和网络两层隔离边界，大幅减少权限弹窗频次，同时提升用户安全性。该功能目前已向所有用户开放，与 Auto Mode 配合使用效果最佳。[来源](https://www.anthropic.com/engineering/claude-code-sandboxing)

### Claude Code on the Web：浏览器端云托管编程

- **Claude Code on the Web** 正式推出，用户可直接在浏览器中将编程任务委托给 Claude，任务运行在 Anthropic 管理的云端基础设施上，支持多任务并行、自动跟进 PR、修复 CI 失败及回应代码审查评论。[来源](https://www.anthropic.com/news/claude-code-on-the-web)

### Skills/插件生态快速增长

- 社区 Skills 生态持续壮大：GitHub 上已有 **340+ 插件**、**1,367+ 代理技能**可用；[claudemarketplace.com](https://claudemarketplace.com) 已收录 150+ 精选技能，支持评分与安装统计。Skills 遵循 AgentSkills.io 开放标准，可跨 Claude Code、Codex、Gemini CLI、Cursor 等多个工具复用。[来源](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4)

### MCP 工具搜索：按需加载，降低上下文消耗

- MCP 新增**工具搜索（Tool Search）**机制：会话启动时仅加载工具名称，工具定义在实际需要时才展开，大幅降低上下文占用。这意味着接入更多 MCP 服务器几乎不影响上下文窗口效率，适合复杂多工具工作流。[来源](https://code.claude.com/docs/en/mcp)

---

## 2026-04-08

### 版本发布：v2.1.89 – v2.1.96

- **v2.1.96（4月8日）** 修复 v2.1.94 引入的 Bedrock 请求 403 回归：使用 `AWS_BEARER_TOKEN_BEDROCK` 或 `CLAUDE_CODE_SKIP_BEDROCK_AUTH` 时会出现 "Authorization header is missing" 错误，本次热修复已恢复正常鉴权流程。[来源](https://github.com/anthropics/claude-code/releases)

- **v2.1.94（4月7日）** 新增 Amazon Bedrock Mantle 支持（通过 `CLAUDE_CODE_USE_MANTLE=1` 启用），API Key、Bedrock、Vertex 等用户的默认 effort 级别提升至 `high`，插件技能名称现统一使用 frontmatter `name` 字段以保证稳定调用名。[来源](https://code.claude.com/docs/en/changelog)

- **v2.1.92（4月4日）** 新增 Bedrock 设置向导（交互式 AWS 认证与模型绑定配置），`/cost` 命令新增按模型和缓存命中的费用明细，Remote Control 会话名称默认使用主机名前缀。[来源](https://code.claude.com/docs/en/changelog)

- **v2.1.91（4月2日）** MCP 工具结果持久化存储，可通过 `_meta["anthropic/maxResultSizeChars"]` 设置最大 500,000 字符，解除大文件/日志读取限制；插件支持在 `bin/` 目录中打包可执行文件；深度链接支持最多 5,000 字符的多行提示。[来源](https://code.claude.com/docs/en/changelog)

- **v2.1.90（4月1日）** 新增 `/powerup` 命令，提供带动画演示的交互式功能学习课程；`.husky` 目录加入受保护目录列表，防止 acceptEdits 模式下误修改 git hooks。[来源](https://code.claude.com/docs/en/changelog)

- **v2.1.89（4月1日）** 新增 PreToolUse hook 的 `"defer"` 延迟权限决策选项，适用于无头会话；新增 `PermissionDenied` hook 事件，支持自动模式分类器拒绝时的重试逻辑；新增 `CLAUDE_CODE_NO_FLICKER=1` 环境变量消除渲染闪烁。[来源](https://code.claude.com/docs/en/changelog)

### 订阅政策变更：第三方工具需单独付费

- 自 2026 年 4 月 4 日中午（太平洋时间）起，Claude Code 订阅者使用 OpenClaw 等第三方接入工具时，不再消耗订阅限额，需改用独立的按量付费方式。[来源](https://techcrunch.com/2026/04/04/anthropic-says-claude-code-subscribers-will-need-to-pay-extra-for-openclaw-support/)

---

## 2026-03（历史回顾）

### Claude Code Channels：接入 Discord 与 Telegram

- Anthropic 发布 Claude Code Channels，支持通过 Discord 或 Telegram 直接向 Claude Code 发送消息并委托编程任务，无需打开终端即可随时随地管理代码工作。[来源](https://venturebeat.com/orchestration/anthropic-just-shipped-an-openclaw-killer-called-claude-code-channels)

### Computer Use 与 Remote Control

- Claude Code 新增 **Computer Use** 功能：通过截图识别屏幕内容，并发出鼠标/键盘指令操作图形界面。**Remote Control** 功能允许任务启动后离开终端，随时从其他设备接管或检查运行中的会话。[来源](https://www.builder.io/blog/claude-code-updates)

### 多代理团队（Agent Teams）与检查点（Checkpoints）

- Claude Code 新增 **Agent Teams** 研究预览功能，可并行启动多个协调运作的代理。**Checkpoint** 系统在每次变更前自动保存代码状态，执行 `/rewind` 即可回退。[来源](https://www.anthropic.com/news/enabling-claude-code-to-work-more-autonomously)

### Claude Code 安全扫描功能（研究预览）

- Anthropic 推出 Claude Code Security，对代码库进行安全漏洞扫描并生成针对性补丁建议，能发现传统静态分析工具难以捕获的漏洞类型，目前以限量研究预览形式开放。[来源](https://www.anthropic.com/news/claude-code-security)
