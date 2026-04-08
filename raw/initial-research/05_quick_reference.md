# 5. Quick Reference

---

## Framework döntési fa

```
Mit szeretnél csinálni?
│
├─ .NET / Java-kompatibilitás kell?
│    └─ IGEN → Microsoft Agent Framework (GA Q1 2026)
│
├─ Gyors prototípus, minimális setup?
│    ├─ Role-based csapatmetafora → CrewAI
│    └─ Code-first, minimalist → Smolagents
│
├─ Production, magas durability?
│    ├─ Komplex workflow, fine-grained kontroll → LangGraph
│    └─ Enterprise, explicit pipeline kontroll → Haystack
│
├─ RAG-heavy alkalmazás?
│    └─ LlamaIndex
│
├─ Type safety + observability?
│    └─ Pydantic AI
│
├─ Provider flexibilitás + OpenAI tooling?
│    └─ OpenAI Agents SDK
│
└─ Google Cloud + streaming?
     └─ Google ADK
```

---

## Framework összefoglaló

| Framework | Típus | Legjobb | Nyelv | Státusz |
|-----------|-------|---------|-------|---------|
| **LangGraph** | State-based | Production durability | Python | Érett |
| **CrewAI** | Role-based | Gyors prototípus | Python | Aktív |
| **OpenAI SDK** | Minimalist | Provider flex | Python, TS | Érett |
| **Google ADK** | Code-first | Google Cloud | Python, TS, Go | Érett |
| **Pydantic AI** | Type-safe | Type safety | Python | Érett |
| **Smolagents** | Code-based | Minimal, OSS | Python | Növekvő |
| **LlamaIndex** | RAG-fókusz | Dokumentumok | Python, TS | Érett |
| **Haystack** | Enterprise | Enterprise | Python | Érett |
| **MS Agent FW** | Enterprise | .NET ökoszisztéma | Python, .NET | RC→GA |

---

## Agent evolúció

```
Prompt
  ↓ + Tool use
Tool-calling LLM
  ↓ + Reasoning loop
ReAct Agent
  ↓ + Specializáció + koordináció
Multi-Agent System
  ↓ + Protokoll-szintű interop
Agent Network (MCP + A2A)
```

---

## Kulcsprotokolok

| Protokoll | Ki fejleszti | Mire való | Státusz |
|-----------|-------------|-----------|---------|
| **MCP** | Anthropic → Linux Foundation | LLM ↔ Tool/Data | Iparági standard |
| **A2A** | Google → Linux Foundation | Agent ↔ Agent | v0.3, 50+ cég |
| **ACP** | Közösségi | Agent ↔ Agent | Emerging |
| **ANP** | Google Cloud | Agent hálózatok | Korai |

---

## Memory típusok gyorsan

| Típus | Hol tárolódik | Mire jó |
|-------|---------------|---------|
| **In-Context** | Context window | Aktív feladat, jelenlegi conversáció |
| **Core Memory** | Context window (managed) | Kritikus user/task info |
| **Recall Memory** | Disk | Teljes história, kereshető |
| **Archival Memory** | DB (vector/graph/KV) | Tudásbázis |
| **Episodic** | DB | Konkrét események |
| **Semantic** | Knowledge graph | Fogalmak, relációk |

---

## Planning stratégiák összehasonlítása

| Stratégia | Komplexitás | Backtrack? | Mikor érdemes |
|-----------|-------------|------------|---------------|
| **CoT** | Alacsony | Nem | Egyszerű lépéses feladatok |
| **ReAct** | Közepes | Nem | Tool use + reasoning keverék |
| **ToT** | Magas | Igen | Komplex, több lehetséges útvonal |
| **GoT** | Nagyon magas | Igen | Non-hierarchikus reasoning |
| **MRKL** | Magas | Nem | Specializált expert modulok |

---

## Multi-agent orchestráció minták

| Minta | Struktúra | Mikor |
|-------|-----------|-------|
| **Supervisor** | 1 orchestrator → N worker | Egyszerű, átlátható feladatok |
| **Hierarchical** | Szintezett csapatok | Skálázható, strukturált projektek |
| **Adaptive Network** | Decentralizált | Rugalmas, dinamikus problémák |
| **Custom** | Bármilyen | Specifikus igények |

---

## Kulcsdátumok (idővonal)

```
2022 ─── ReAct paper (Yao et al.)
2023 ─── LangChain érett, CrewAI megjelenik
         GPT-4 function calling
2024 ─── Anthropic bejelenti MCP-t (nov.)
2025 ─── OpenAI Agents SDK (márc.)
         Google ADK + A2A protokoll (ápr.)
         Smolagents 26k+ star
         MS Agent Framework RC (okt.)
         MCP → Linux Foundation (dec.)
2026 ─── MS Agent Framework GA (Q1)
         A2A v0.3 ipari standard
         MCP ökoszisztéma 75+ connector
```

---

## Fogalomszótár

| Fogalom | Magyar magyarázat |
|---------|------------------|
| **Agent** | Autonóm LLM-alapú rendszer, amely célt követ |
| **Orchestrator** | Más agent-eket koordináló, felsőbb szintű agent |
| **Tool / Function call** | Külső rendszer hívása az LLM által |
| **ReAct** | Thought→Action→Observation loop |
| **RAG** | Retrieval-Augmented Generation – keresés + generálás |
| **Agentic RAG** | Agent által vezérelt, dinamikus RAG |
| **MCP** | Model Context Protocol – tool/data csatlakozó szabvány |
| **A2A** | Agent2Agent – agent-agent kommunikáció protokoll |
| **Guardrail** | Input/output validáció, biztonsági réteg |
| **Handoff** | Agent-ek közötti feladat átadás |
| **Context window** | Az LLM "rövid memóriája" (pl. 128k token) |
| **Embedding** | Szöveg vektoros reprezentációja (RAG alapja) |
| **Vector store** | Embedding-ek tárolója és keresője |
| **Knowledge graph** | Strukturált relációs tudásbázis |

---

## Hasznos linkek

| Link | Tartalom |
|------|---------|
| https://modelcontextprotocol.io | MCP specifikáció |
| https://a2a-protocol.org | A2A protokoll |
| https://docs.anthropic.com | Claude / MCP docs |
| https://github.com/huggingface/smolagents | Smolagents |
| https://github.com/openai/openai-agents-python | OpenAI Agents SDK |
| https://google.github.io/adk-docs/ | Google ADK docs |
| https://ai.pydantic.dev | Pydantic AI |
| https://docs.crewai.com | CrewAI docs |
| https://langchain-ai.github.io/langgraph/ | LangGraph docs |
| https://karpathy.ai | Karpathy blog |
