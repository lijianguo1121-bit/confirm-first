# confirm-first

一个让 AI 在动手前先和你确认的 skill：给一个简单命令，AI 会先分析你可能需要的场景/子任务，列出一份可勾选的清单，你确认之后才执行——避免 AI 自动做一堆你不需要的事。

An AI agent skill that adds a pre-execution confirmation gate: give a simple command, the agent analyzes which scenarios/sub-tasks you probably need, presents a tick-able checklist, and only executes what you confirm.

## 触发方式 | Triggers

- `/确认` 或 `/confirm`
- 自然语言：「先问我」「先列清单」「check with me first」

## 工作流程 | Workflow

1. AI 用一句话复述你的目标
2. 拆解出 3–10 个候选事项，推荐的预勾选 `[x]`，可选的留空 `[ ]`
3. **停下等你确认**，不执行任何操作
4. 你回复编号（`1 3 4`）、排除项（`不要 2`）、`全部` 或 `按推荐执行`
5. AI 只执行你确认的事项，跳过的一项都不会做

示例：

```
我理解你的目标是：把这份季度数据做成汇报材料

建议执行以下事项（回复编号调整，如 "1 3 4" 或 "不要 2"）：
- [x] 1. 清洗数据并计算核心指标（推荐：后续所有产出都依赖它）
- [x] 2. 生成趋势图表
- [ ] 3. 写成 Word 报告（可选：如果只是内部看一眼可以不要）
- [ ] 4. 做成 PPT（可选：需要汇报时再勾）

回复"全部"或"按推荐执行"也可以。
```

## 安装 | Install

### Kimi Work

从 [Releases](../../releases) 下载 `confirm-first.skill` 并导入，或直接把这个仓库里的 `SKILL.md` 放到你的 skills 目录：

```
~/.config/agents/skills/confirm-first/SKILL.md
```

### 其他 agent 平台 | Other agent platforms

这就是一个标准的 `SKILL.md`（YAML frontmatter + Markdown 指令），兼容任何支持 skills 的 agent 运行时（Kimi Code、Claude Code 等），把 `SKILL.md` 放进对应的 skills 目录即可。

## 测试版：confirm-first-plus 🧪

`confirm-first-plus/` 是增强测试版：在确认清单之后，自动为每个事项**在 GitHub 上匹配最强的开源工具 / skill / MCP 服务**（优先本地已装、其次高星活跃项目），给出「事项 → 工具」的映射方案，你确认后才执行。

- 触发：`/确认+` 或 `/confirm+`
- 流程：确认清单 → 匹配工具 → 确认映射 → 执行并验证
- 规则：星数和活跃度只报实际搜到的结果；你拒绝的工具绝不使用；安装任何新工具前必先询问

## 设计原则 | Design principles

- **清单即边界**：被跳过的事项绝不执行，连"顺手帮忙"也不行
- **随时可打断**：执行中发现新的必要步骤，会停下来再次确认
- **零依赖**：基础版纯文本交互，不需要任何插件或小组件，任何对话环境都能用；plus 版只需要一个 GitHub 搜索入口

## License

[MIT](LICENSE)
