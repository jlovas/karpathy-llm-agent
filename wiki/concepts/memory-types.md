---
title: "Memory Types"
type: concept
sources: [raw/initial-research/01_alapfogalmak.md]
related: [concepts/agent-loop, concepts/agentic-rag]
created: 2026-04-07
updated: 2026-04-07
coverage: medium
confidence: high
---

# Memory Types

## Négy fő típus

### In-Context Memory
A jelenlegi context window. Gyors, de korlátozott (pl. 128k token). Dinamikusan kezelt summarizálással.

### External Memory

| Altípus | Leírás | Tárolás |
|---------|--------|---------|
| **Core Memory** | Kritikus kontextus blokkok (user prefs, task state) | In-context, agent kezeli |
| **Recall Memory** | Teljes interakció-história, kereshető | Disk |
| **Archival Memory** | Explicit tudásbázis | Vector DB / Graph DB / KV |

### Episodic Memory
Konkrét események és kontextusaik. Hasonló szituációban visszakereshető.

### Semantic Memory
Strukturált tudás fogalmakról és relációkról. Knowledge graph-ban tipikusan.

## Tárolási megoldások

| Megoldás | Példák | Előny | Hátrány |
|----------|--------|-------|---------|
| Vector Store | Pinecone, Weaviate | Szemantikus keresés | Komplex, drága |
| KV Store | Redis, MongoDB | Gyors, egyszerű | Korlátozott query |
| Knowledge Graph | Neo4J, Cognee | Relációk, determinisztikus | Erőforrás-igényes |

**Ajánlás (2025-2026):** Knowledge graph + vector store kombináció agentic RAG-hoz.
