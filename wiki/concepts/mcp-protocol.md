---
title: "Model Context Protocol (MCP)"
type: concept
sources: [raw/initial-research/03_state_of_the_art.md]
related: [concepts/a2a-protocol, concepts/tool-use, entities/microsoft-agent-framework]
created: 2026-04-07
updated: 2026-04-07
coverage: medium
confidence: high
---

# Model Context Protocol (MCP)

## Mi ez?

Nyílt protokoll az LLM alkalmazások és külső eszközök/adatforrások integrációjához. "USB szabvány az AI tool-oknak" – egységes csatlakozó bármilyen integrációhoz.

## Idővonal

| Dátum | Esemény |
|-------|---------|
| 2024. november | Anthropic bejelenti |
| 2025. március | OpenAI adoptatálja |
| 2025. április | Google DeepMind megerősíti |
| 2025. november | Spec v25-11-25 |
| 2025. december | Agentic AI Foundation (Linux Foundation) |

## Architektúra

```
LLM Application (MCP Client)
        ↕ MCP Protocol
MCP Server (adatforrás/eszköz)
```

Egy MCP server-t egyszer kell megírni → bármely MCP-kompatibilis LLM használhatja.

## 2025-ös spec újítások

- Aszinkron műveletek
- Statelessness design
- Server identity
- Official extensions

## Kapcsolódó

Az [[a2a-protocol]] az agent-agent kommunikációt szabványosítja – MCP kiegészítője, nem konkurense.
