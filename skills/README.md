# 5 Skills til dit projekt

Vælg den skill der passer til det projekt du bygger. Læs den — den
fortæller dig præcis hvad du skal gøre, hvad du skal undgå, og hvorfor.

## Hvad er en "skill"?

En skill er en kort, præcis vejledning skrevet til en AI-assistent
(som Hermes). Når du læser den, lærer du:

1. **Hvornår du bruger den** — trigger-ord du kan sige til din AI
2. **Hvad du skal gøre** — en trin-for-trin arbejdsgang
3. **Hvad du IKKE skal gøre** — anti-patterns og faldgruber
4. **Hvorfor det virker** — principperne bag

Du behøver ikke bruge en skill med det samme. Bare **bogmærk den** og
kom tilbage når du er nået dertil i dit projekt.

---

## 1. 📄 [standalone-html-deliverables](standalone-html-deliverables.md) — HJEMMESIDE

> **Lær at bygge en komplet, selvstændig HTML-side** med dark glass-effekter,
> responsivt layout og produktionskvalitet.

| | |
|---|---|
| **Til projekt** | Hjemmeside (eller cheat sheet, CV, portfolio) |
| **Niveau** | Let til mellem |
| **Tid** | 2-4 timer |

**Hvornår du bruger den:** Når du starter hjemmeside-projektet og vil
have det til at se "rigtigt" ud med det samme — ikke bare tekst på en
hvid baggrund.

**Det lærer du:**

- Single-file pattern: ALT i én HTML-fil (HTML + CSS + JS)
- Dark glass-effekt med `backdrop-filter: blur()`
- Responsivt grid der virker på mobil og desktop
- Animationer med CSS transitions
- Konsistent spacing og typografi

---

## 2. 🎮 [html-interactive-games](html-interactive-games.md) — SPIL

> **Single-file HTML-spil med canvas, sprites, kollision og game loop**
> — alt i én fil der bare åbner i browseren.

| | |
|---|---|
| **Til projekt** | Spil (2D i browseren) |
| **Niveau** | Mellem |
| **Tid** | 2-4 timer |

**Hvornår du bruger den:** Når du bygger spil-projektet. Du lærer den
samme måde som de professionelle — ét spil, én fil, ingen build.

**Det lærer du:**

- HTML5 Canvas til at tegne spillet
- Game loop med `requestAnimationFrame`
- Sprite-håndtering og kollision
- Input (tastatur + mus)
- Lyd med Web Audio API

---

## 3. 🎨 [frontend-design](frontend-design.md) — DESIGN (ALLE PROJEKTER)

> **Produktions-kvalitet UI/UX** med animationer, typografi, farver og
> komponenter der ser professionelle ud.

| | |
|---|---|
| **Til projekt** | ALLE (hjemmeside, webshop, app, spil) |
| **Niveau** | Alle niveauer |
| **Tid** | Løbende |

**Hvornår du bruger den:** Hver gang du er ved at give op på hvordan
noget skal se ud. Brug den som **inspiration** mere end regel.

**Det lærer du:**

- Hvordan professionelle designere tænker (typografi, whitespace, motion)
- Hvordan du vælger farver der passer sammen
- Hvordan du laver animationer der føles naturlige
- Hvad der adskiller "elev-projekt" fra "rigtigt produkt"

---

## 4. 🐙 [github-repo-management](github-repo-management.md) — GITHUB (ALLE PROJEKTER)

> **Clone, opret, fork projekter.** Lær at arbejde med GitHub som de
> professionelle — remotes, branches, releases.

| | |
|---|---|
| **Til projekt** | ALLE (når du vil gemme dit projekt) |
| **Niveau** | Let til mellem |
| **Tid** | 30-60 min |

**Hvornår du bruger den:** Når du er færdig med dit projekt (eller en
del af det) og vil gemme det på GitHub, så andre kan se det.

**Det lærer du:**

- `git clone`, `git init`, `git remote add`
- Oprette et nyt repo på github.com
- Pushe dit første commit
- Forstå hvad en branch er, og hvorfor du skal bruge dem

---

## 5. 💡 [web-dev-design-resources](web-dev-design-resources.md) — INSPIRATION (ALLE PROJEKTER)

> **5 must-bookmark websites** med UI-komponenter, design-systemer og
> UX-inspiration du kan kopiere fra.

| | |
|---|---|
| **Til projekt** | ALLE (når du mangler idéer) |
| **Niveau** | Alle |
| **Tid** | 10 min (for at bogmærke) |

**Hvornår du bruger den:** Når du stirrer på din side og tænker "hmm,
hvad nu?". Disse 5 sites giver dig konkrete idéer du kan stjæle.

**Det lærer du:**

- Hvor du finder gode UI-komponenter (knapper, cards, layouts)
- Hvor du finder design-systemer (Stripe, Linear, Vercel)
- Hvor du finder AI-drevet design inspiration
- Hvordan du "remixer" noget du ser, til dit eget

---

## Hvordan bruger du skills?

1. **Vælg den skill der passer** til dit projekt
2. **Åbn filen** (du kan læse den direkte her på GitHub)
3. **Læs "Triggers"** — de ord du kan sige til din AI for at aktivere den
4. **Læs "Steps"** — den præcise arbejdsgang du skal følge
5. **Læs "Pitfalls"** — de ting du skal undgå

**Tip:** Giv din AI linket til skill-filen og sig:
> "Læs den her skill og følg den: [indsæt link]"
> 
> Din AI læser den og arbejder efter den.

---

## De 5 skills i rækkefølge efter projekt

| Projekt | Første skill | Anden skill |
|---------|--------------|-------------|
| **Hjemmeside** | `web-dev-design-resources` (idéer) | `standalone-html-deliverables` (byg) |
| **Webshop** | `frontend-design` (look) | `standalone-html-deliverables` (struktur) |
| **App** | `frontend-design` (look) | `html-interactive-games` (interaktivitet) |
| **Spil** | `html-interactive-games` (det her er kernen) | `frontend-design` (polish) |
| **Brainstorm** | `web-dev-design-resources` (inspiration) | — |
| **ALLE → GitHub** | `github-repo-management` | — |