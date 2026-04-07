---
title: "Agent Loop (ReAct)"
type: concept
sources: [raw/initial-research/01_alapfogalmak.md]
related: [concepts/tool-use, concepts/planning-strategies, concepts/memory-types]
created: 2026-04-07
updated: 2026-04-07
coverage: medium
confidence: high
---

# Agent Loop (ReAct)

## Definíció

Az LLM Agent autonóm rendszer: érzékel → következtet → cselekszik → megismétli.

**ReAct** (Reasoning + Acting, Yao et al. 2022): `Thought → Action → Observation` loop – a domináns agent architektúra alapja.

## A loop lépései

| Lépés | Leírás |
|-------|--------|
| **Perceive** | Input fogadása (user üzenet, tool eredmény, memória) |
| **Think** | Reasoning a következő lépésről |
| **Act** | Tool hívás vagy válasz generálás |
| **Observe** | Tool eredmény befogadása |
| **Loop/Stop** | Ismétlés vagy megállás ha cél teljesült |

## Ismert problémák

- Uninformatív tool eredmény → végtelen loop
- Hosszú taskok → context overflow
- **Megoldás:** Early stopping, dynamic re-planning, hierarchikus memória ([[memory-types]])

## Evolúció

```
Egyszerű Prompt
  ↓ + tool hívás
Tool-calling LLM
  ↓ + reasoning loop
ReAct Agent
  ↓ + specializáció + koordináció
Multi-Agent System ([[multi-agent-patterns]])
  ↓ + protokoll interop
Agent Network ([[mcp-protocol]] + [[a2a-protocol]])
```
