---
title: "Framework összehasonlítás"
type: comparison
sources: [raw/initial-research/02_framework_osszehasonlitas.md]
related: [entities/langgraph, entities/crewai, entities/openai-agents-sdk, entities/google-adk, entities/pydantic-ai, entities/smolagents, entities/llamaindex, entities/haystack, entities/microsoft-agent-framework]
created: 2026-04-07
updated: 2026-04-07
coverage: medium
confidence: high
---

# Framework összehasonlítás (2026)

## Összefoglaló táblázat

| Framework | Típus | Legjobb | Nyelv |
|-----------|-------|---------|-------|
| [[langgraph\|LangGraph]] | State-based | Production durability | Python |
| [[crewai\|CrewAI]] | Role-based | Gyors prototípus | Python |
| [[openai-agents-sdk\|OpenAI SDK]] | Minimalist | Provider flexibilitás | Python, TS |
| [[google-adk\|Google ADK]] | Code-first | Google Cloud | Python, TS, Go |
| [[pydantic-ai\|Pydantic AI]] | Type-safe | Type safety | Python |
| [[smolagents\|Smolagents]] | Code-based | Minimal, OSS | Python |
| [[llamaindex\|LlamaIndex]] | RAG-fókusz | Dokumentumok | Python, TS |
| [[haystack\|Haystack]] | Enterprise | Enterprise | Python |
| [[microsoft-agent-framework\|MS Agent FW]] | Enterprise | .NET ökoszisztéma | Python, .NET |

## Döntési fa

```
.NET / Java-kompatibilitás kell?
  → IGEN: Microsoft Agent Framework

Python, gyors prototípus?
  → Role-based csapat metafora: CrewAI
  → Code-first, minimális: Smolagents

Production, durability kritikus?
  → Komplex workflow: LangGraph
  → Enterprise pipeline: Haystack

RAG-heavy?
  → LlamaIndex

Type safety prioritás?
  → Pydantic AI

Provider flexibilitás / OpenAI tooling?
  → OpenAI Agents SDK

Google Cloud + streaming?
  → Google ADK
```
