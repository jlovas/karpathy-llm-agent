---
title: "OpenAI Agents SDK"
type: entity
sources: [raw/initial-research/02_framework_osszehasonlitas.md]
related: [comparisons/framework-comparison]
created: 2026-04-07
updated: 2026-04-07
coverage: medium
confidence: high
---

# OpenAI Agents SDK

**Státusz:** Production-ready | **Megjelent:** 2025. március | **Nyelv:** Python, TypeScript

## 4 core primitív

| Primitív | Leírás |
|----------|--------|
| Agents | Utasítások, eszközök, control flow |
| Handoffs | Explicit delegálás agent-ek között |
| Guardrails | Input/output validáció |
| Tracing | Vizualizáció és debugging |

## Mikor érdemes

Minimális, érthető implementáció. Provider flexibilitás (Anthropic, Google, DeepSeek, Llama...). OpenAI tooling ökoszisztéma kihasználása.
