---
title: "Source: Antigravity.codes – Karpathy LLM Wiki Guide"
type: source-summary
sources: [raw/articles/antigravity-karpathy-wiki-guide.md]
related: [concepts/llm-wiki-pattern, comparisons/rag-vs-llm-wiki, entities/karpathy]
created: 2026-04-07
updated: 2026-04-07
coverage: high
confidence: high
---

# Antigravity.codes: Karpathy's LLM Wiki – The Complete Guide

**Forrás:** https://antigravity.codes/blog/karpathy-llm-wiki-idea-file
**Megjelent:** 2026-04-04

## Főbb tanulságok

1. **Idea file formátum** – Karpathy nem kódot, hanem ötletet osztott meg. Az LLM agent testreszabja az implementációt. Új open source paradigma: nyílt ötlet, nem nyílt kód.

2. **RAG vs Wiki** – A wiki egyszer kompilál, RAG minden kérdésnél újraderál. A wiki compound-ol.

3. **Háromrétegű architektúra** – raw/ (immutable) + wiki/ (LLM-owned) + CLAUDE.md (schema/executable spec)

4. **3 operáció** – Ingest (1 forrás → 5-15 lap érintve), Query (értékes válasz visszaírható), Lint (health check)

5. **index.md RAG helyett** – Moderált méretig (100 forrás, ~100-400 lap) az index.md elegendő navigációhoz. qmd kellhet tovább.

6. **log.md audit trail** – Append-only, unix-toolokkal parseable (`grep "^## [" log.md | tail -5`)

7. **Tool stack** – Obsidian (IDE/viewer), Web Clipper (ingest), qmd (search 100+ lapnál), Marp (prezentáció), Dataview (frontmatter query), Git (verziókezelés)

8. **Memex kapcsolat** – Vannevar Bush 1945-ös víziója. Az LLM megoldja a karbantartási problémát.

9. **Community fejlesztések** – .brain folder pattern, gist-alapú agent-agent kommunikáció, "append and review" evolúciója

## Karpathy idézet

> "Obsidian az IDE; az LLM a programozó; a wiki a kódbázis."

> "A dokumentum egyetlen feladata hogy kommunikálja a mintát. Az LLM kitalálja a többit."
