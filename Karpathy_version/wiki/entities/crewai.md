---
title: "CrewAI"
type: entity
sources: [raw/initial-research/02_framework_osszehasonlitas.md]
related: [comparisons/framework-comparison, concepts/multi-agent-patterns]
created: 2026-04-07
updated: 2026-04-07
coverage: medium
confidence: high
---

# CrewAI

**Státusz:** Leggyorsabban növekvő multi-agent framework | **Nyelv:** Python | **Megjelenés:** 2023+

## Mikor érdemes

Gyors prototípus multi-agent rendszerekhez. Ha az emberi csapatstruktúra jól leképezhető agentekre.

## Architektúra

Role-based agent modeling – minden agentnek van **role, goal, backstory**. "Crew" metafora.

## Előny / Hátrány

✓ Intuitív, gyors setup, lean codebase
✗ ~5x drágább mint single-agent, kevésbé alkalmas komplex orchestrationre
