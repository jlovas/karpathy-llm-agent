# 1. LLM Agent alapfogalmak és evolúció

---

## Mi az LLM Agent?

Egy LLM Agent egy autonóm rendszer, amely Large Language Model-t használ arra, hogy:
1. **Érzékelje** a környezetét (input: szöveg, tool eredmények, memória)
2. **Következtessen** róla (reasoning)
3. **Cselekvéseket hajtson végre** (tool hívások, válasz generálás)
4. **Célokat érjen el** iteratívan, megállási feltétel alapján

---

## Az evolúció fázisai

### Fázis 1: Egyszerű Prompt
Közvetlen LLM kérdés, nincs eszköz vagy reasoning loop.

```
User → LLM → Válasz
```

**Limitáció:** Nem tud valós adatokat lekérdezni, nem tud számolni, nem tud cselekedn.

---

### Fázis 2: Tool Use (Function Calling)
Az LLM strukturált JSON function call-okat generál külső rendszerek meghívásához.

```
User → LLM → [JSON tool call] → Tool execution → LLM → Válasz
```

**Hogyan működik:**
1. System prompt leírja az elérhető eszközöket
2. LLM JSON-t generál (function name + arguments)
3. Tool végrehajtódik sandbox-ban
4. Eredmény visszakerül az LLM kontextusába

**Best practices (2025):**
- Eszköznevekből legyen egyértelmű a szándék
- Argumentumok legyenek természetesek, ne opaque ID-k
- Mindig validáld és sanitizáld a tool inputokat
- Explicit hibakezelés (reject/fix/escalate szabályok)

---

### Fázis 3: ReAct (Reasoning + Acting)
**Introduced by:** Yao et al., 2022

A `Thought → Action → Observation` loop ötvözi a chain-of-thought reasoning-t a tool use-szal.

```
Task
  └─ Thought: "Meg kell néznem az időjárást"
       └─ Action: get_weather(city="Budapest")
            └─ Observation: "18°C, napos"
                 └─ Thought: "Kész, válaszolok"
                      └─ Final Answer
```

Ez ma is a domináns agent architektúra alapja. A loop addig fut, amíg a megállási feltétel nem teljesül.

**Problémák:**
- Uninformatív tool eredmények végtelen loophoz vezet
- Hosszú taskok esetén context overflow
- **Megoldás:** Early stopping, dynamic re-planning, hierarchikus memória

---

### Fázis 4: Multi-Agent rendszerek
Több specializált agent koordináltan dolgozik.

```
Orchestrator Agent
  ├─ Research Agent
  ├─ Writing Agent
  └─ Critic Agent
```

**Teljesítmény előny (Gartner, 2025):**
- 45%-kal gyorsabb probléma megoldás
- 60%-kal pontosabb eredmény vs. single-agent

---

## Agent Loop (Cognitive Loop)

A ReAct loop konkrét lépései:

| Lépés | Leírás |
|-------|--------|
| **Perceive** | Bejövő input fogadása (user üzenet, tool eredmény, memória retrieval) |
| **Think** | Reasoning generálása a következő lépésről |
| **Act** | Tool hívás vagy válasz generálás |
| **Observe** | Tool eredmény befogadása a kontextusba |
| **Loop/Stop** | Ismétlés vagy megállás, ha a cél teljesült |

---

## Memory típusok

### In-Context Memory
- A jelenlegi context window tartalma
- Gyors, de korlátozott méretű (pl. 128k token)
- Dinamikusan kezelt: summarizálás, context rewriting

### External Memory
Három altípus:

| Típus | Leírás | Implementáció |
|-------|--------|---------------|
| **Recall Memory** | Teljes interakció-história, kereshető | Disk storage |
| **Archival Memory** | Explicit tudásbázis | Vector DB, Graph DB, KV store |
| **Core Memory** | Kritikus kontextus blokkok (user prefs, task state) | In-context, agent kezeli |

### Episodic Memory
Konkrét események, interakciók és kontextusaik tárolása. Hasonló szituációknál visszakereshető.

### Semantic Memory
Strukturált tudás fogalmakról, tényekről, relációkról. Tipikusan knowledge graph-ban.

**Tárolási megoldások összehasonlítása:**

| Megoldás | Példák | Előny | Hátrány |
|----------|--------|-------|---------|
| Vector Store | Pinecone, Weaviate | Unstrukturált adat | Komplex, drága |
| Key/Value Store | Redis, MongoDB | Gyors, egyszerű | Korlátozott query |
| Knowledge Graph | Neo4J, Cognee | Relációk, determinisztikus | Erőforrás-igényes |

**Ajánlás (2025-2026):** Knowledge graph + vector store kombináció a legjobb agentic RAG-hoz.

---

## Planning stratégiák

### Chain of Thought (CoT)
Lépésenkénti köztes reasoning. Az agent koherens language sequence-t generál cselekvés előtt.

```
"Először megnézem X-et, aztán Y-t, végül összevonom..."
```

### Tree of Thoughts (ToT)
Több reasoning ágat explorál párhuzamosan, keresési stratégiával (DFS, BFS, beam search).
Lehetővé teszi a visszalépést (backtracking) ha egy ág zsákutcába fut.

```
          [Probléma]
         /     |     \
      [Ág 1] [Ág 2] [Ág 3]
        ✗      ✓      ...
```

### Graph of Thoughts (GoT)
A ToT kiterjesztése gráf struktúrával – komplex, nem-hierarchikus reasoning relációkhoz.

### MRKL (Modular Reasoning, Knowledge, Language)
Az LLM-et specializált expert modulokkal (szimbolikus eszközök vagy kisebb LLM-ek) kombinálja. Minden expert a saját domain-jéért felel.

### ReAct Planning
A planning folyamatos, minden observation után. Nem front-loadol mindent az elejére.

### Dynamic Planning
Adaptív test-time compute allokáció: hosszú taskoknál dinamikusan dönt, mikor érdemes tervezni vs. végrehajtani.

---

## Tool use best practices (2026)

1. **Egyértelmű nevek és leírások** – az LLM ezek alapján dönt
2. **Természetes argumentumok** – kerüld az UUID-kat mint input
3. **Sandbox execution** – minden tool call izoláltan fusson
4. **Validáció** – bemeneti értékek ellenőrzése kötelező
5. **Tool Search** (Anthropic, 2025) – ezres nagyságrendű tool-ok kezelésére, context overhead nélkül
6. **Programmatic Tool Calling** – code environment-ben való végrehajtáshoz

---

## Összefoglalás

```
Egyszerű prompt
    ↓ Tool use hozzáadása
Tool-calling LLM
    ↓ Reasoning loop hozzáadása
ReAct Agent
    ↓ Specializáció + koordináció
Multi-Agent System
    ↓ Protokoll-szintű interoperabilitás
Agent Network (MCP + A2A)
```
