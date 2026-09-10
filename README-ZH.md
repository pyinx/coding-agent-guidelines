# Coding Agent Guidelines

一套面向 Codex 和 Claude Code 的精简、高可靠编码基线。

这些规则约束智能体的行为，但不规定具体工具、工作流或项目架构。

## 为什么需要

编码智能体通常不是因为缺少指令而失败，而是因为判断失误。

一组约束在每一步都生效：绝不编造、绝不伪装成功，未经确认不做破坏性操作，让面向用户的决策以用户目标和产品语境为依据，覆盖完整且可访问的流程，并在命名、架构和行为上保持一致。规则冲突时，按明确的优先级顺序裁决。

在此之上，五种持久有效的行为按序推进：

1. 理解目标，并指出请求中错误或缺失的部分。
2. 设计方案前，先理解现有系统。
3. 设计最小方案，不承载任何未被要求的东西。
4. 在保留契约的前提下，实施外科手术式的变更。
5. 声明成功前，用最新证据验证结果。

## 文件

| 文件 | 用途 |
| --- | --- |
| `AGENTS.md` | Codex 和其他兼容智能体的规范唯一来源。 |
| `CLAUDE.md` | Claude Code 入口，负责导入 `AGENTS.md`。 |
| `skills/coding-guidelines/SKILL.md` | 独立 skill 包。正文是 `AGENTS.md` 的副本，以便单独分发。 |

以 `AGENTS.md` 为准。将 `CLAUDE.md` 保持为兼容入口。

## 安装

克隆仓库：

```sh
mkdir -p ~/.config
git clone https://github.com/pyinx/coding-agent-guidelines.git ~/.config/coding-agent-guidelines
```

### 项目级

将两个文件复制到新项目根目录：

```sh
cp -n ~/.config/coding-agent-guidelines/AGENTS.md ./AGENTS.md
cp -n ~/.config/coding-agent-guidelines/CLAUDE.md ./CLAUDE.md
```

提交这两个文件，让所有贡献者使用相同规范。

### 全局

将规范链接到两个智能体的配置目录：

```sh
mkdir -p ~/.codex ~/.claude
ln -s ~/.config/coding-agent-guidelines/AGENTS.md ~/.codex/AGENTS.md
ln -s ~/.config/coding-agent-guidelines/AGENTS.md ~/.claude/AGENTS.md
ln -s ~/.config/coding-agent-guidelines/CLAUDE.md ~/.claude/CLAUDE.md
```

Claude Code 的链接会保留相对路径 `@AGENTS.md` 的导入关系。

如果目标文件已存在，请合并内容，不要盲目覆盖现有规范。

修改指令文件后，请启动新的智能体会话。

## 定制

保持全局规则通用。将项目命令和架构边界放在各自仓库中。

仅在规则缺失会反复导致具体问题时添加规则。

优先写原则，而非工具名称。优先写约束，而非流程清单。

删除重复平台默认行为或无法影响实际决策的规则。

## 贡献

保持变更精简且有充分依据。

说明每条新增规则要解决的失败模式。

先修改 `AGENTS.md`。将 `CLAUDE.md` 保持为导入入口。

修改 `AGENTS.md` 后，必须同步 `skills/coding-guidelines/SKILL.md` 的正文，二者需逐字一致。

## 许可证

本项目尚未声明许可证。
