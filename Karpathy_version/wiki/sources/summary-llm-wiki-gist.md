---
title: "Source: Karpathy – LLM Wiki (eredeti gist)"
type: source-summary
sources: [raw/articles/llm-wiki.md]
related: [concepts/llm-wiki-pattern, comparisons/rag-vs-llm-wiki, entities/karpathy]
created: 2026-04-07
updated: 2026-04-07
coverage: high
confidence: high
---

# Karpathy – LLM Wiki (eredeti gist)

**Forrás:** https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
**Típus:** Idea file – szándékosan absztrakt, LLM agent-nek szánva

---

## Főbb tanulságok

### 1. A core idea – RAG vs Wiki

> "The LLM is rediscovering knowledge from scratch on every question. There's no accumulation."

A wiki **persistent, compounding artifact** – a kereszthivatkozások már megvannak, az ellentmondások már jelzve vannak, a szintézis tükrözi mindazt amit olvastál.

### 2. Háromrétegű architektúra

- `raw/` – immutable forrás, az LLM olvas, nem ír
- `wiki/` – az LLM teljes tulajdona
- schema (CLAUDE.md) – ez teszi az LLM-et wiki maintainer-ré, nem csak chatbot-tá

> "You and the LLM co-evolve this over time."

### 3. Ingest – személyes preferencia

Karpathy egyenként ingestál, aktívan részt vesz: elolvassa a summarykat, ellenőrzi a frissítéseket, irányítja az LLM-et mit hangsúlyozzon. Lehet batch is, de a kurátor jelenlét értéket ad.

### 4. Query → visszaírás (compounding loop)

> "Good answers can be filed back into the wiki as new pages."

A felfedezés ugyanúgy compound-ol mint a forrás ingest. A wiki nemcsak külső forrásokból, hanem saját explorációdból is gazdagodik.

### 5. log.md unix trick

Konzisztens prefix → parseable:
```
## [2026-04-02] ingest | Article Title
```
```bash
grep "^## \[" log.md | tail -5   # utolsó 5 bejegyzés
```

### 6. Kép limitáció

Az LLM nem tudja natívan olvasni a markdownt inline képekkel egy menetben. Workaround: szöveg először, képek külön lépésben. "A bit clunky but works well enough."

### 7. Az idea file szándékos absztraktsága

> "Everything mentioned above is optional and modular."

Nincs kötelező eszköz. A séma a doménhez igazodik, nem fordítva. A dokumentum egyetlen feladata: kommunikálni a mintát.

### 8. Memex kapcsolat (Vannevar Bush, 1945)

Privát, aktívan kurált tudásbázis asszociatív linkekkel. A hiányzó elem: ki csinálja a karbantartást. Az LLM megoldja – nem unatkozik, nem felejt el cross-reference-t frissíteni, 15 fájlt érint egy menetben.

---

## Use case-ek amiket Karpathy említ

- Személyes (célok, egészség, önfejlesztés)
- Kutatás (mélyülő téma hetek/hónapok alatt)
- Könyvolvasás (Tolkien Gateway analógia)
- Business/team (Slack, meeting transcripts, project docs)
- Competitive analysis, due diligence, trip planning, hobby deep-dives

---

## Nincs ellentmondás a meglévő wiki tartalommal.

Ez a forrás a [[concepts/llm-wiki-pattern]] és [[comparisons/rag-vs-llm-wiki]] lapok **elsődleges forrása**.
