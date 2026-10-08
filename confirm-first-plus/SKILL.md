---
name: confirm-first-plus
description: TEST VERSION — pre-execution confirmation gate with automatic GitHub tool matching. Use when the user invokes "/确认+", "/confirm+", "confirm first plus", "先问我再匹配工具", or wants Kimi to (1) present a tick-able checklist of scenarios/sub-tasks before executing, and (2) for each confirmed item, automatically search GitHub for the strongest matching open-source tool, agent skill, or MCP server, then execute with it after a quick confirmation. Prevents unwanted automatic work and upgrades execution with best-in-class community tools.
---

# Confirm First Plus (test)

Extends `confirm-first`: confirmation gate + automatic matching of the best GitHub tools/skills for each confirmed item.

## Phase 1 — Confirm the plan (same as confirm-first)

1. Restate the goal in one sentence.
2. Decompose into 3–10 candidate items: recommended `[x]` with reason, optional `[ ]`.
3. Present the checklist and STOP — execute nothing before the user replies.
4. Interpret replies generously ("1 3 4", "不要 2", "全部", "按推荐执行").

## Phase 2 — Match tools for confirmed items

For each confirmed item, in order of preference:

1. **Already available**: check skills/plugins/CLIs already installed in the current environment — using them costs nothing and carries no install risk.
2. **GitHub search** (when nothing local fits):
   - Derive 1–3 search queries from the item: task type + domain/format, e.g. `pdf merge cli`, `mcp server notion`, `screenshot tool`.
   - Search repositories sorted by stars; also check relevant `awesome-*` lists and MCP server registries/collections.
   - If a query returns 0 results, broaden it: drop the stars filter, drop one keyword, or switch to the task's generic name. Never report "no tool exists" after a single narrow query.
   - Score candidates: stars, last commit within ~12 months, README quality, installability in this environment (npm/pip/brew CLI, MCP plugin, or pure-prompt skill).
3. Pick ONE best match per item. If nothing scores well, mark the item **built-in** and plan to execute with native capabilities.

## Phase 3 — Confirm the tool mapping (keep it short)

```
工具匹配方案（回复"确认"执行，或指出要换的行）：
1. <事项> → <工具名> ★<星数>（<一句话说明>，<使用方式：已装/需安装/内置>）
2. <事项> → 内置能力（GitHub 上没有明显更优的工具）
```

Default gate: wait for confirmation. Skip the wait only if the user has said "工具也自动定" in this conversation.

## Phase 4 — Execute and verify

- Prefer installed tools; ask before installing anything new.
- Never run a tool the user rejected; never smuggle unconfirmed steps into an item.
- After each item, verify the output exists/works before moving on.
- If a tool fails mid-run, fall back to the runner-up candidate or built-in capability, and say so.
- Final report: results per item, skipped items, and the tool used per item (so the user can reuse the mapping).

## Rules

- Checklist stays scannable: ≤ 10 items, one line each.
- If the request is already fully specific, say so and skip Phase 1 — but Phase 2/3 still apply when the task could benefit from a specialized tool.
- Star counts and activity are observed facts from search results — report what was actually found, never guess numbers.
