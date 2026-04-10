# Claude Code 生态系统动态

> 每日自动聚合，最新内容在最前。

---

## 2026-04-10

### 版本发布：v2.1.97 – Focus View、Bedrock 向导与 PowerShell 预览

- **v2.1.97（4月8日）** 新增 **Focus View 切换**（`Ctrl+O`，仅限 `NO_FLICKER` 模式），聚焦后只显示当前提示词、工具摘要（含编辑 diffstat）及最终响应，有效减少视觉噪音；新增状态栏 `refreshInterval` 配置项，支持每 N 秒自动刷新。[来源](https://code.claude.com/docs/en/changelog)

- 新增**互动式 Amazon Bedrock 设置向导**，引导完成 AWS 认证、区域配置与模型绑定，与 Vertex AI 向导流程保持一致；同时上线 **PowerShell 工具（预览版，Windows 专属）**，带有危险命令检测。修复了 MCP HTTP/SSE 连接以约 50MB/小时速率累积未释放缓冲区的内存泄漏问题。[来源](https://code.claude.com/docs/en/changelog)

### Claude Mythos Preview + Project Glasswing：千计零日漏洞被发现

- Anthropic 发布 **Claude Mythos Preview** 的安全评估报告：使用该模型对主流操作系统和浏览器进行扫描，共发现**数千个此前未知的零日漏洞**，其中最古老的漏洞存在于 OpenBSD 中长达 27 年。该模型由 Claude Code 驱动，能自动读取代码、验证假设并输出带 PoC 的漏洞报告。[来源](https://red.anthropic.com/2026/mythos-preview/)

- Anthropic 同步发布 **Project Glasswing**：邀请 AWS、Apple、Cisco、Google、Microsoft、Nvidia 等主要科技企业优先使用 Mythos Preview 开展**防御性安全工作**并向行业共享发现成果，以在攻击者利用类似能力之前抢先修复漏洞。目前 Mythos 仅以受控预览形式向少数合作方开放。[来源](https://fortune.com/2026/04/07/anthropic-claude-mythos-model-project-glasswing-cybersecurity/)

---

## 2026-04-09

### 版本发布：v2.1.98 – Vertex AI 向导、Perforce 集成与安全加固

- **v2.1.98（4月9日）** 新增 **Google Vertex AI 交互式设置向导**（从登录界面"第三方平台"入口可访问，引导完成 GCP 认证、项目/区域配置及模型绑定），并引入 **Perforce 集成**（`CLAUDE_CODE_PERFORCE_MODE` 环境变量，只读文件写入时会给出 `p4 edit` 提示）。新增 **Monitor 工具**用于流式接收后台脚本事件，子进程沙盒在 Linux 上支持 PID 命名空间隔离（需设置 `CLAUDE_CODE_SUBPROCESS_ENV_SCRUB`）。[来源](https://code.claude.com/docs/en/changelog)

- 安全方面修复了 Bash 工具**反斜杠转义标志权限绕过漏洞**和**复合命令绕过强制权限提示**问题；同步修复 MCP OAuth 刷新令牌在 ADFS 等 IdP 下失效、429 重试未应用指数退避等问题。[来源](https://code.claude.com/docs/en/changelog)

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
