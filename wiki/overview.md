---
title: "LLM Agent Wiki – Áttekintés"
type: overview
sources: [raw/initial-research/01_alapfogalmak.md, raw/initial-research/02_framework_osszehasonlitas.md, raw/initial-research/03_state_of_the_art.md, raw/initial-research/04_karpathy.md]
related: [index, concepts/llm-wiki-pattern, entities/karpathy]
created: 2026-04-07
updated: 2026-04-07
coverage: medium
confidence: medium
---

# LLM Agent Wiki – Áttekintés

Ez a wiki az LLM Agent technológia teljes képét adja – a kiinduló állapottól a legfejlettebb multi-agent rendszerekig.

## A nagy kép

Andrej Karpathy szerint **"2025-2035 a agensek évtizede"**. Az LLM-ek operációs rendszerekké válnak, a szoftver fejlesztés paradigmája eltolódik az explicit algoritmusok (Software 1.0) és a neurális hálók (Software 2.0) után a természetes nyelvű specifikáció felé ([[karpathy]] – Software 3.0).

## Evolúció egy mondatban

```
Prompt → Tool Use → ReAct Loop → Single Agent → Multi-Agent → Agent Networks
```

Részletek: [[agent-loop]], [[tool-use]], [[planning-strategies]]

## Protokoll réteg (2025-2026)

Két szabvány stabilizálódik:
- [[mcp-protocol]] – LLM ↔ Eszköz/Adatforrás (Anthropic → Linux Foundation)
- [[a2a-protocol]] – Agent ↔ Agent (Google → Linux Foundation, 50+ cég)

## Framework táj

9 aktív framework versenyez, különböző niche-ekkel. Részletes összehasonlítás: [[framework-comparison]].

.NET/Java kompatibilis egyetlen opció: [[microsoft-agent-framework]].

## Ez a wiki

Ez a wiki maga is a [[llm-wiki-pattern]] szerint épül fel – Karpathy "idea file" architektúrája alapján.
