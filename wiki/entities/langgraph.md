---
title: "LangChain / LangGraph"
type: entity
sources: [raw/initial-research/02_framework_osszehasonlitas.md]
related: [comparisons/framework-comparison, concepts/multi-agent-patterns]
created: 2026-04-07
updated: 2026-04-07
coverage: medium
confidence: high
---

# LangChain / LangGraph

**Státusz:** Iparági standard (47M+ PyPI letöltés) | **Nyelv:** Python

## Mikor érdemes

Production rendszerek ahol a durability és state management kritikus. Komplex workflow-k precíz kontrollal.

## Architektúra

- **LangChain** – building blocks (model wrappers, prompt templates, chains)
- **LangGraph** – state-based agent orchestráció; minden agent egy centrális state objektumból olvas/ír

## Előny / Hátrány

✓ Production-grade megbízhatóság, 100+ integráció, state persistence
✗ Meredek tanulási görbe
