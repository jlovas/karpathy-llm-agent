# LLM Wiki – Schema (CLAUDE.md)

Ez a fájl definiálja hogyan működik az LLM Wiki ebben a projektben.
Téma: **LLM Agents, Agent frameworkök, Karpathy LLM Wiki**
Olvasó: Senior szoftverfejlesztő, Java/Python háttér, tanulási célú projekt.

---

## Könyvtárstruktúra

```
raw/                    ← SOHA NE MÓDOSÍTSD. Immutable forrásanyagok.
  articles/             ← Webes cikkek (Obsidian Web Clipper)
  papers/               ← Kutatási paperek, PDF-ek
  repos/                ← GitHub repo README-k, dokumentációk
  assets/               ← Képek, diagramok (lokálisan letöltve)
  initial-research/     ← Kezdeti kutatási anyagok

wiki/                   ← AZ LLM ÍRJA ÉS TARTJA KARBAN. Te csak olvasod.
  index.md              ← Master katalógus – minden ingest után frissítsd
  log.md                ← Append-only napló – minden operációt rögzíts
  overview.md           ← Magas szintű szintézis – a "big picture"
  concepts/             ← Fogalmak, technológiák, minták
  entities/             ← Szereplők: frameworkök, cégek, személyek
  sources/              ← Forrás-összefoglalók (egy lap = egy raw forrás)
  comparisons/          ← Összehasonlítások, tradeoff elemzések
```

---

## Wiki lap formátum (YAML frontmatter kötelező)

```yaml
---
title: "Lap címe"
type: concept | entity | source-summary | comparison | overview
sources: []             # raw/ fájlok amikre hivatkozik
related: []             # wiki/ lapok amikkel kapcsolódik
created: YYYY-MM-DD
updated: YYYY-MM-DD
coverage: high | medium | low   # high: 3+ forrás, medium: 2, low: 0-1
confidence: high | medium | low
---
```

**Coverage szabályok:**
- `high` (3+ forrás): Megbízható, nem kell raw-t olvasni
- `medium` (1-2 forrás): Elfogadható, érdemes ellenőrizni
- `low` (0-1 forrás): Gyenge alap, raw forrást is nézd meg

**Linkek:** Obsidian `[[wiki-link]]` formátum. Mindig a `wiki/` könyvtárhoz relatív.

---

## Ingest operáció

Amikor azt mondom: **"ingest [fájlnév]"**

1. Olvasd el a forrást a `raw/` könyvtárból
2. Beszéljük át a főbb tanulságokat (kérdezz ha kell)
3. Hozd létre a `wiki/sources/summary-[slug].md` lapot
4. Frissítsd az érintett `wiki/concepts/` lapokat (vagy hozd létre ha nem létezik)
5. Frissítsd az érintett `wiki/entities/` lapokat
6. Ha 2+ forrás ugyanazt a dolgot különbözőképpen mondja: jelöld az ellentmondást
7. Frissítsd a `wiki/index.md`-t (új lap hozzáadása)
8. Fűzz be egy bejegyzést a `wiki/log.md`-be

**Egy ingest 5-15 wiki lapot érinthet.**

---

## Query operáció

Amikor kérdést teszek fel:

1. Olvasd el a `wiki/index.md`-t → azonosítsd a releváns lapokat
2. Olvasd el azokat a lapokat
3. Szintetizálj választ `[[wiki-link]]` hivatkozásokkal
4. Ha az answer értékes → ajánld fel hogy bejegyezzük wiki lapként

**Ha a wiki coverage `low` egy témán → jelezd, és ajánld fel hogy raw forrást is megnézünk.**

---

## Lint operáció

Amikor azt mondom: **"lint"**

Készíts Wiki Health Report-ot:

1. **Ellentmondások** – két lap ütköző állítása (forrásokkal)
2. **Árva lapok** – nincs befelé mutató link (orphan pages)
3. **Hiányzó lapok** – fogalmak amelyek 3+ helyen szerepelnek, de nincs saját lapjuk
4. **Elavult állítások** – régebbi forrás állítása, amelyet újabb megcáfolt
5. **Low coverage lapok** – csak 1 forrással alátámasztott állítások
6. **Javasolt vizsgálatok** – témák amelyeket érdemes mélyebben kutatni

---

## Compile operáció

Amikor azt mondom: **"compile"**

- Csak az utolsó ingest óta módosult lapokat kompilálj újra
- Ellenőrizd a cross-reference konzisztenciát
- Frissítsd az `overview.md`-t ha szükséges

---

## Általános szabályok

- `raw/` könyvtárat SOHA ne módosítsd
- `wiki/log.md`-be csak append (soha ne szerkeszd a régi bejegyzéseket)
- Minden lap kapjon YAML frontmatter-t
- `[[wikilink]]` formátum – ne abszolút útvonalakat használj
- Ha bizonytalan vagy egy állításban: `confidence: low` és jelöld a forrást
- Magyar és angol fogalmak egyaránt használhatók, de legyél konzisztens lapon belül
