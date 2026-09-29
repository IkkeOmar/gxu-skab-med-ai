# GXU — Skab med AI

Workshop-materiale til GXU onsdag d. 30. september 2026.

Målgruppe: 7.-8. klasse. Workshoppen er "kom-igang"-tonen — ikke et foredrag.

## Indhold

- **`index.html`** — Hovedpræsentationen. Åbn den i browseren, tryk F11 for fuld skærm, brug pil-tasterne til at navigere. Responsiv — virker også på telefon (vertikal scroll + tap-knap).
- **`prompts.html`** — Den side QR-koden peger på. **6 prompts i 5 sektioner:**
  - Sektion 01: 4 projekt-prompts (hjemmeside / webshop / app / spil)
  - Sektion 02: Første prompt til Hermes når du er logget ind
  - **Sektion 03: 4 hurtige drop-pocket prompts** (Brainstorm / Forklar kode / "Det virker ikke" / Refactor)
  - Sektion 04: GitHub — sådan logger du ind og laver en token
  - Sektion 05: 5 skills hvis du vil lære mere
- **`mobile.html`** — Elev-guide designet til telefonen. Lodret scroll, forklarer værktøjer, prompting, de 4 projekter, og hvordan man giver sin AI-agent adgang til GitHub. Linker direkte til `prompts.html` med CTA-knap.
- **`cheatsheet.html`** — 1-sides Hermes cheat sheet. Alle slash-kommandoer, providers, profil-værktøjer.
- **`assets/`** — Billeder, videoer og QR-kode.

## Slides

1. Forside + interaktivt kursus-map (8 kort + "Få prompts med hjem" CTA)
2. Om Omar (DTU-forsker + vaskebjørn-GIF)
3. 4 ord du skal kende (Server, LLM, AI-agent, Harness)
4. **Hvad er kodning?** (definition + 4 egenskaber)
5. Brainstorm med gratis AI + QR-kode + CTA-knap
6. Sådan snakker du med en AI (trash in / trash out)
7. Værktøjerne (OpenRouter, GitHub, VSCode, Hermes) — **alle 4 er klikbare links til deres hjemmesider**
8. Vælg dit projekt + QR-kode + CTA-knap
9. Go build + **inspirations-link til codecrafters-io/build-your-own-x** + **6 end-points** + QR-kode + CTA-knap

Alle slides med QR-kode har en orange **"ELLER ÅBN HER →"** CTA-knap ved siden af, så man ikke behøver at scanne for at komme til `prompts.html`.

## Navigation

- `→` eller `SPACE` — næste slide
- `←` — forrige slide
- `1-9` — hop direkte til en slide
- `F` — fullscreen til/fra
- `V` — **VISION-mode** (større tekst til bagerst-i-klassen, se nedenfor)
- Klik på et kort på slide 1 for at hoppe til det emne
- Klik på en orange CTA-knap for at gå direkte til `prompts.html`

## Vision-mode

Tryk `V` på tastaturet for at slå vision-mode til/fra. Alle slides skalerer op så teksten kan læses fra bagerst i klassen (8-10m afstand med projektor). Orange "👁️ VISION MODE" indikator vises i øverste højre hjørne.

**Vision-mode er kun til desktop** (window.innerWidth > 768px). På telefon giver det ikke mening — der scroller man allerede vertikalt, og mobil-mediaqueryens egne font-sizes vinder automatisk. V-tasten ignoreres også på mobil.

| Element | Normal | Vision |
|---------|--------|--------|
| H1 (forside + slut) | 88px | 110px |
| H2 (slide-overskrift) | 56px | 76px |
| H3 (kort-titel) | 24px | 32px |
| Body / lead | 14-22px | 17-30px |
| Slide padding | 56×72px | 80×90px |

Alle 9 slides er testet til at passe i 1440×900 viewport uden overflow i både normal og vision-mode. Mobil-layout (375×667) er upåvirket af vision-mode.

## Links

Præsentationen linker til gratis AI-tjenester: Kimi, DeepSeek, Z.ai, Gemini, ChatGPT, samt fmhy.net/ai som oversigt.
