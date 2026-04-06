# 全局 Claude Code 行为规则

## 对话流程规则

**重要：每次回复结束后，必须使用 `AskUserQuestion` 工具弹出选择框，询问用户的下一步指示。不允许主动结束对话。**

选择框应包含当前上下文中合理的后续操作选项，例如：
- 继续当前任务的下一步
- 相关的其他操作
- 结束当前任务

这条规则适用于所有对话和所有项目，无论任务类型。

## 执行前确认规则

**重要：在修改任何代码或执行任何命令之前，必须先通过 `AskUserQuestion` 工具向用户说明操作计划并请求确认，得到用户明确同意后方可执行。禁止用普通文本等待用户回复来代替此流程。**

具体要求：
- 在同一轮回复中，用 `AskUserQuestion` 描述将要进行的修改内容或执行的命令及其原因
- 选项至少包含"确认，执行"和"取消"
- 收到用户通过 `AskUserQuestion` 的确认回复后，再进行实际操作

此规则适用于：代码编辑、文件创建/删除、Shell 命令执行、配置变更等一切实质性操作。对话期间所有交互均应保持在同一会话中，不得中断。

## 开发工作流偏好（Superpowers 集成）

当涉及以下场景时，应主动通过 AskUserQuestion 建议用户使用对应的 Superpowers 技能：

- **新功能/创意讨论** → 建议 `/brainstorming`
- **多步骤实现任务** → 建议 `/writing-plans`
- **编写代码** → 遵循 TDD 原则（建议 `/test-driven-development`）
- **遇到 bug/测试失败** → 建议 `/systematic-debugging`
- **声称任务完成前** → 建议 `/verification-before-completion`
- **代码审查** → 建议 `/requesting-code-review`
- **分支合并/PR** → 建议 `/finishing-a-development-branch`

注意：建议使用技能时，通过 AskUserQuestion 提供选项让用户决定是否启用，
不强制每次都走完整流程。简单任务可直接执行。
