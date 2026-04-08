# 2. Framework összehasonlítás (2026)

> 9 framework részletes bemutatása. Mindegyiknél: architektúra, feature-ök, mikor érdemes használni, nyelv, aktuális státusz.

---

## LangChain / LangGraph

**Státusz:** Iparági standard, 47M+ PyPI letöltés
**Nyelv:** Python
**Verzió:** v0.1+ (folyamatosan frissül)

### Architektúra
- **LangChain**: alap framework – building blocks (model wrappers, prompt templates, chains)
- **LangGraph**: state-alapú agent orchestráció
  - Minden agent egy **centrális state objektumból** olvas és ír
  - Reducer logika kezeli a konkurens frissítéseket
  - Gráf-alapú végrehajtás: pontosan definiált branching és loop-ok

### Főbb feature-ök
- State persistence és recovery (durability)
- 100+ integráció (tool-ok, service-ek)
- Production-grade megbízhatóság
- Komplex workflow-k precíz kontrollal

### Mikor érdemes használni
- Production rendszerek, ahol a durability kritikus
- Komplex workflow-k, ahol az irányíthatóság fontos
- Ha már LangChain ökoszisztémában vagy

### Hátrány
- Viszonylag meredek tanulási görbe
- A "LangChain == bonyolult" reputáció részben megalapozott (de LangGraph ezt javítja)

---

## CrewAI

**Státusz:** Leggyorsabban növekvő multi-agent framework
**Nyelv:** Python
**Megjelenés:** 2023+

### Architektúra
- **Role-based agent modeling** – emberi csapatstruktúrát imitál
- Agenteket "crew"-kba szervezi: minden agentnek van **role, goal, backstory**
- Intuitív team metafora fejlesztőknek és stakeholder-eknek

### Főbb feature-ök
- Egyszerű, intuitív agent team kompozíció
- Beépített role management és task delegation
- Gyors prototípus-készítés
- Lean codebase, modern design

### Mikor érdemes használni
- Gyors prototípus multi-agent rendszerekhez
- Ha az emberi csapatstruktúra jól leképezhető agentekre
- Ha a developer intuition fontosabb a fine-grained kontrollnál

### Hátrány
- Magasabb cost: 5 agent ~5x drágább mint 1 LangChain agent
- Kevésbé alkalmas komplex orchestration logikára

---

## OpenAI Agents SDK

**Státusz:** Production-ready, megjelent: 2025. március
**Nyelv:** Python, TypeScript
**Előd:** Experimental Swarm projekt

### Architektúra
**4 core primitív:**

| Primitív | Leírás |
|----------|--------|
| **Agents** | Utasítások, eszközök, control flow |
| **Handoffs** | Explicit delegálás agent-ek között |
| **Guardrails** | Input/output validáció |
| **Tracing** | Beépített vizualizáció és debugging |

### Főbb feature-ök
- Provider-agnostikus (Anthropic, Google, DeepSeek, Llama, stb.)
- Lightweight, open-source
- MCP integráció
- TypeScript támogatás (2025)
- Integráció az OpenAI ökoszisztémával (evaluations, fine-tuning, distillation)

### Mikor érdemes használni
- Minimális, érthető agent implementáció
- Ha provider flexibilitás kell
- Ha az OpenAI tooling ökoszisztémát akarod kihasználni

### Hátrány
- OpenAI-centrikus naming és design, bár provider-agnostikus

---

## Google Agent Development Kit (ADK)

**Státusz:** Production-ready, megjelent: 2025. április
**Nyelv:** Python, TypeScript, Go (1.0.0)

### Architektúra
- **Code-first** Python/TypeScript framework
- Model-agnostikus, Gemini-optimalizált
- Multi-agent hierarchiák kompozícióval
- Szoftverfejlesztői workflow-érzet

### Főbb feature-ök
- Gazdag model támogatás (Gemini, Vertex AI Model Garden, LiteLLM)
- Tool ökoszisztéma (Search, Code Execution, MCP, LangChain, LlamaIndex integráció)
- Bidirectional audio és video streaming
- OpenTelemetry integráció
- Self-healing logic plugin-okon keresztül

### Mikor érdemes használni
- Google Cloud ökoszisztémában
- Ha fejlett streaming képességek kellenek
- Ha a szoftverfejlesztői metafora közel áll hozzád

### Hátrány
- Google-ekoszisztéma lock-in érzés (bár model-agnostikus)

---

## Pydantic AI

**Státusz:** Production-ready, type-safe Python framework
**Nyelv:** Python

### Architektúra
- **Type-safe** agent building – validáció íráskor, ne futáskor
- Comprehensive model support
- Szoros observability integráció

### Főbb feature-ök
- Minden major model provider (OpenAI, Anthropic, Gemini, DeepSeek, Grok, Cohere, Mistral, Perplexity, ...)
- Type-safe agent definíció IDE supporttal
- Strukturált output validáció
- Pydantic Logfire mély integráció (observability)
- Composable capabilities (tool-ok, hook-ok, utasítások bundling-je)
- Behavior tracing és cost tracking

### Mikor érdemes használni
- Ha a type safety prioritás Python-ban
- Ha comprehensive observability kell
- Ha már Pydantic ökoszisztémában vagy (FastAPI projekt, stb.)

### Filozofia
"FastAPI érzés" GenAI app fejlesztéshez – ha FastAPI-t szeretsz, ez a te frameworköd.

---

## Smolagents (HuggingFace)

**Státusz:** Gyorsan növekvő, megjelent: 2025, 26k+ GitHub star
**Nyelv:** Python

### Architektúra
- **Minimalist, code-first** megközelítés (agents.py < 1000 sor!)
- **JSON function calls helyett Python kódot generál** az agent
- Model-agnostikus

### Agent típusok

| Típus | Leírás |
|-------|--------|
| **CodeAgent** | Python kód snippetek mint akciók |
| **ToolCallingAgent** | Klasszikus tool-calling megközelítés |

### Főbb feature-ök
- 3 sor kód a kezdéshez
- Sandbox execution (Blaxel, E2B, Modal, Docker, Pyodide+Deno)
- Model-agnostikus (local transformers, Hub modellek, OpenAI, Anthropic, LiteLLM)
- Tool/agent megosztás a HuggingFace Hub-on
- Multimodal (vision, video, audio)

### Mikor érdemes használni
- Minimális setup, gyors iteráció
- Ha a code-based action filozofia vonzó
- Open source modellek kipróbálásához

### Filozofia
"A programozási nyelvek jobb kifejező eszközök a számítógépes viselkedéshez, mint a JSON" – ezért generál kódot a JSON helyett.

### Növekedés
2025-ben 3 000-ről 26 000+ star-ra nőtt a GitHub-on.

---

## LlamaIndex (Agent Capabilities)

**Státusz:** Production-ready, erős RAG + agent integráció
**Nyelv:** Python, TypeScript

### Architektúra
- **Workflows 1.0**: Lightweight multi-step agentic alkalmazásokhoz
- Agent Workflows multi-step orchestrációval
- Erős RAG + agent integráció

### Főbb feature-ök
- **Agentic Document Workflows (ADW)**: tudás-munka automatizáláshoz
- Document agents perzisztens state management-tel
- Agent templates (számla feldolgozás, szerződés review, igény kezelés)
- Day-zero support új modellekhez (GPT-5, Claude Opus)
- Mély integráció retrieval-lel és indexeléssel

### 2025-ös újítások
- **LlamaAgents**: one-click document agent deployment
- LlamaSplit, LlamaSheets

### Mikor érdemes használni
- Ha heterogén adatforrásokon alapuló retrieval kell
- Dokumentum feldolgozás és tudás-munka automatizálása
- Ha a RAG fontosabb mint a pure agentic reasoning

---

## Haystack (deepset)

**Státusz:** Production-ready enterprise framework
**Nyelv:** Python
**Aktuális verzió:** 2.25.2 (2026. március 5.)

### Architektúra
- Moduláris pipeline és agent workflow-k
- Universal Agent komponens chat-alapú LLM-ekhez
- Explicit kontroll: retrieval, routing, memory, generálás

### Főbb feature-ök
- Enterprise ügyfelek: Airbus, The Economist, NVIDIA, Comcast
- Agent resumption snapshot-okból, debuggingal
- SearchableToolset – csökkenti a context használatot
- Jinja2 templates agent-ekhez
- Folyamatos frissítések

### Mikor érdemes használni
- Enterprise deployment, ahol a production durability kritikus
- Ha explicit kontroll kell a pipeline komponensek felett
- Komplex retrieval és routing

### Hátrány
- Magasabb komplexitás

---

## Microsoft Agent Framework (Semantic Kernel utód)

**Státusz:** RC 2025. október, GA Q1 2026
**Nyelv:** Python, .NET (C#) – **Java-barát!**

### Háttér
A Microsoft konvergálta az **AutoGen**-t és a **Semantic Kernel**-t egységes Microsoft Agent Framework-be.

| Framework | Státusz |
|-----------|---------|
| AutoGen | Maintenance mode |
| Semantic Kernel | Maintenance mode |
| **Microsoft Agent Framework** | **Aktív fejlesztés, ez a jövő** |

### Menetrend
- **RC:** 2025. október
- **GA (.NET + Python):** Q1 2026
- **Process Framework GA:** Q2 2026

### Architektúra
- Enterprise-grade multi-agent orchestráció
- Multi-provider model support (OpenAI, Anthropic, Gemini, local modellek)
- Cross-runtime interoperabilitás A2A és MCP protokollokon
- Unified interface a korábbi fragmentáció helyett

### Főbb feature-ök
- Production-ready agent kompozíció
- **.NET és Python támogatás** (Java fejlesztőknek .NET a belépési pont)
- MCP protokoll integráció
- A2A protokoll support

### Mikor érdemes használni
- Microsoft / Azure ökoszisztémában
- .NET stack esetén (a legjobb enterprise opció)
- Ha MCP + A2A interoperabilitás kell

---

## Összefoglaló táblázat

| Framework | Típus | Legjobb | Cost | Nyelv | Státusz |
|-----------|-------|---------|------|-------|---------|
| LangGraph | State-based | Production durability | Közepes | Python | Érett |
| CrewAI | Role-based | Gyors prototípus | Alacsony-közepes | Python | Aktív |
| OpenAI SDK | Minimalist | Provider flexibilitás | Közepes | Python, TS | Érett |
| Google ADK | Code-first | Google Cloud, streaming | Közepes | Python, TS, Go | Érett |
| Pydantic AI | Type-safe | Type safety, observability | Közepes | Python | Érett |
| Smolagents | Code-based | Minimal setup, OSS | Alacsony | Python | Növekvő |
| LlamaIndex | RAG-fókusz | Dokumentum processing | Közepes | Python, TS | Érett |
| Haystack | Enterprise | Enterprise durability | Magas | Python | Érett |
| MS Agent Framework | Enterprise | Microsoft/.NET ökoszisztéma | Közepes | Python, .NET | RC→GA |

---

## Döntési fa

```
Kell .NET / Java-kompatibilitás?
  → IGEN: Microsoft Agent Framework
  → NEM:
      Gyors prototípus kell?
        → IGEN: CrewAI vagy Smolagents
        → NEM:
            Production, durability kritikus?
              → IGEN: LangGraph vagy Haystack
              → NEM:
                  RAG-heavy alkalmazás?
                    → IGEN: LlamaIndex
                    → NEM:
                        Type safety prioritás?
                          → IGEN: Pydantic AI
                          → NEM: OpenAI Agents SDK vagy Google ADK
```
