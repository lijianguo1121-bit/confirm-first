---
name: confirm-first
description: Pre-execution confirmation gate. Use when the user invokes "/确认", "/confirm", "confirm first", "先问我", "先列清单", "check with me first", or otherwise asks Kimi to analyze a request and present a selectable checklist of scenarios/sub-tasks BEFORE executing anything. Kimi proposes candidate work items with sensible defaults pre-checked, the user ticks or adjusts the selection, and only the confirmed items get executed — preventing unwanted automatic work.
---

# Confirm First

Turn a simple command into an explicit, user-approved execution plan. Nothing runs until the user confirms the checklist.

## Workflow

1. **Restate the goal** in one sentence, so misunderstandings surface early.
2. **Decompose** the request into 3–10 candidate items. Each item is one actionable sub-task or scenario the user might want. Mark recommended items `[x]` (with a short reason) and optional ones `[ ]`.
3. **Present the checklist and STOP.** Do not call tools, create files, or execute anything before the user replies.
4. **Interpret the reply generously**: numbers ("1 3 4"), exclusions ("不要 2"), "全部", "按推荐执行" all count. If genuinely ambiguous, ask one short question.
5. **Execute only confirmed items.** Skipped items must not be performed — not even as "helpful" extras mid-workflow.
6. **Report** results grouped by item, and explicitly list what was skipped.

## Checklist format

```
我理解你的目标是：<一句话复述>

建议执行以下事项（回复编号调整，如 "1 3 4" 或 "不要 2"）：
- [x] 1. <事项>（推荐：<原因>）
- [x] 2. <事项>
- [ ] 3. <事项>（可选：<什么时候需要它>）

回复"全部"或"按推荐执行"也可以。
```

## Rules

- Never smuggle unconfirmed steps into a confirmed item.
- If new necessary steps emerge mid-execution, pause and re-confirm with a mini checklist.
- Keep the checklist scannable: at most 10 items, one line each.
- If the user's request is already fully specific (e.g. "只改第 3 页标题"), skip the checklist and say why.
