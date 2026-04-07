# 3. State of the Art (2025-2026)

---

## Model Context Protocol (MCP)

**Bejelentés:** 2024. november – Anthropic
**Státusz:** Iparági standard, Linux Foundation-höz átadva (2025. december)

### Mi az MCP?
Nyílt protokoll az LLM alkalmazások és külső adatforrások/eszközök zökkenőmentes integrációjához. Gondolj rá úgy, mint egy **USB szabványra az AI tool-ok számára** – egységes csatlakozó, akármi csatlakozzon.

### Történet

| Dátum | Esemény |
|-------|---------|
| 2024. november | Anthropic bejelenti az MCP-t |
| 2025. március | OpenAI hivatalosan adoptatálja |
| 2025. április | Google DeepMind megerősíti Gemini támogatást |
| 2025. november | Spec v25-11-25 – major fejlesztések |
| 2025. december | Anthropic átadja az Agentic AI Foundation-nek (AAIF) |

### 2025-ös spec újítások (v25-11-25)
- Aszinkron műveletek
- Statelessness design
- Server identity
- Official extensions

### Adopció
- Claude: 75+ connector a directory-ban
- **Tool Search** képesség: ezres nagyságrendű tool kezelése context overhead nélkül
- **Programmatic Tool Calling**: code environment-ben való végrehajtáshoz

### Hogyan működik?

```
LLM Application (MCP Client)
        ↕ MCP Protocol
MCP Server (adatforrás/eszköz)
   ├── Fájlrendszer
   ├── Adatbázis
   ├── API
   └── ...
```

### Miért fontos?
Egy MCP server-t egyszer kell megírni, aztán **bármely MCP-kompatibilis LLM** használhatja. Ez megszünteti a framework-specifikus integrációk szükségességét.

---

## Agent2Agent (A2A) Protokoll

**Bejelentés:** 2025. április 9. – Google
**Státusz:** Nyílt standard, v0.3, Linux Foundation
**Ipari támogatás:** 50+ cég (Atlassian, Box, Cohere, Intuit, LangChain, MongoDB, PayPal, Salesforce, SAP, ServiceNow, Workday)

### Mi az A2A?
Az A2A az **agent-ek közötti kommunikáció szabványa** – az MCP kiegészítője, nem konkurense.

| Protokoll | Mire való |
|-----------|-----------|
| **MCP** | LLM ↔ Eszköz/Adatforrás kommunikáció |
| **A2A** | Agent ↔ Agent kommunikáció |

### 3 core képesség

**1. Agent Card** – JSON formátum az agent képességeinek hirdetéséhez
```json
{
  "name": "ResearchAgent",
  "capabilities": ["web_search", "document_analysis"],
  "input_schema": {...},
  "output_schema": {...}
}
```
Kliens agent-ek ezek alapján választják ki a megfelelő remote agent-et.

**2. Task Object** – Task lifecycle management
- Azonnali vagy hosszú futású task-ok
- Agent-ek státusz update-eket kommunikálnak

**3. Message Communication** – Kontextus, válaszok, artifact-ok megosztása

### Technikai implementáció
- **HTTP, JSON-RPC, Server-Sent Events (SSE)**
- ISO 8601 timestamp-ek
- Enterprise biztonsági és compliance guardrail-ek

### Hatás
Framework- és vendor-agnosztikus agent együttműködés. Egy LangGraph agent tud kommunikálni egy CrewAI agent-tel, ha mindkettő A2A-t használ.

---

## Multi-Agent Orchestration minták

**Piaci növekedés (Gartner, 2025):** 1445%-os növekedés a multi-agent rendszer kérdésekben (Q1 2024 → Q2 2025)

### 4 fő orchestráció minta

#### 1. Supervisor Pattern
Centralizált irányítás: egyetlen orchestrator irányít worker agent-eket.

```
[Orchestrator]
  ├─ [Worker A]
  ├─ [Worker B]
  └─ [Worker C]
```
**Előny:** Egyszerű, átlátható
**Hátrány:** Bottleneck az orchestrator-nál

#### 2. Hierarchical Pattern
Szintezett struktúra: magasabb szintű agent-ek koordinálnak, alacsonyabb szintűek végrehajtanak.

```
[Strategy Agent]
  ├─ [Team Lead A]
  │    ├─ [Worker 1]
  │    └─ [Worker 2]
  └─ [Team Lead B]
       ├─ [Worker 3]
       └─ [Worker 4]
```
**Előny:** Skálázható, jól strukturált
**Hátrány:** Komplexitás és overhead

#### 3. Adaptive Network Pattern
Decentralizált együttműködés: agent-ek önállóan döntenek az együttműködésről.

```
[Agent A] ←──→ [Agent B]
    ↑                ↑
    └────→ [Agent C] ┘
```
**Előny:** Rugalmas, robosztus
**Hátrány:** Nehezebb debuggolni

#### 4. Custom Pattern
Programmatikus rugalmasság specifikus orchestráció igényekhez.

### Kommunikációs protokollok (4 major)
1. **MCP** (Anthropic) – LLM-eszköz integráció
2. **ACP** – Agent Communication Protocol (emerging)
3. **A2A** (Google-backed, 50+ cég) – agent-agent kommunikáció
4. **ANP** (Google Cloud) – Agent Network Protocol

---

## Long-Running Agents és Agentic Workflows

### A kihívás
Hosszú horizon-ú task-oknál az agent-nek:
- Sok lépésen át kell megőrizni a kontextust
- Kezeli a context overflow-t
- Visszatér a helyes irányba ha eltéved
- Perzisztálni kell state-et (crash recovery)

### Agentic RAG rendszerek
Hagyományos RAG vs. Agentic RAG:

| | Hagyományos RAG | Agentic RAG |
|-|-----------------|-------------|
| Retrieval | Statikus pipeline | Agent dönti el mikor és hogyan |
| Query | Egyszer | Iteratív, finomítható |
| Forrás | Egy | Több, dinamikus |
| Workflow | Rögzített | Komplex, multi-step |

### Memory management long-running agent-eknél

```
Short-Term Memory (STM)
└── Jelenlegi context window

Long-Term Memory (LTM)
├── Recall: Teljes história, kereshető
├── Archival: Persistent knowledge base
└── Core: Kritikus kontextus blokkok
```

**Tárolási megoldások:**

| Megoldás | Példa | Mire jó |
|----------|-------|---------|
| Vector Store | Pinecone, Weaviate | Unstrukturált, szemantikus keresés |
| KV Store | Redis, MongoDB | Gyors, egyszerű lookup |
| Knowledge Graph | Neo4J, Cognee, DGraph | Relációk, determinisztikus navigáció |

**Ajánlás:** Knowledge graph + vector store kombináció agentic RAG-hoz.

### Letta 2025 innovációk
- Dinamikus memory block management (Claude Sonnet memory tools-szal)
- Letta Filesystem dokumentum organizáláshoz
- Multi-tier memory kompozíció (core + message + recall + archival)
- Benchmark: Szofisztikált memory kompozíció >> egyszerű megközelítések

### Best practices

1. **Summarizálás és context rewriting** a context kezeléshez
2. **Retrieval-augmented memory** kompozíció
3. **Teljes state perzisztálás** adatbázisba (memória, reasoning, tool call-ok)
4. **Core memories** stratégiai injektálása a context window-ba
5. **Early stopping** mechanizmus a végtelen loop-ok elkerülésére

---

## RAG evolúció: "RAG is dead, long live agentic retrieval"

*(LlamaIndex, 2025)*

### Hagyományos RAG problémái
- Statikus pipeline – nem tud alkalmazkodni
- Egyszeri retrieval – nem iterál
- Nincs reasoning a retrieval stratégia felett

### Agentic retrieval integráció minták

**1. Retrieval Planning**
Agent dönti el mit, mikor és honnan kérdezzen le.

**2. Iterative Retrieval**
Agent finomítja a query-ket az observation-ök alapján.

**3. Multi-Source Orchestration**
Agent választ több tudásforrás közül.

**4. Grounded Generation**
Agent a retrieved kontextusra alapozza az outputot.

---

## Trendek és predikciók (2026)

| Trend | Részletek |
|-------|-----------|
| **Protokoll konvergencia** | MCP és A2A univerzális standard lesz agent interoperabilitáshoz |
| **Memory management** | Long-running agent-ek multi-tier memory rendszereket igényelnek |
| **Framework konszolidáció** | Microsoft, Google, OpenAI enterprise standard-ok lesznek |
| **Code-first filozofia** | Smolagents code-based approach nyer teret JSON felett |
| **Agent-optimized design** | Fejlesztők agent-fogyasztásra is terveznek (nem csak emberre) |
| **Production readiness** | 2026 fókusz: observability, durability, cost optimizálás |
| **Multi-agent adopció** | Gartner 1445%-os növekedés → éles production deployment-ek |
