# Plasingsgids — church-studies

## Hoekom heet alles `index.html`?

Dit is nie 'n fout nie, en dit moet so bly.

'n Webbediener soek outomaties na `index.html` wanneer iemand net 'n vouernaam vra. Daarom werk hierdie skakel:

```
stromevanlewe.netlify.app/studies/offence/
```

Die bediener kry `studies/offence/index.html` en wys dit. **As jy die lêer 'n ander naam gee**, moet die besoeker die volle naam tik:

```
stromevanlewe.netlify.app/studies/offence/aanstoot-studie.html
```

Lelik, en elke ou skakel breek. So: die naam is `index.html`, en dit is die **vouer** wat sê waar dit hoort.

Ek het die lêers hier onder tydelike name gegee sodat jy hulle nie kan verwar nie. **Hernoem elkeen wanneer jy dit plaas.**

---

## Die volledige boom

```
church-studies/                          ← die repo se wortel
│
├── index.html                           1_TUISBLAD_index.html
├── README.md                            (reeds korrek genoem)
├── _redirects
├── netlify.toml                         (hernoem van netlify.toml.txt)
│
├── assets/
│   ├── hero.jpg                         (die linosnee)
│   └── logo.png
│
├── bibleplans/
│   └── 3-month-plan/
│       └── index.html                   (bestaan reeds — moenie aanraak nie)
│
├── studies/
│   └── offence/
│       └── index.html                   2_STUDIE_index.html
│
└── boodskappe/
    ├── index.html                       3_BOODSKAPPE_index.html
    ├── index.json                       4_BOODSKAPPE_index.json
    └── m/
        ├── 2026-09-06-hendrik.af.md     5_HENDRIK_2026-09-06.af.md
        └── 2026-09-06-hendrik.en.md     6_HENDRIK_2026-09-06.en.md
```

---

## Die hernoemtabel

| Laai af as | Skuif na hierdie vouer | Hernoem na |
|---|---|---|
| `1_TUISBLAD_index.html` | `/` (die wortel) | `index.html` |
| `2_STUDIE_index.html` | `/studies/offence/` | `index.html` |
| `3_BOODSKAPPE_index.html` | `/boodskappe/` | `index.html` |
| `4_BOODSKAPPE_index.json` | `/boodskappe/` | `index.json` |
| `5_HENDRIK_2026-09-06.af.md` | `/boodskappe/m/` | `2026-09-06-hendrik.af.md` |
| `6_HENDRIK_2026-09-06.en.md` | `/boodskappe/m/` | `2026-09-06-hendrik.en.md` |

**Drie lêers heet `index.html` en hulle is drie verskillende lêers.** Kyk na die nommer voor die naam om te weet watter een waarheen gaan. Moenie hulle omruil nie — die studie is 146 KB, die tuisblad 71 KB, die boodskappe 36 KB, so as jy twyfel, wys die grootte jou.

**Alles in klein letters.** GitHub Pages is hooflettergevoelig. `Boodskappe/` en `boodskappe/` is twee verskillende vouers daar.

---

## Wat is 'n JSON-lêer?

Dit is net 'n netjiese lys. Die rekenaar lees dit, so dit is streng oor drie dinge:

**1. Net dubbele aanhalingstekens.** `"Hendrik"` werk. `'Hendrik'` breek. Ook: 'n regte aanhalingsteken uit Word (`"` of `"`) breek dit. Tik in 'n gewone teksredigeerder, nie in Word nie.

**2. 'n Komma tussen items, maar nie ná die laaste een nie.**

```json
"speaker": "Hendrik",
"date": "2026-09-06"          ← geen komma, want dit is die laaste
```

**3. Elke `{` het 'n `}` en elke `[` het 'n `]`.**

Dit is al. As iets breek, is dit byna altyd een van hierdie drie.

---

## Om 'n nuwe boodskap by te voeg

**Stap 1 — Twee teksleêrs.**

Neem jou dokument, sny die frontmatter bo-aan af (die deel tussen die twee `---` reëls), en stoor as:

```
boodskappe/m/2026-09-13-dawid.af.md
boodskappe/m/2026-09-13-dawid.en.md
```

Die naam is jou keuse, maar hou by die patroon **datum-spreker**. Dit sorteer vanself en jy weet oor drie jaar nog wat dit is.

**Stap 2 — Een inskrywing in `boodskappe/index.json`.**

Maak die lêer oop. Jy sien:

```json
"messages": [
  {
    ... Hendrik se inskrywing ...
  }
]
```

Plak jou nuwe blok **voor** Hendrik s'n, en sit 'n komma tussen die twee blokke. Nuutste bo.

Hier is 'n leë een om te kopieer:

```json
    {
      "id": "2026-09-13-dawid",
      "date": "2026-09-13",
      "speaker": "Dawid",
      "series": { "af": "Aanstoot", "en": "Offence" },
      "seriesNo": 2,
      "title": {
        "af": "Afrikaanse titel",
        "en": "English title"
      },
      "summary": {
        "af": "Twee of drie sinne wat sê waaroor dit gaan.",
        "en": "Two or three sentences saying what it is about."
      },
      "texts": [
        { "af": "Matteus 18:15", "en": "Matthew 18:15", "osis": "MAT.18.15" }
      ],
      "tags": ["aanstoot", "vergifnis"],
      "media": { "audio": "", "video": "" },
      "related": []
    },
```

**Die `id` moet presies ooreenstem met die lêername** in `m/`, sonder die `.af.md`. As die `id` `2026-09-13-dawid` is, moet die lêers `2026-09-13-dawid.af.md` en `2026-09-13-dawid.en.md` heet. Dít is die veld wat die meeste foute veroorsaak.

**Die `osis`-kode** is hoe die blad die bible.com-skakel bou. Die patroon is `BOEK.HOOFSTUK.VERS`:

| Boek | Kode | | Boek | Kode |
|---|---|---|---|---|
| Genesis | `GEN` | | Matteus | `MAT` |
| Psalm | `PSA` | | Markus | `MRK` |
| Spreuke | `PRO` | | Lukas | `LUK` |
| Jesaja | `ISA` | | Johannes | `JHN` |
| Handelinge | `ACT` | | Romeine | `ROM` |
| 1 Korintiërs | `1CO` | | 2 Korintiërs | `2CO` |
| Galasiërs | `GAL` | | Efesiërs | `EPH` |
| Filippense | `PHP` | | Kolossense | `COL` |
| Hebreërs | `HEB` | | Jakobus | `JAS` |
| 1 Petrus | `1PE` | | Openbaring | `REV` |

Voorbeelde: `GAL.5.17` · `PSA.46.5` · `MAT.18.15`

**Die `media`-veld** bly leeg totdat daar 'n opname is. Dan:

```json
"media": { "audio": "https://.../preek.mp3", "video": "https://youtu.be/xxxx" }
```

Albei is opsioneel. Los leeg wat nie bestaan nie.

**Die `related`-veld** skakel na iets anders op die webwerf. Los as `[]` as daar niks is nie, of:

```json
"related": [
  { "href": "../studies/offence/#s6", "af": "Studie · Sessie 6", "en": "Study · Session 6" }
]
```

---

## Kontroleer voordat jy stoot

**Die JSON:** gaan na `jsonlint.com`, plak die hele lêer in, druk *Validate*. Dit sê in een sekonde of dit reg is en wys presies watter reël stukkend is. Doen dit elke keer — dit vat tien sekondes en spaar 'n aand se soek.

**Ná die stoot**, maak `stromevanlewe.netlify.app/boodskappe/` oop:

| Wat jy sien | Wat dit beteken |
|---|---|
| Jou boodskap in die lys | Alles reg |
| Die lys is heeltemal leeg | Die JSON is stukkend — gaan jsonlint |
| Boodskap is in die lys, maar "Kon nie die boodskap laai nie" | Die `id` stem nie ooreen met die lêernaam in `m/` nie |
| Hele blad is blank | 'n Lêer is op die verkeerde plek, of 'n hoofletter is verkeerd |

---

## Kortweg

1. Laai die ses lêers af
2. Hernoem elkeen volgens die tabel hierbo
3. Sit elkeen in sy vouer
4. Hernoem `netlify.toml.txt` na `netlify.toml`
5. Stoot
6. Maak die webwerf oop en klik deur al drie afdelings
