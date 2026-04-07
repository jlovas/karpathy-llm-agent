---
title: "Agentic RAG"
type: concept
sources: [raw/initial-research/03_state_of_the_art.md]
related: [concepts/memory-types, concepts/llm-wiki-pattern, comparisons/rag-vs-llm-wiki]
created: 2026-04-07
updated: 2026-04-07
coverage: medium
confidence: medium
---

# Agentic RAG

## RAG vs Agentic RAG

| | Hagyományos RAG | Agentic RAG |
|-|-----------------|-------------|
| Retrieval | Statikus pipeline | Agent dönti el |
| Query | Egyszer | Iteratív |
| Forrás | Egy | Több, dinamikus |
| Workflow | Rögzített | Multi-step |

## Integráció minták

1. **Retrieval Planning** – agent dönti el mit, mikor, honnan
2. **Iterative Retrieval** – query finomítás observation után
3. **Multi-Source Orchestration** – választ több forrás között
4. **Grounded Generation** – output retrieved kontextusra alapozva

## LlamaIndex 2025: "RAG is dead, long live agentic retrieval"

A statikus RAG pipelines-t felváltják az agent-vezérelt, dinamikus retrieval rendszerek.

## Kapcsolódó

Az [[llm-wiki-pattern]] egy speciális megközelítés: a tudás kompilált formában él a wiki-ben, nem nyers dokumentumokban.
