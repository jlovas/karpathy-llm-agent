---
title: "LLM Wiki Pattern"
type: concept
sources: [raw/articles/llm-wiki.md, raw/initial-research/04_karpathy.md, raw/articles/antigravity-karpathy-wiki-guide.md]
related: [entities/karpathy, comparisons/rag-vs-llm-wiki, concepts/agentic-rag, sources/summary-llm-wiki-gist]
created: 2026-04-07
updated: 2026-04-07
coverage: high
confidence: high
---

# LLM Wiki Pattern

Karpathy által 2026. április 3-án posztolt, majd április 4-én "idea file"-ként közzétett architektúra.

## A lényeg

A hagyományos RAG minden kérdésnél újra deriválja a tudást. Az LLM Wiki egyszer kompilál, aztán compound-ol.

| | RAG | LLM Wiki |
|-|-----|---------|
| Feldolgozás ideje | Query time | Ingest time |
| Kereszthivatkozások | Ad-hoc | Előre felépítve |
| Ellentmondások | Észrevétlen | Jelzett |
| Tudásfelhalmozás | Nincs | Compound |
| Kimenet | Chat (ephemeral) | Markdown (tartós) |

## Háromrétegű architektúra

**Layer 1 – Raw Sources** (`raw/`): Immutable. Az LLM olvas, de soha nem ír.

**Layer 2 – Wiki** (`wiki/`): Az LLM teljes tulajdona. Summaries, entity pages, concept pages, comparisons.

**Layer 3 – Schema** (`CLAUDE.md`): Az LLM-nek szóló utasítás – struktúra, konvenciók, workflow-k. Ez teszi az LLM-t "wiki maintainer"-ré, nem csak chatbotot.

## Három core operáció

- **Ingest** – új forrás beépítése (1 forrás → 5-15 lap érintve). Karpathy személyes stílusa: egyenként, aktív részvétellel – olvassa a summarykat, irányítja az LLM-et.
- **Query** – kérdezés a wiki-ből. **Értékes válasz visszaírható wiki lapként** – a saját exploráció ugyanúgy compound-ol mint a forrás ingest.
- **Lint** – health check: ellentmondások, árva lapok, hiányzó oldalak

## Karpathy metaforája

> "Obsidian az IDE; az LLM a programozó; a wiki a kódbázis."

## Az "idea file" fogalom

Karpathy nem kódot osztott meg, hanem ötletet – mert az LLM agent személyre szabja az implementációt. Ez egy új open source formátum: nem nyílt kód, hanem **nyílt ötlet**.

## Memex kapcsolat (1945)

[[karpathy]] a Vannevar Bush-féle Memex koncepcióhoz kapcsolja: privát, aktívan kurált tudásbázis asszociatív linkekkel. A hiányzó elem amit Bush nem tudott megoldani: ki csinálja a karbantartást. Az LLM megoldja.

## Kép limitáció (fontos!)

Az LLM nem tudja natívan olvasni a markdownt inline képekkel egy menetben.
**Workaround:** szöveget olvas először, képeket külön lépésben nézi meg.
Obsidian beállítás: `raw/assets/` attachment folder + `Ctrl+Shift+D` hotkey a képek lokális letöltéséhez.

## log.md unix trick

```bash
grep "^## \[" wiki/log.md | tail -5   # utolsó 5 bejegyzés
```

Konzisztens prefix kell: `## [YYYY-MM-DD] operáció | Cím`

## Eszközök

| Eszköz | Szerep | Kötelező? |
|--------|--------|-----------|
| Obsidian | Wiki böngésző / IDE | Ajánlott |
| Obsidian Web Clipper | Web cikk → markdown | Ajánlott |
| qmd | Search 100+ lapnál | Opcionális |
| Git | Verziókezelés | Ajánlott |
| Marp | Prezentáció generálás | Opcionális |
| Dataview | Frontmatter query | Opcionális |
