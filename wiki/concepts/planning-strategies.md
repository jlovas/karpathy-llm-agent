---
title: "Planning Strategies"
type: concept
sources: [raw/initial-research/01_alapfogalmak.md]
related: [concepts/agent-loop]
created: 2026-04-07
updated: 2026-04-07
coverage: medium
confidence: high
---

# Planning Strategies

## Összehasonlítás

| Stratégia | Komplexitás | Backtrack? | Mikor érdemes |
|-----------|-------------|------------|---------------|
| **CoT** | Alacsony | Nem | Egyszerű lépéses feladatok |
| **ReAct** | Közepes | Nem | Tool use + reasoning keverék |
| **ToT** | Magas | Igen | Több lehetséges útvonal |
| **GoT** | Nagyon magas | Igen | Non-hierarchikus reasoning |
| **MRKL** | Magas | Nem | Specializált expert modulok |

## Részletek

**Chain of Thought (CoT):** Lépésenkénti köztes reasoning. Koherens language sequence cselekvés előtt.

**Tree of Thoughts (ToT):** Párhuzamos reasoning ágak DFS/BFS/beam search-el. Backtracking ha egy ág zsákutca.

**Graph of Thoughts (GoT):** ToT kiterjesztése gráf struktúrával – nem-hierarchikus relációkhoz.

**MRKL:** LLM + specializált expert modulok (szimbolikus eszközök vagy kisebb LLM-ek). Minden expert saját domain-jéért felel.

**Dynamic Planning:** Adaptív test-time compute – hosszú taskoknál dönt mikor tervezzen vs hajtson végre.
