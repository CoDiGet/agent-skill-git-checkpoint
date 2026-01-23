# Agent Skill: Git Local Checkpoint 🛡️

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

一个专为 AI Agent 设计的 "Skill" 模块。
当 AI 助手修改你的代码后，它会自动执行 `git commit` 进行本地存档，防止代码丢失或改乱。

> **核心特性：只在本地存档，绝不 Push。安全第一。**

## ✨ 功能特点

- **🔄 全自动触发**：配置后，AI 改完代码会自动保存，无需人类口头指令。
- **🧠 风格模仿**：AI 会读取你项目现有的 `git log`，模仿你的提交风格（中文/英文/Emoji/Conventional Commits）。
- **🔒 安全沙箱**：内置 Explicit Constraints，严禁 AI 执行 `git push`，避免污染远程仓库。
- **🔌 标准格式**：符合 Anthropic / Spring AI 等框架定义的 `SKILL.md` 标准。

## 🚀 如何使用

### 1. 下载 Skill
将本仓库中的 `skills/git-checkpoint/SKILL.md` 复制到你的 Agent 项目的技能目录中。

### 2. 工具依赖
你的 Agent 环境需要具备执行 Shell 命令的能力（通常通过 Function Calling 实现）。
确保你的 Agent 挂载了一个名为 `run_shell_command` 的工具。

### 3. 集成示例 (System Prompt)

虽然 `SKILL.md` 中已经包含触发规则，但为了效果最佳，建议在你的主 System Prompt 中也提及：

```text
You have a skill named "git-local-checkpoint". 
Protocol: Always run this skill automatically after you finish editing any code files. 
Treat it as a strictly local "Ctrl+S" operation.
```

🛠️ 工作流程演示
```text
用户: "把 main.py 里的端口改成 8080。"

AI Agent:

🛠️ 调用 write_file 修改代码。

🤖 触发 Auto-Trigger Protocol。

📖 读取 git log，发现你喜欢用 emoji 风格 (e.g., "✨ feat: ...").

💾 执行 git add . && git commit -m "⚡ perf: change port to 8080"。

💬 回复用户: "已修改端口为 8080，并自动创建本地备份。"
```
---
⚠️ 免责声明
此 Skill 仅执行本地 Git 操作。虽然设有安全限制，但请确保在受控环境中使用 AI 执行 Shell 命令。建议在开发分支上使用。

License
MIT
