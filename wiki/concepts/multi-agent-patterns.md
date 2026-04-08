---
title: "Multi-Agent Orchestration Patterns"
type: concept
sources: [raw/initial-research/03_state_of_the_art.md]
related: [concepts/a2a-protocol, concepts/agent-loop, entities/langgraph, entities/crewai]
created: 2026-04-07
updated: 2026-04-07
coverage: medium
confidence: high
---

# Multi-Agent Orchestration Patterns

## Piaci kontextus

Gartner (2025): 1445%-os növekedés multi-agent rendszer kérdésekben (Q1 2024 → Q2 2025).
Teljesítmény előny: 45%-kal gyorsabb, 60%-kal pontosabb vs. single-agent.

## 4 fő minta

### Supervisor
```
[Orchestrator] → [Worker A], [Worker B], [Worker C]
```
Egyszerű, átlátható. Bottleneck az orchestratornál.

### Hierarchical
```
[Strategy] → [Team Lead A] → [Worker 1], [Worker 2]
           → [Team Lead B] → [Worker 3], [Worker 4]
```
Skálázható, strukturált. Komplexebb.

### Adaptive Network
```
[Agent A] ↔ [Agent B] ↔ [Agent C]
```
Decentralizált, rugalmas. Nehezebb debuggolni.

### Custom
Programmatikus rugalmasság specifikus igényekhez.

## Framework implementációk

- [[langgraph]] – state-based, Supervisor/Hierarchical
- [[crewai]] – role-based, Supervisor metafora
- [[microsoft-agent-framework]] – enterprise Hierarchical
