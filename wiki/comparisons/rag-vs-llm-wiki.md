---
title: "RAG vs LLM Wiki"
type: comparison
sources: [raw/articles/llm-wiki.md, raw/initial-research/04_karpathy.md, raw/articles/antigravity-karpathy-wiki-guide.md]
related: [concepts/llm-wiki-pattern, concepts/agentic-rag, entities/karpathy]
created: 2026-04-07
updated: 2026-04-07
coverage: high
confidence: high
---

# RAG vs LLM Wiki

## Összehasonlítás

| Dimenzió | Hagyományos RAG | LLM Wiki |
|----------|-----------------|---------|
| Feldolgozás ideje | Query time (minden kérdésnél) | Ingest time (egyszer) |
| Kereszthivatkozások | Ad-hoc, kérdésenként | Előre felépítve, tartós |
| Ellentmondások | Észrevétlen marad | Jelzett ingestion-kor |
| Tudás felhalmozás | Nincs – minden kérdésnél nulláról | Compound – minden forrással gazdagodik |
| Kimenet | Chat válasz (ephemeral) | Markdown lap (tartós) |
| Karbantartó | Rendszer (black box) | LLM (átlátható, szerkeszthető) |
| Példák | NotebookLM, ChatGPT uploads | Karpathy LLM Wiki |

## A kulcs különbség (Karpathy – eredeti gist)

> "The LLM is rediscovering knowledge from scratch on every question. There's no accumulation."

> "The wiki is a persistent, compounding artifact. The cross-references are already there. The contradictions have already been flagged."

Az LLM Wiki egyszer kompilál → aztán compound-ol. Minden új forrás gazdagítja a meglévő struktúrát.

**Compounding loop:** forrás ingest → wiki lapok → query → értékes válasz visszaírható → wiki gazdagodik. Nemcsak a forrásokból, hanem a saját kérdezésedből is épül.

## Mikor melyik?

**RAG:** Gyors, egyszeri kérdések nagy dokumentum korpuszra. Nincs időd wikire.

**LLM Wiki:** Mélyülő kutatás hetek/hónapok alatt. Tudás felhalmozása fontos. Visszatérő témák.

## Kapcsolódó

Az [[concepts/agentic-rag]] egy hibrid megközelítés – agent-vezérelt, dinamikus RAG.
