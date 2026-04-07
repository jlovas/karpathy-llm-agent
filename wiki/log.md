# Activity Log

_Append-only. Soha ne szerkeszd a régi bejegyzéseket._

---

## [2026-04-07] init | Wiki inicializálás

Rendszer: Wiki felépítve Karpathy LLM Wiki architektúra alapján.
Séma: CLAUDE.md létrehozva.
Struktúra: raw/ + wiki/ háromrétegű architektúra.
Forrás anyagok: raw/initial-research/ (5 fájl – kezdeti kutatás eredménye)

## [2026-04-07] compile | Kezdeti tartalom beépítése

Forrás: raw/initial-research/ (5 fájl)
Lapok létrehozva:
- wiki/concepts/ (9 lap)
- wiki/entities/ (10 lap)
- wiki/comparisons/ (2 lap)
- wiki/overview.md
Megjegyzés: Kezdeti tartalom – coverage: medium. Ingest operációkkal bővítendő.

## [2026-04-07] ingest | Karpathy – LLM Wiki (eredeti gist)

Forrás: raw/articles/llm-wiki.md
URL: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
Lap létrehozva: wiki/sources/summary-llm-wiki-gist.md
Lapok frissítve:
- wiki/concepts/llm-wiki-pattern.md (sources +1, query→visszaírás, kép limitáció, log.md unix trick)
- wiki/comparisons/rag-vs-llm-wiki.md (sources +1, Karpathy eredeti idézetek, compounding loop)
- wiki/entities/karpathy.md (sources +1, idea file koncepció, gist dátumok)
- wiki/index.md (új source bejegyzés)
Ellentmondás: nincs. Az eredeti gist megerősíti és gazdagítja a meglévő tartalmat.
Coverage változás: llm-wiki-pattern.md és rag-vs-llm-wiki.md → elsődleges forrással alátámasztva.

## [2026-04-07] lint | Wiki Health Check #1

Ellentmondás: 0
Törött link: 4 (source-initial-research-* lapok hiányoztak) → javítva: stub jelzéssel helyettesítve
Typo: 1 (index.md sor 24: "[kcore") → javítva
Árva lap: 1 (sources/source-antigravity-karpathy-wiki.md – csak index-ből hivatkozott)
Hiányzó lapok: Anthropic (5 helyen szerepel, nincs entity), qmd (2 helyen), AutoGen (1 helyen)
Low coverage: entities/pydantic-ai.md (1 forrás), entities/haystack.md (1 forrás)
Javasolt vizsgálatok: Anthropic entity lap, LangChain vs LangGraph szétválasztás, AutoGen entity, idea file concept lap
