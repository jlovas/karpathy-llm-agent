---
title: "Tool Use / Function Calling"
type: concept
sources: [raw/initial-research/01_alapfogalmak.md]
related: [concepts/agent-loop, concepts/mcp-protocol]
created: 2026-04-07
updated: 2026-04-07
coverage: medium
confidence: high
---

# Tool Use / Function Calling

## Hogyan működik

1. System prompt leírja az elérhető eszközöket
2. LLM strukturált JSON tool call-t generál (function name + arguments)
3. Tool sandbox-ban végrehajtódik
4. Eredmény visszakerül az LLM kontextusába

## Best practices (2026)

- **Egyértelmű nevek** – az LLM a leírás alapján dönt
- **Természetes argumentumok** – ne UUID-k, hanem olvasható értékek
- **Sandbox execution** – izoláltan fusson minden hívás
- **Validáció** – bemenetek ellenőrzése (reject/fix/escalate szabályok)
- **Tool Search** (Anthropic, 2025) – ezres nagyságrendű tool context overhead nélkül
- **Programmatic Tool Calling** – code environment-ben való végrehajtáshoz

## Kapcsolódó protokoll

Az [[mcp-protocol]] szabványosítja a tool/data integráció csatlakozóját – "USB szabvány az AI tool-oknak".
