---
name: standalone-html-deliverables
category: web
description: Build polished, production-quality standalone HTML pages (guides, docs, dashboards, cheat sheets, proposals). Dark glass-morphism design system with animations, copyable code blocks, callout boxes, accordions, and responsive layout — all in a single self-contained .html file. No build tools, no framework.
related_skills: [deliverable-hosting, web-dev-design-resources, fable-mode]
triggers:
  - "create a guide / doc / reference page"
  - "build a standalone HTML page"
  - "make a polished cheat sheet"
  - "deliver documentation as HTML"
  - "single-page HTML deliverable"
  - "visual documentation page"
  - "build an interactive reference card"
  - "create a setup guide as HTML"
  - "build a pitch deck / presentation page"
  - "create an HTML slide deck"
  - "make a sales or investor deck"
  - "technical proposal page"
  - "use phosphor icons / replace emojis"
  - "make it look less AI / less template"
  - "grain texture / wave divider / dot grid design"
---

# Standalone HTML Deliverables

Build beautiful, self-contained HTML pages in a single file. Dark glass-morphism design system, inline CSS, no dependencies beyond CDN-free fonts and CSS-only interactivity.

## Design System (CSS Variables)

The skill ships with two documented palettes. Choose the one that fits the audience.

### Variant A: Default Hermes Palette (Dark Tech)

Used for most guides, docs, and technical deliverables. Blue/purple accent blend on dark slate.

```css
@import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600&display=swap');

:root {
  --bg: #0a0b0f;        /* page background */
  --bg2: #111318;       /* card background */
  --bg3: #181b21;       /* code block background */
  --border: #22262e;    /* subtle borders */
  --text: #e3e6eb;      /* primary text */
  --text2: #8b92a0;     /* secondary / muted text */
  --accent: #6c8aff;    /* primary accent (blue) */
  --accent2: #a78bfa;   /* secondary accent (purple) */
  --green: #34d399;     /* success */
  --orange: #fbbf24;    /* warning */
  --red: #f87171;       /* error / danger */
  --font: 'JetBrains Mono','SF Mono','Cascadia Code','Fira Code','Consolas',monospace;
  --font-body: -apple-system,BlinkMacSystemFont,'Segoe UI',system-ui,sans-serif;
}
```

### Variant B: NILT Navy Palette (Corporate Dark)

Use for corporate / engineering-firm deliverables where a professional navy identity is requested. Modeled after nilt.com's Elementor/Astra design system. Navy-deep backgrounds, light-blue accent, Montserrat body font.

```css
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800&family=JetBrains+Mono:wght@400;500;600&display=swap');

:root {
  --bg: #0b0b20;        /* deep navy — page, header bg (darkened from #0d0d30 for richer contrast) */
  --bg2: #0f0f2a;       /* dark navy — section backgrounds (darkened) */
  --bg3: #14143a;       /* navy blue — card, code block bg (darkened) */
  --border: #1e3a5f;    /* teal-navy borders */
  --text: #e3e6eb;      /* light text on dark */
  --text2: #b0c4d8;     /* muted blue-gray text */
  --accent: #6ec1e4;    /* light blue — primary accent (nilt.com) */
  --accent2: #087bc5;   /* medium blue — hover, secondary accent */
  --green: #34d399;     /* success */
  --orange: #fbbf24;    /* warning */
  --red: #f87171;       /* error / danger */
  --font: 'JetBrains Mono','SF Mono','Cascadia Code','Fira Code','Consolas',monospace;
  --font-body: 'Montserrat',-apple-system,BlinkMacSystemFont,'Segoe UI',system-ui,sans-serif;
}
```

**Key differences from Variant A:**
- Backgrounds are navy (`#0d0d30`) instead of cool slate (`#0a0b0f`)
- Accent is light blue (`#6ec1e4`) instead of violet-blue (`#6c8aff`)
- Body font is Montserrat (corporate/professional feel)
- Muted text is warmer (`#b0c4d8` vs `#8b92a0`)
- All callout/card borders use `rgba(110,193,228, .xx)` tinting instead of the default accent colors

### Switching Palettes

To swap from Variant A to Variant B in an existing deliverable:
1. Replace the `@import url(...)` line (add Montserrat, keep JetBrains Mono)
2. Replace the entire `:root {}` block with Variant B's values
3. Update any hardcoded accent colors in `.callout`, `.phase-dot`, `.arch-card:hover` borders, nav background
4. Hero gradient: `linear-gradient(135deg, #6ec1e4, #00355A)` instead of the default
5. Footer + nav bg: `rgba(13,13,48,.92)` instead of `rgba(10,11,15,.85)`
6. On Glass cards: change `rgba(108,138,255,.12)` → `rgba(110,193,228,.12)` for active states
7. Keep ALL animations, copy buttons, and structural HTML — only colors and typography change

### Variant C: NILT Navy Deep (Updated)

Refined version of Variant B with deeper backgrounds for richer contrast:

```css
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&family=DM+Serif+Display:ital@0;1&family=JetBrains+Mono:wght@400;500;600&display=swap');

:root {
  --bg: #0b0b20;
  --bg2: #0f0f2a;
  --bg3: #14143a;
  --border: #1e1e50;
  --text: #e8e8f0;
  --text2: #9090b8;
  --accent: #6ec1e4;
  --accent2: #4a8fd0;
  --green: #34d399;
  --orange: #fbbf24;
  --red: #f87171;
  --purple: #a78bfa;
  --font: 'JetBrains Mono','SF Mono','Cascadia Code','Fira Code','Consolas',monospace;
  --font-body: 'Inter',-apple-system,BlinkMacSystemFont,'Segoe UI',system-ui,sans-serif;
  --font-display: 'DM Serif Display',Georgia,serif;
}
```

**Changes from Variant B:**
- Backgrounds deepened (`#0b0b20` ← `#0d0d30`, `#14143a` ← `#161655`)
- Body font is Inter (cleaner, more modern) instead of Montserrat
- DM Serif Display added for quote blocks and subtitles (adds personality)
- Muted text cooler (`#9090b8` ← `#b0c4d8`)
- Purple added as secondary accent (`#a78bfa`)
- Borders darker for more contrast (`#1e1e50` ← `#1e3a5f`)
- Use with Inter + JetBrains Mono + optional DM Serif Display for `italic` touches

### Phosphor Icons (Replace Emojis)

**User preference: use Phosphor icons instead of emojis in card icon divs, callouts, highlight bars, and all decorative elements.** See `references/phosphor-icons.md` for the full mapping table, CDN setup, and usage pattern.

```html
<!-- Instead of --> <div class="icon">🔒</div>
<!-- Use -->        <i class="ph ph-lock-key" style="color:var(--accent);font-size:22px"></i>
```

CDN: `<script src="https://unpkg.com/@phosphor-icons/web@2.1.1"></script>` — add to `<head>` or before `</body>`.

The reference file maps ~60+ emojis to their Phosphor equivalents across cards, callouts, highlight bars, hero badges, section labels, and nav elements.

### Anti-Template Design Patterns ("Less AI" Techniques)

When the user says "make it look less AI" or "more original," apply one or more of these patterns to break the default glass-morphism template look:

#### 1. Grain Texture Overlay

Adds subtle noise to the background — kills the sterile flat look:

```css
body::before{
  content:'';position:fixed;inset:0;z-index:-1;pointer-events:none;
  opacity:.2;
  background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
  background-size:256px 256px;
}
```

Adjust `opacity` (`.2` = subtle, `.35` = noticeable, `.5` = heavy texture).

#### 2. Dot Grid Background

Pattern overlay on the page body or hero section:

```css
body{
  background-image:
    radial-gradient(rgba(110,193,228,.04) 1px,transparent 1px);
  background-size:32px 32px;
}
```

For hero-only: add a `.dot-grid` div with the same properties, `pointer-events:none`.

#### 3. Wave/Curve SVG Dividers

Replace plain `<hr>` / gradient-line dividers between sections:

```html
<div class="wave-divider">
  <svg viewBox="0 0 1200 32" preserveAspectRatio="none">
    <path d="M0,16 Q60,32 120,16 T240,16 T360,16 T480,16 T600,16 T720,16 T840,16 T960,16 T1080,16 T1200,16" stroke-width="1.5"/>
  </svg>
</div>
```

```css
.wave-divider{position:relative;height:48px;overflow:hidden;display:flex;align-items:flex-end;justify-content:center;max-width:100%}
.wave-divider svg{width:100%;height:32px;opacity:.15}
.wave-divider svg path{fill:none;stroke:var(--accent);stroke-width:.5}
```

Vary the path control points for different wave shapes (sine, sawtooth, single-curve).

#### 4. Animated Hero Gradient

Adds a shifting gradient to hero title text instead of static:

```css
.hero h1 span{
  background:linear-gradient(135deg,var(--accent),var(--purple),var(--accent2));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  background-size:200% 200%;animation:gradientShift 6s ease-in-out infinite
}
@keyframes gradientShift{0%,100%{background-position:0% 50%}50%{background-position:100% 50%}}
```

Adds motion to the hero without being distracting. Works with any 2-3 color gradient.

#### 5. Display Font for Quotes

Use a serif display font (DM Serif Display, Playfair Display, etc.) for quote blocks to add editorial personality:

```css
/* Add to Google Fonts import */
@import url('https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&display=swap');

/* Use as font for quote text */
.quote-block p{font-family: 'DM Serif Display', Georgia, serif; font-style: italic;}
```

Pair with `<i class="ph ph-quotes"></i>` instead of a CSS pseudo-element for the quote mark.

#### 6. Card Hover Gradient Overlay

Adds a subtle directional gradient that fades in on hover, breaking the solid card look:

```css
.card{position:relative;overflow:hidden}
.card::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,rgba(110,193,228,.02),transparent 60%);
  pointer-events:none;opacity:0;transition:opacity .35s
}
.card:hover::before{opacity:1}
```

#### 7. Nav Underline Animation

Adds an animated underline on nav link hover — small polish detail:

```css
nav .links a{position:relative}
nav .links a::after{
  content:'';position:absolute;bottom:2px;left:50%;transform:translateX(-50%);
  width:0;height:2px;border-radius:2px;
  background:var(--accent);transition:width .2s
}
nav .links a:hover::after{width:20px}
```

#### 8. Polished Comparison Tables (Stripe + Sticky + Scroll Gradient)

For tables that compare options across many dimensions, use these enhancements to make them scannable on desktop AND mobile.

**CSS:** `border-collapse: separate; border-spacing:0;` instead of `collapse` — enables rounded corners:

```css
.comp-table{width:100%;border-collapse:separate;border-spacing:0;font-size:13px}
.comp-table thead{position:sticky;top:0;z-index:2}
.comp-table thead tr{background:rgba(110,193,228,.04)}
.comp-table th{
  padding:14px 16px;text-align:left;font-family:var(--font);font-size:10px;
  text-transform:uppercase;letter-spacing:.5px;color:var(--accent);font-weight:600;
  border-bottom:1px solid var(--border);background:rgba(11,11,32,.8);backdrop-filter:blur(8px)}
.comp-table th:first-child{border-radius:12px 0 0 0}
.comp-table th:last-child{border-radius:0 12px 0 0}
.comp-table td{padding:12px 16px;text-align:left;color:var(--text2);transition:background .15s}
.comp-table tr td{border-bottom:1px solid rgba(255,255,255,.025)}
.comp-table tbody tr:nth-child(even) td{background:rgba(255,255,255,.008)}
.comp-table tbody tr:hover td{background:rgba(110,193,228,.04)}
.comp-table tbody tr:last-child td:first-child{border-radius:0 0 0 12px}
.comp-table tbody tr:last-child td:last-child{border-radius:0 0 12px 0}
```

**Sticky first column** (labels always visible when scrolling horizontally on mobile):

```css
.comp-table td:first-child{
  color:var(--text);font-weight:500;white-space:nowrap;
  position:sticky;left:0;z-index:1
}
.comp-table td:first-child::after{
  content:'';position:absolute;right:0;top:0;bottom:0;
  width:1px;background:linear-gradient(180deg,transparent,var(--border),transparent)}
```

On mobile, the sticky column needs its own background to avoid showing cells beneath:

```css
@media(max-width:768px){
  .comp-table td:first-child{position:sticky;left:0;z-index:1;background:var(--bg3)}
  .comp-table tbody tr:nth-child(even) td:first-child{background:rgba(20,20,58,1)}
}
```

**Scroll-gradient indicator** — a fade on the right edge that tells users the table scrolls:

```css
.table-wrapper{
  overflow-x:auto;border:1px solid var(--border);border-radius:16px;
  background:var(--bg3);position:relative}
.table-wrapper::after{
  content:'';position:absolute;right:0;top:0;bottom:0;width:32px;
  background:linear-gradient(90deg,transparent,rgba(11,11,32,.6));
  pointer-events:none;opacity:0;transition:opacity .3s;border-radius:0 16px 16px 0}
.table-wrapper:not(.at-end)::after{opacity:1}
```

**JS to toggle `.at-end`:**

```javascript
document.querySelectorAll('.table-wrapper').forEach(function(w){
  function check(){ w.classList.toggle('at-end', w.scrollLeft + w.clientWidth >= w.scrollWidth - 4); }
  w.addEventListener('scroll', check);
  setTimeout(check, 100);
});
```

**Same pattern for `cmd-table` variant:**

```css
.cmd-table{width:100%;border-collapse:separate;border-spacing:0;margin:16px 0;font-size:13px}
.cmd-table th,.cmd-table td{padding:10px 12px;text-align:left;border-bottom:1px solid rgba(255,255,255,.025)}
.cmd-table th{font-family:var(--font);font-size:11px;text-transform:uppercase;letter-spacing:.5px;color:var(--text2);background:rgba(255,255,255,.02)}
.cmd-table th:first-child{border-radius:8px 0 0 0}
.cmd-table th:last-child{border-radius:0 8px 0 0}
.cmd-table tbody tr:nth-child(even) td{background:rgba(255,255,255,.005)}
.cmd-table tbody tr:hover td{background:rgba(110,193,228,.03)}
.cmd-table td code{font-family:var(--font);font-size:12px;background:rgba(255,255,255,.06);padding:1px 5px;border-radius:4px}
.cmd-table td:first-child{color:var(--text);font-weight:500}
.cmd-table-wrapper{overflow-x:auto;border:1px solid var(--border);border-radius:12px;background:var(--bg3);position:relative}
.cmd-table-wrapper::after{content:'';position:absolute;right:0;top:0;bottom:0;width:32px;background:linear-gradient(90deg,transparent,rgba(13,13,48,.6));pointer-events:none;opacity:0;transition:opacity .3s;border-radius:0 12px 12px 0}
.cmd-table-wrapper:not(.at-end)::after{opacity:1}
```

## Page Structure

### 1. Hero Section
Full-viewport hero with gradient text, animated background orbs, subtitle, badges, and auto-height for mobile.

```html
<div class="hero">
  <div class="hero-bg"><div class="orb"></div><div class="orb"></div></div>
  <h1>Title <span>Highlight</span></h1>
  <p>Subtitle / description</p>
  <div class="hero-badges">
    <span class="live">● Live</span>
    <span>Badge 2</span>
  </div>
</div>
```

**CSS for hero orbs animation:**
```css
.hero-bg .orb{position:absolute;border-radius:50%;filter:blur(80px);opacity:.15}
.hero-bg .orb:nth-child(1){width:500px;height:500px;background:var(--accent);top:-10%;left:-10%}
.hero-bg .orb:nth-child(2){width:400px;height:400px;background:var(--accent2);bottom:-5%;right:-5%}
@keyframes orbFloat{0%,100%{transform:translate(0,0) scale(1)}33%{transform:translate(30px,-40px) scale(1.1)}66%{transform:translate(-20px,20px) scale(.95)}}
```

### 2. Card Grid (Architecture / Features)
3-column responsive grid, glass-morphism cards with icons. The `grid-template-columns: repeat(auto-fit, minmax(300px, 1fr))` auto-wraps on mobile.

```html
<div class="arch-grid">
  <div class="arch-card">
    <div class="icon" style="background:rgba(108,138,255,.15)">🧠</div>
    <h3>Title</h3>
    <p>Description text</p>
  </div>
</div>
```

Card hover: `transform: translateY(-2px)` + accent border on hover.

### 3. Code Block with Copy Button

```html
<div class="code-block">
  <div class="header">
    <span class="lang">Bash</span>
    <button class="copy-btn" onclick="copyCode(this)">Copy</button>
  </div>
  <pre><span class="cmt"># comment</span>command</pre>
</div>
```

**Copy function (inline JS, no dependencies):**
```javascript
function copyCode(btn){
  const code=btn.closest('.code-block').querySelector('pre');
  navigator.clipboard.writeText(code.textContent).then(()=>{
    btn.textContent='Copied!';btn.classList.add('copied');
    setTimeout(()=>{btn.textContent='Copy';btn.classList.remove('copied')},2000);
  });
}
```

**Syntax highlighting classes** (CSS-only, no JS library):
- `.cmt` → `#5c6370` (comments)
- `.kw` → `#c678dd` (keywords)
- `.str` → `#98c379` (strings)
- `.fn` → `#61afef` (functions)
- `.num` → `#d19a66` (numbers)
- `.var` → `#e06c75` (variables)
- `.sec` → `#56b6c2` (sections)

### 4. Callout / Info Boxes

```css
.callout{padding:16px 18px;border-radius:12px;margin:16px 0;border-left:3px solid;font-size:14px}
.callout.info{background:rgba(108,138,255,.08);border-color:var(--accent)}
.callout.warn{background:rgba(251,191,36,.08);border-color:var(--orange)}
.callout.success{background:rgba(52,211,153,.08);border-color:var(--green)}
.callout.err{background:rgba(248,113,113,.08);border-color:var(--red)}
```

### 5. Phase / Progress Track

```html
<div class="phase-track">
  <span class="phase-dot active">1. Current</span>
  <span class="phase-dot">2. Next</span>
  <span class="phase-dot done">3. Done</span>
</div>
```

```css
.phase-dot.active{background:rgba(108,138,255,.12);border-color:var(--accent);color:var(--accent)}
.phase-dot.done{background:rgba(52,211,153,.1);border-color:var(--green);color:var(--green)}
```

### 6. Accordion (Troubleshooting)

```html
<details class="trouble-item">
  <summary>Problem title</summary>
  <div class="content">Fix description with code: <code>command</code></div>
</details>
```

```css
.trouble-item{border:1px solid var(--border);border-radius:12px;margin:12px 0;overflow:hidden}
.trouble-item summary{padding:14px 18px;cursor:pointer;font-weight:600;font-size:14px}
.trouble-item summary:hover{background:rgba(255,255,255,.02)}
```

### 7. Command Table

```html
<table class="cmd-table">
  <tr><th>Component</th><th>Recommended</th><th>Minimum</th></tr>
  <tr><td>RAM</td><td>64 GB</td><td>32 GB</td></tr>
</table>
```

```css
.cmd-table{width:100%;border-collapse:collapse;font-size:13px}
.cmd-table th,.cmd-table td{padding:10px 12px;text-align:left;border-bottom:1px solid var(--border)}
.cmd-table th{font-family:var(--font);font-size:11px;text-transform:uppercase;letter-spacing:.5px;color:var(--text2)}
```

### 8. Animated Terminal Demo

```html
<div class="term-demo">
  <div class="term-bar">
    <span class="dot r"></span><span class="dot y"></span><span class="dot g"></span>
    <span class="title">Terminal</span>
  </div>
  <div class="term-body">
    <span class="prompt">$ </span>
    <span class="typing-line d1">command</span>
    <span class="cursor"></span>
  </div>
</div>
```

```css
.typing-line{overflow:hidden;white-space:nowrap;animation:typing 2s steps(40,end) forwards;display:inline-block}
.typing-line.d1{animation-delay:.3s;width:0}
@keyframes typing{to{width:100%}}
.cursor{display:inline-block;width:8px;height:16px;background:var(--text);animation:blink 1s step-end infinite;vertical-align:text-bottom}
@keyframes blink{50%{opacity:0}}
```

## Full Template (Minimum Viable Shell)

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Title</title>
<style>
  /* Paste all CSS from sections above here */
</style>
</head>
<body>
<script>
/* Paste copyCode function here */
</script>
</body>
</html>
```

## Brand Restyling Workflow

When adapting an existing deliverable to match a client's brand identity:

1. Extract the brand color palette (see `references/brand-color-extraction.md` for the Wayback Machine technique when Cloudflare blocks access)
2. Map colors to CSS variables (`--bg`, `--accent`, etc.)
3. Check if the palette matches an existing variant (e.g. **Variant B: NILT Navy** above) — many corporate sites use a similar navy + light-blue scheme
4. If custom, create a new Variant C. Update: font stack (Google Fonts link), navigation background, hero gradient, card colors, code block backgrounds, accent colors on all interactive elements
5. Keep all animations, copy buttons, and structural HTML — only change colors and typography
6. Deploy and verify: check `Content-Type: text/html` AND visual output before presenting

## Extended Design Patterns

These patterns were developed for the Hermes Local AI Guide and are now available for any technical documentation page.

### 9. Vertical Timeline (Roadmap)

Full CSS-only vertical timeline with staggered fade-in animations. Alternates cards left/right on desktop, collapses to single-column on mobile.

```html
<div class="roadmap">
  <h2>Title <span class="phase-tag">tag</span></h2>
  <p class="sub">Description</p>
  <div class="tl">
    <div class="tl-item">
      <div class="tl-card">
        <div class="tl-num hw">1</div>
        <div class="tl-icon">🖥</div>
        <h3>Step Title</h3>
        <div class="tl-meta">
          <span class="time">1 hour</span>
          <span class="cat">category</span>
          <span class="dep">depends on: step X</span>
        </div>
        <p>Description text</p>
        <div class="tl-deps"><span>Next → <code>command</code></span></div>
      </div>
    </div>
    <!-- More .tl-item entries... -->
  </div>
  <div class="tl-summary">
    <p>⏱ <strong>~3–5 hours</strong> total · 9 steps</p>
  </div>
</div>
```

**CSS for the timeline:**
```css
.tl{position:relative}
.tl::before{content:'';position:absolute;left:50%;top:0;bottom:0;width:3px;
  background:linear-gradient(180deg,var(--accent),var(--accent2) 40%,rgba(108,138,255,.2) 80%,transparent);z-index:0}
.tl-item{position:relative;display:flex;margin-bottom:32px;z-index:1;
  opacity:0;animation:tlFadeIn .6s ease-out forwards}
.tl-item:nth-child(1){animation-delay:0s}
.tl-item:nth-child(2){animation-delay:.1s}
/* ... up to 9 */
@keyframes tlFadeIn{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}
.tl-item:nth-child(odd){flex-direction:row}
.tl-item:nth-child(even){flex-direction:row-reverse}
.tl-card{width:calc(50% - 40px);background:var(--card-bg);border:1px solid var(--border);
  border-radius:16px;padding:20px 22px;position:relative}
.tl-card:hover{border-color:var(--accent);transform:translateY(-2px);
  box-shadow:0 8px 32px rgba(108,138,255,.1)}
.tl-num{position:absolute;width:36px;height:36px;border-radius:50%;
  display:flex;align-items:center;justify-content:center;font-size:14px;
  font-weight:800;font-family:var(--font);z-index:2;border:2px solid}
.tl-item:nth-child(odd) .tl-num{right:-58px;top:12px}
.tl-item:nth-child(even) .tl-num{left:-58px;top:12px}
/* Color variants for numbered dots */
.tl-num.hw{background:rgba(108,138,255,.15);border-color:var(--accent);color:var(--accent)}
.tl-num.ai{background:rgba(52,211,153,.12);border-color:var(--green);color:var(--green)}
.tl-num.net{background:rgba(248,113,113,.12);border-color:var(--red);color:var(--red)}
/* Meta badges inside cards */
.tl-meta{display:flex;flex-wrap:wrap;gap:6px;margin:6px 0 8px}
.tl-meta span{padding:2px 10px;border-radius:100px;font-size:9px;font-family:var(--font);font-weight:600;
  text-transform:uppercase}
.tl-meta .time{background:rgba(108,138,255,.1);color:var(--accent);border:1px solid rgba(108,138,255,.2)}
.tl-meta .cat{background:rgba(167,139,250,.1);color:var(--accent2);border:1px solid rgba(167,139,250,.2)}
.tl-meta .dep{background:rgba(52,211,153,.08);color:var(--green);border:1px solid rgba(52,211,153,.15)}
.tl-deps{margin-top:8px;padding-top:8px;border-top:1px solid rgba(255,255,255,.04)}
.tl-deps span{font-size:10px;color:var(--text2);font-family:var(--font)}
.tl-deps code{background:rgba(108,138,255,.08);padding:1px 6px;border-radius:4px;font-size:10px;color:var(--accent)}
.tl-summary{text-align:center;margin-top:20px;padding:24px;background:var(--card-bg);
  border:1px solid var(--border);border-radius:16px}
.tl-summary strong{color:var(--accent);font-size:18px}
/* Mobile: single column, line shifts left */
@media(max-width:768px){
  .tl::before{left:24px}
  .tl-item,.tl-item:nth-child(even){flex-direction:row!important;padding-left:56px}
  .tl-card{width:100%}
  .tl-num{left:-44px!important;right:auto!important;width:32px;height:32px;font-size:12px}
}
```

### 10. Model Comparison Table with Tags

Compact table for comparing models, hardware, or any multi-option comparison. Uses inline tag badges for scannability.

```html
<div class="model-comp">
<table>
  <thead><tr><th>Model</th><th>Size</th><th>Fits?</th><th>Speed</th></tr></thead>
  <tbody>
    <tr><td>Model A <span class="tag best">#1</span></td><td>137 GB</td><td>✓</td><td>~8 tok/s</td></tr>
    <tr><td>Model B <span class="tag good">primary</span></td><td>19 GB</td><td>✓</td><td>~35 tok/s</td></tr>
  </tbody>
</table>
</div>
```

```css
.model-comp{background:var(--card-bg);border:1px solid var(--border);border-radius:16px;
  padding:4px;overflow:hidden;margin-bottom:24px}
.model-comp table{width:100%;border-collapse:collapse;font-size:12px}
.model-comp th{font-family:var(--font);font-size:10px;text-transform:uppercase;
  letter-spacing:1px;color:var(--accent);font-weight:600;background:rgba(108,138,255,.04)}
.model-comp th,.model-comp td{padding:12px 14px;text-align:left;border-bottom:1px solid rgba(255,255,255,.04)}
.model-comp td{color:var(--text2);font-weight:400}
.model-comp td:first-child{color:var(--text);font-weight:600}
.tag{display:inline-block;padding:1px 8px;border-radius:100px;font-size:9px;font-weight:700;
  letter-spacing:.5px;text-transform:uppercase;font-family:var(--font)}
.tag.best{background:rgba(52,211,153,.15);color:var(--green);border:1px solid rgba(52,211,153,.3)}
.tag.good{background:rgba(108,138,255,.12);color:var(--accent);border:1px solid rgba(108,138,255,.2)}
.tag.ok{background:rgba(251,191,36,.1);color:var(--orange);border:1px solid rgba(251,191,36,.2)}
```

### 11. Custom Hero Badge Colors

To add a model-specific or category badge with its own color:

```html
<span class="glm">GLM 5.2 Ready</span>
```

```css
.hero-badges span.glm{border-color:var(--accent2);color:var(--accent2)}
```

Pattern: add a CSS class matching the badge's semantic category, set `border-color` + `color` to a themed variable. This keeps the standard `.live` badge untouched.

### 12. Extended Callout Colors

Beyond the standard 4 callout types, add semantic colors for model-specific or additional categories:

```css
.callout.purple{border-left-color:var(--accent2);background:rgba(167,139,250,.06)}
.callout.purple strong{color:var(--accent2)}
```

Usage: `<div class="callout purple"><strong>🧬 GLM 5.2</strong> Content here</div>`

Add as many custom callout colors as the content domain requires. Keep the `.callout strong` pattern consistent — always match the `strong` color to the border-left color.

### 13. Pitch Deck Mode (Presentation Layout)

For pitch decks, proposals, and presentation-style pages, see `references/pitch-deck-patterns.md` for the full section structure, content rules, and audience-specific guidance. Key differences from a standard guide page:

- **12-section structure** — Hero → Why → Technology → Comparison → Models → Management → Applications → Skills → Meta → Hardware → Getting Started → Footer
- **Engineering audience** — Name real models, include non-software use cases, show "skills amplify cheap models" concept
- **Variant B (NILT Navy)** or **Variant C (NILT Navy Deep)** preferred — professional corporate feel
- **Phosphor icons** instead of emojis for all card icons, callouts, highlight bars, and badges (see `references/phosphor-icons.md` for the full mapping)
- **Anti-template patterns** — apply grain texture, wave dividers, dot grid, and animated hero gradient to avoid the generic AI-generated look (see "Anti-Template Design Patterns" section)
- **Highlight bars** for key speed/control claims ("<1 second vs 10 minutes")
- **Meta section** — "This page was built by the tool itself" as proof point
- **No personal names** — use "we" / "our team" / generalized examples

## Deployment

After building your HTML deliverable, deploy it using the **`deliverable-hosting`** skill (`skill_view(name='deliverable-hosting')`).

Minimum deploy checklist:
- **File must be named `index.html`** — Netlify zip deploy serves the root filename as the site root. If you zip a file named `my-guide.html` → 404. Always copy/rename to `index.html` before zipping.
- **Include `netlify.toml`** in the zip to force `Content-Type: text/html; charset=utf-8`. Without it, Netlify may serve your HTML as `text/plain` (browser shows raw source).
- **Verify after deploy** — `curl -sI <url> | grep content-type` must return `text/html`, and `curl -s <url> | grep "<unique-text>"` must match.

See `deliverable-hosting` for the full deploy workflow (GitHub push, zip upload, tunnel fallback) and all Netlify API patterns.

## Critical Pre-Flight: Verify Output Before Claiming "Done"

**When a previous turn was interrupted (system note: "your previous turn was interrupted"), all expected tool results from that turn were discarded. You cannot assume writes, patches, or deploys from an interrupted turn took effect.**

**Verification steps before telling the user "Done":**
1. Read the file back — confirm new content exists at the expected line/section
2. Check git status — `git diff HEAD --stat` or `git log -3` to see uncommitted/new changes
3. Check the live URL — `curl -s <url> | grep "<unique-text>"` to confirm it deployed
4. Only then say "Done"

> Real example from this skill's own history: the agent described every detail of content it "added" — but `git diff HEAD --stat` showed zero changes. The previous turn had been interrupted. All work was hallucinated.

## Quality Checklist (Before Delivery)

- [ ] **Pre-flight: verify writes took effect** — read file or check git status. Interrupted turns discard all results.
- [ ] **Vision-check the rendered page** — use browser_vision or open the URL. Do NOT trust web_extract (it strips all styling).
- [ ] **Content-Type verified** — `curl -sI <url> | grep content-type` must return `text/html`. If `text/plain`, add `netlify.toml` and redeploy.
- [ ] All code blocks have copy buttons
- [ ] Responsive: test at 375px width (mobile)
- [ ] No broken links or placeholder text
- [ ] CSS is inline (no external stylesheets — standalone file)
- [ ] Dark theme is coherent (no light flash on load)
- [ ] Animations don't overwhelm content
- [ ] Code syntax highlighting classes applied
- [ ] Scroll behavior: smooth + scroll-padding-top for sticky nav

## Pitfalls

| Problem | Cause | Fix |
|---------|-------|------|
| You say "Done" but nothing was actually written | Previous turn was interrupted — tool results discarded | Read the file or check git status before claiming completion. See "Critical Pre-Flight" section above |
| User says the page is just plain text | web_extract shows content, not rendered HTML | **Always vision-check before presenting**. Add netlify.toml if Netlify serves as text/plain. See references/brand-color-extraction.md for branded restyling |
| Netlify deploy returns 404 after zip upload | Zip file contains wrong filename (e.g. `my-guide.html` instead of `index.html`) | Netlify serves the zip root file as the site root. Always name it `index.html`. Use `cp my-guide.html /tmp/deploy/index.html && cd /tmp/deploy && zip -r /tmp/deploy.zip .` to ensure correct name at root. |
| Netlify serves .html as text/plain | Netlify MIME detection fails on some .html files | Add netlify.toml with `[[headers]]` for `*.html` → `Content-Type: text/html; charset=utf-8`. Include netlify.toml in every zip deploy. Verify with `curl -sI <url> | grep content-type` |
| You say it looks great but user sees raw text | You inspected file contents, not rendered output | HTTP headers + visual check before claiming "done". Never use web_extract to judge visual quality |
| White flash on load | Browser default bg before CSS applies | Add `body{background:var(--bg)}` in first `<style>` block |
| Copy button copies wrong text | The button selects wrong `.code-block` parent | Use `btn.closest('.code-block')` not `btn.parentElement` |
| Table overflows on mobile | No scroll wrapper | Wrap tables in `<div class="cmd-table-wrapper" style="overflow-x:auto">` |
| Code block too wide | Long lines without wrapping | `pre{overflow-x:auto}` (don't use word-wrap — breaks copyable commands) |
| Zero-width orbs on hero | Orbs have no width/height without CSS | Always set explicit `width` + `height` on `.hero-bg .orb` |
| Mobile nav toggle does nothing | Inline `onclick` + `addEventListener` both wired — they fire sequentially, toggling class twice (net: nothing) | Remove inline `onclick`. Use only `addEventListener` in a clean IIFE. Add click-outside-to-close. See `references/pitch-deck-patterns.md` → "Nav Toggle Pitfall" for the correct pattern. |
| Missing `.` on class selector in `@media` block — e.g. `hero{` instead of `.hero{` | Cut-paste error during refactoring. CSS parser silently ignores the invalid selector; style never applies. | Always grep for bare class names after editing: `pattern="\b(hero|nav|section|footer)\{"` across the file. If any hit has no `.` / `#` / element prefix before it, it's a bug. |
| Table wrapper divs exist in HTML but no CSS rule — `.cmd-table-wrapper` used in markup, no styling block | Wrapper divs added ad-hoc during content iteration, CSS block never wired up | Add `overflow-x:auto;margin:16px 0` (NOT `overflow:hidden` — that clips, doesn't scroll). Also add mobile font-size reduction inside the `@media` block. |
| `scroll-padding-top` doesn't match real nav height | Nav height changed (e.g. 80px → 60px) during restyle, but the scroll offset was never updated. Anchors land behind the sticky nav. | After any nav height change, verify with `grep scroll-padding-top` and `grep "nav.{.*height"`. The scroll padding should be nav height + 8px buffer. |
| Footer badge not actually removed — you patched it locally but the deployed page still shows it | Multiple git branches / sessions editing the same file. Your local fix didn't survive a rebase, or the Netlify deploy picked up a stale build. | After any badge/claim removal: (1) `curl -s <url> | grep <removed-text>` must return 0 matches, (2) use browser to verify visually, (3) check deploy state via Netlify API if using manual deploys. |
| Deploy triggered from GitHub but builds stale — git-push auto-deploy not wired | Netlify site created via manual upload, never connected to the GitHub repo | Use manual zip deploy as escape hatch: `zip -r - . -x '.git/*' | curl .../deploys`. Or connect the site to the repo in Netlify dashboard. |
| Browser tools unavailable — no CDP endpoint running | Chromium/Chrome not installed on the server, or no headless instance left running | Install: `sudo apt install chromium-browser`. Start: `terminal(background=true, command="chromium-browser --headless --disable-gpu --remote-debugging-port=9222 --no-sandbox about:blank")`. Verify: `curl -s http://127.0.0.1:9222/json/version`. |
| Password login page POST fails with `{"detail":"Method Not Allowed"}` after tunnel deploy | Login form `action="/"` posts to domain root, which is not caught by the tunnel ingress rule for `/path*` | Set form `action="/path"` to match the tunnel ingress path prefix. E.g. if tunnel serves `/pitch-deck*` → form `action="/pitch-deck"`. The tunnel rule only matches paths starting with the configured prefix. |
| Table rows don't alternate color | CSS uses `nth-child(even)` but table has no `<tbody>` wrapper (vanilla HTML tables without `<tbody>` still work in DOM, but `nth-child` counts from `<table>` directly) | Wrap table rows in `<tbody>...</tbody>`. CSS `nth-child(even)` counts `<tr>` children, so it needs a stable parent. Browsers auto-insert `<tbody>` in DOM even if omitted in HTML, but the selector behavior can be unpredictable — always write it explicitly. |
