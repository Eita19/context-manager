# Context Manager

[![Stars](https://img.shields.io/github/stars/Eita19/context-manager?style=flat)](https://github.com/Eita19/context-manager)
[![Based on](https://img.shields.io/badge/based-Claude%20Code-7B68EE?style=flat)](https://github.com/anthropics/skills)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

> **Long session context management for AI agents** — based on Claude Code's autoCompact system

**Handle long sessions without losing focus. Auto-compress, protect tail, budget tokens.**

---

## What is Context Manager?

When conversations get long, AI agents lose track. Context Manager teaches your agent to:

- **Protect the tail** — Keep recent context untouched
- **Compress smart** — Shrink without losing meaning
- **Budget tokens** — Know when to compress before hitting limits

---

## When to Use

- Session exceeds 80% of token limit
- Long task with many steps
- Sub-agent results need synthesis
- "Context getting full" warnings appear

---

## Core Concept: Protected Tail

Always keep these untouched:
- Last 5 user messages
- Last 3 assistant messages
- Current task context
- Critical decisions made

---

## Compression Triggers

| Level | Token Usage | Action |
|-------|------------|--------|
| Warning | >80% | Micro-compact tool results |
| Danger | >90% | Fold early messages to summary |
| Critical | >95% | Emergency compress + warn |

---

## Compression Types

### Micro-Compact
```
[Tool: file_edit] 150 lines → [File edited: 3 files modified]
[Tool: bash] 89 lines → [Command completed: npm install]
```

### Context Fold
```
[Messages 1-50] → [Early discussion: resolved X, decided Y]
```

---

## Token Budget

Track for long tasks:
```
Budget: 500k tokens
Used: 234k (46%)
Remaining: 266k
Action: Enable auto-compact at 400k
```

---

## Quick Start

```bash
clawhub install context-manager
```

---

*Based on [Claude Code autoCompact](https://github.com/anthropics/skills)*
