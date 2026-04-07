---
title: "Agent2Agent Protocol (A2A)"
type: concept
sources: [raw/initial-research/03_state_of_the_art.md]
related: [concepts/mcp-protocol, concepts/multi-agent-patterns]
created: 2026-04-07
updated: 2026-04-07
coverage: medium
confidence: high
---

# Agent2Agent Protocol (A2A)

## Mi ez?

Agent-ek közötti kommunikáció nyílt szabványa. Az [[mcp-protocol]] kiegészítője:

| Protokoll | Mire való |
|-----------|-----------|
| MCP | LLM ↔ Eszköz/Adatforrás |
| **A2A** | Agent ↔ Agent |

## Alapadatok

- **Bejelentés:** 2025. április 9. – Google
- **Verzió:** v0.3
- **Governance:** Linux Foundation
- **Támogatók:** 50+ cég (Atlassian, Box, Cohere, LangChain, PayPal, Salesforce, SAP, Workday...)

## 3 core képesség

1. **Agent Card** – JSON: az agent képességeinek hirdetése
2. **Task Object** – Task lifecycle (azonnali vagy hosszú futású)
3. **Message Communication** – Kontextus, válaszok, artifact-ok megosztása

## Technikai stack

HTTP + JSON-RPC + Server-Sent Events (SSE)

## Hatás

Framework-agnosztikus agent együttműködés. Egy LangGraph agent kommunikálhat egy CrewAI agent-tel ha mindkettő A2A-t használ.
