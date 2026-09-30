---
name: web-dev-design-resources
description: 5 must-bookmark websites for web dev design — UI components, AI design systems, UX inspiration. Load before web dev styling tasks.
tags: [design, ui, ux, inspiration, components, tailwind, framer-motion, figma, design-systems, frontend]
related_skills: [standalone-html-deliverables, fable-mode]
---

# Web Dev Design Resources — 5 Must-Bookmark Sites

**Brug:** Når brugeren laver front-end / web dev / UI styling → load denne skill først.

En samling af 5 websites til UI-komponenter, design systems og inspiration.

---

## 1. Aceternity UI — `ui.aceternity.com`

200+ **production-ready UI-komponenter** med Tailwind CSS + Framer Motion.

**Bedst til:** Landing pages, hero sections, bento grids, backgrounds — copy-paste i React/Next.js.

- Gratis komponenter + All-Access Pass (premium)
- Copy-paste — ingen kompleks opsætning
- Brugt af Google, Microsoft, Cisco, Harvard
- Creator: Mannu Paaji
- Templates: Agency, SaaS, AI Agent

**Brug:** Skal bruge flot hero/animation på 5 min → Aceternity.

---

## 2. Refero Style — `styles.refero.design`

2.000+ **DESIGN.md** design system-filer fra verdens bedste produkter — AI-ready.

**Bedst til:** At give din AI-agent (Cursor, Claude Code, Codex, v0) en præcis design-guide før den koder.

- AI-readable format: farver, typografi, spacing, komponenter
- Real-world: Apple, Vercel, Claude, ElevenLabs, Mercury, shadcn/ui
- Søgbar m. visuelle previews
- Refero MCP — giv AI adgang til tusindvis af produkt-screens

**Brug:** AI coding → smid et DESIGN.md ind som context.

---

## 3. Mobbin — `mobbin.com`

Verdens største bibliotek af **real-world UI/UX screenshots** — 1.428 apps, 621.500+ screens.

**Bedst til:** UX research — se hvordan apps løser checkout, onboarding, settings, login, etc.

- 50+ UI patterns (searchable)
- Video mode: flows med micro-interactions
- Prototype mode: interactive hotspots
- Figma Plugin: copy direkte til Figma
- Brugt af Figma, Coinbase, Airbnb, Uber, Spotify, Notion
- Free tier

**Brug:** UX research → se hvordan Airbnb/Uber/Shopify gør det på 2 min.

---

## 4. Godly — `godly.website`

Kurateret galleri af **verdens bedste web design** — opdateret dagligt.

**Bedst til:** Visuel inspiration — layouts, farver, design-retninger.

- Dagligt opdateret
- SaaS, portfolios, ecommerce, marketing
- Fokus på kreative high-quality websites

**Brug:** Mangler inspiration til nyt projekt → browse Godly.

---

## 5. 10x — URL unknown

**Status:** Kunne ikke identificere domænet entydigt. Instagram-reelen (@kiksugc, "Idea to functioning IOS app in minutes #10x #vibecoding") nævner "10x" — muligvis hashtag #10x der blev misforstået som sitenavn.

**Bedste bud:** `10xdesigners.co` (10X Hub — design resource hub) eller `10x.framer.website` (10x Designers community).

**Hvis du ved URL'en:** patch med `skill_view(name='web-dev-design-resources')` og opdater.

---

## Workflow — Hvornår bruger du hvad?

**UI-komponenter (hero, bento, animation)** → Aceternity UI
**AI design-guide før coding** → Refero Style (DESIGN.md)
**UX research — real-world patterns** → Mobbin
**Visuel inspiration — find retning** → Godly
**10x** → Spørg brugeren hvis du mangler URL

---

**Oprindelse:** Instagram reel af @kiksugc (Joaquin Fernandez) — #10x #vibecoding

---

## Reusable CSS Components (fra sessionsarbejde)

Hurtige dark-theme datavisualiseringsmønstre, opdaget og dokumenteret fra brugerens projekter. Se `references/data-viz-patterns.md` for fuld reference.

| Pattern | Brug | Klasse |
|---------|------|--------|
| **Data Grid** | Finansielle metrics (revenue, assets, debt, ratio) | `.data-grid` |
| **Rate Chart** | Sammenligningssøjler med severity-farver | `.rate-chart` |

**Farvekodning:** `pos` = grøn (positiv), `neg` = rød (negativ), `neu` = guld (neutral).  
**Severity:** `danger` >75%, `high` 50-75%, `med` 25-50%, `low` <25%.

Brugerens præference: data skal kunne aflæses på <1 sekund → brug visuelle søjler, progress bars, og farvekodning frem for monospace tekstblokke.

## Network Maps (vis.js) — Regler & Mønstre

Når du bygger **netværkskort** med vis.js (`new vis.Network`) i mørk baggrund, følg disse mønstre. Se `references/data-viz-patterns.md` → afsnit "Vis.js Network Map Patterns" for fuld reference.

### 🔐 KRITISK: Verificér alle edges mod research-data

**FØR du deployer** et netværkskort, skal du **altid krydstjekke hver eneste edge** mod den originale research-fil. Brugeren opdager med det samme hvis pile peger forkert.

**Workflow:**
1. Læs research-filen (f.eks. `pitch.md`) — find alle relationer
2. Krydstjek hver edge mod research: fra→to + label skal matche kilden
3. Særligt udsatte: labels der gætter en persons rolle (f.eks. "Næstform." vs "Flagkonsulent"), og indirekte forbindelser (f.eks. NKN GRAFISK → foreningen er en stretch)
4. Tilføj `title` på ALLE nodes og edges — rich HTML tooltips så man kan se detaljerne

### 🎯 Node-former efter type

| Type | vis.js shape | Eksempel |
|------|-------------|----------|
| Personer | `dot` (cirkel) | Kim Andersen, Ernst Jønsson |
| Organisationer | `diamond` | Kongehuset, Odd Fellow |
| Penge/entiteter | `box` | Energinet, SSF, NKN GRAFISK |

### ⚙️ Anbefalet physics

```js
physics: {
  solver: "forceAtlas2Based",
  forceAtlas2Based: {
    gravitationalConstant: -40,
    centralGravity: 0.005,
    springLength: 180,
    springConstant: 0.02,
    damping: 0.4
  },
  stabilization: { iterations: 100 }
}
```

### 💡 Tooltips

Alle nodes og edges skal have en `title` (HTML-streng) så brugeren kan hover og se detaljer. Edge-titles skal forklare relationen i klartekst.

### 🎨 Kanter (edges)

- Brug `arrows: { to: { enabled: true, scaleFactor: 0.8, type: "arrow" } }` i stedet for `arrows: "to"` — giver mere kontrol
- Edge-farve: `"rgba(255,255,255,0.12)"` med highlight/hover i accentfarve
- `smooth: { type: "curvedCW", roundness: 0.08 }` for pæne buede linjer
- Label-farve: `"rgba(255,255,255,0.35)"`, size: 8, strokeWidth: 0

### ⚠️ Pitfalls

- **Guessed labels:** Brug ALDRIG en label du ikke har verificeret mod research. "Næstformand" for Cruys-Bagger var forkert — han er flagkonsulent.
- **Indirekte forbindelser:** En persons tidligere selskab (NKN GRAFISK) er IKKE foreningens oprindelse. Forbindelsen går gennem personen, ikke direkte til foreningen.
- **Dobbelt-protektor:** Hvis Prins Joachim kun er protektor for D-S Sydslesvig, skal pilen gå 19→14, IKKE 10→19.
- **Overflødige kanter:** Hvis én edge allerede dækker en relation (f.eks. 5→20 "Rådgiver"), så tilføj ikke en ekstra (10→20 "Råder").