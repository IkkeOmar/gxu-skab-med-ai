---
name: html-interactive-games
version: 1.1.0
category: development
description: Build complete standalone interactive HTML files — games, showcases, and informational pages — as single self-contained files with no dependencies. Covers game mechanics, multi-player flows, timeline/scroll animations, interactive card UIs, terminal simulators, and copy-button command blocks.
tags: [development, html, frontend, javascript, ui, animations, interactive, single-page]
related_skills: [ui-floating-primitives, video-technical-analysis]
---

# Standalone Interactive HTML Games

Build complete, self-contained interactive games as single `.html` files that work offline, require zero dependencies, and persist state across page reloads via `localStorage`. Designed for in-person group play (party games, quiz games, board games).

**Related: `ui-floating-primitives`** — when building game overlays (clue popups, modals, context menus) that need to stay on-screen regardless of viewport, load that skill for Floating UI collision detection patterns. For single-file mode, embed `@floating-ui/dom` via CDN.

## When to use

- User asks for a game, quiz, or multiplayer tool to play with friends
- User asks for a "standalone HTML file" or "just build it"
- User asks for an interactive showcase, landing page, or informational page as a single HTML file
- You need a single-page experience with no server, no framework, no install
- The page needs to work offline or be shareable as a single file
- The experience should involve scroll animations, interactive cards, click-to-expand, terminal simulators, or command blocks with copy buttons

## Core principles

### 1. Everything in one file

- All HTML, CSS, and JS in a single `.html` file
- No external CDNs, no npm, no build step
- The user opens it in a browser and plays immediately
- Use CSS custom properties (`:root`) for theming — easy to tweak colors

### 2. Generate all content yourself

**CRITICAL PREFERENCE:** When building a game that needs questions, prompts, categories, or any content — **make it up yourself**. Do NOT leave blanks, placeholders, or ask the user to fill in content. The user wants to play, not write game content. If you need 30 quiz questions, write all 30.

### 3. localStorage for session memory

```javascript
function save() { localStorage.setItem('game_state', JSON.stringify(state)); }
function load() { return JSON.parse(localStorage.getItem('game_state')); }
```

- Save on every state transition (buzz in, correct answer, new clue, etc.)
- Restore on page load in `DOMContentLoaded`
- The game should seamlessly resume after page refresh

### 4. No external dependencies

- No CDN scripts, no font imports, no icon libraries
- Use system UI font stack: `system-ui, -apple-system, sans-serif`
- Inline all icons as Unicode characters or CSS shapes — never external icon sets

## Standard game architecture

### Setup phase
- **Dynamic player count:** Dropdown/select (2-5) that generates the right number of name inputs via JS
  ```javascript
  function updatePlayerInputs(){
    const n=parseInt(document.getElementById('playerCount').value);
    const defaults=['Omar','Ali','Mikkel','Sofie','Lars'];  // match your group
    const container=document.getElementById('playerInputs');
    container.innerHTML='';
    for(let i=1;i<=n;i++){
      const inp=document.createElement('input');
      inp.id='p'+i+'name';
      inp.placeholder='Spiller '+i;
      inp.value=defaults[i-1]||'Spiller '+i;
      container.appendChild(inp);
    }
  }
  ```
- Player name inputs (pre-fill with defaults)
- Start button reads `playerCount` then loops `1..n` to collect names → initializes state → renders board
- A "Nulstil" (reset) button to wipe localStorage and restart
- **Everything adapts to player count:** score chips, buzz buttons, keyboard shortcuts (1-N instead of hardcoded 1-5), Final Jeopardy wager/answer rows

### Game state (single object)
```javascript
const game = {
  players: [{ name, score, color, id }],
  boardState: [{ category, clues: [{ clue, answer, value, used, isDD }] }],
  phase: 'board' | 'clue' | 'answer' | 'final',
  activeClue: null,
  buzzer: null,         // who buzzed (player index)
  failedBuzzers: [],    // who already got it wrong (for re-open)
  usedCount: 0,
  // Final Jeopardy
  finalWagers: [],
  finalAnswers: [],
  finalLocked: false,
};
```

### Board rendering
- `display: grid` for the game board (categories × values)
- Category headers with gradient backgrounds
- Clickable value cells that grey out when used
- Score row showing each player's current total

### Clue flow (Jeopardy-style)
1. Player clicks a value → clue appears in overlay
2. **Buzz phase:** Each player has a dedicated buzz button (plus keyboard shortcuts 1-5)
3. First buzz → winner gets control
4. **Answer phase:** Show the correct answer, let the buzzed player judge correct/wrong
5. **Wrong answer:** Re-open buzzers for remaining players
6. Mark clue as used → return to board

### Special features
- **Daily Double:** Randomly assigned to 2 clues (value 400-800). Winner wagers points before answering. Min: clue value. Max: their current score.
- **Final Jeopardy:** Triggers when all clues are used. All players wager, write answers, then simultaneous reveal.
- **Keyboard shortcuts:** 1-N for buzzing (matches player order), range adapts to player count. Guard with `pi < game.players.length` to prevent out-of-range keys.

### Winner screen
- Sort players by score descending
- Show full ranking with scores
- "Nyt spil" button to restart

## UI design patterns for party games

### Color system
```css
:root {
  --bg: #0a0e1a;        /* Deep space dark */
  --board-bg: #0d1230;   /* Slightly lighter */
  --card-bg: #151d4a;    /* Card/panel background */
  --gold: #ffd700;       /* Primary accent */
  --cyan: #00e5ff;       /* Secondary accent */
  --purple: #7c3aed;     /* Tertiary accent */
  --text: #e2e8f0;       /* Body text */
  --dim: #64748b;        /* Muted text */
}
```

### Player color coding (for 5 players)
```javascript
const playerColors = ['#ff6b6b', '#ffd93d', '#6bcb77', '#4d96ff', '#ff6bff'];
```
Each player gets a consistent color used across: score chip, buzz button, indicator dot.

### Key UI patterns
- **Overlay/modal** for clues, answers, and game phases — uses `position: fixed; inset: 0`
- **Gradient buttons** for primary actions (`background: linear-gradient(135deg, ...)`)
- **Used cells** get low opacity + deactivated pointer events
- **Responsive** — switch `grid-template-columns` at breakpoints (3-col at 768px, 2-col at 480px)
- **Buzz buttons** highlight winner (gold background + scale) and dim losers

### Animation principles
- Subtle hover scale on clickable elements (1.03-1.05)
- Pulse animation for Daily Double badge
- No jank — use `transform`/`opacity` only, not layout-triggering properties

## Showcase/Informational Page Architecture

For non-game pages — product showcases, documentation landing pages, feature explorers — use a different structure while keeping the same single-file, zero-dep principles.

### Common sections (scroll-based layout)
```
┌─────────────────────────────────────┐
│  Hero Section                       │
│  - Animated gradient/glow bg       │
│  - Title + subtitle + CTAs         │
│  - Terminal mockup or demo widget  │
├─────────────────────────────────────┤
│  Core Philosophy (3-6 cards)        │
│  - Grid of benefit cards           │
│  - Hover effects + icons           │
├─────────────────────────────────────┤
│  Deep Dive (numbered reasons)       │
│  - Vertical list with numbers      │
│  - Comparison table (optional)      │
├─────────────────────────────────────┤
│  Features (click-to-expand cards)   │
│  - Grid of expandable cards        │
│  - Click toggles detail section    │
├─────────────────────────────────────┤
│  Architecture Diagram               │
│  - Visual node/flow representation  │
│  - CSS-only (no SVG/canvas needed)  │
├─────────────────────────────────────┤
│  Get Started (command blocks)       │
│  - Code blocks with copy buttons   │
│  - Sequential steps                │
├─────────────────────────────────────┤
│  Footer                             │
└─────────────────────────────────────┘
```

### Key UI patterns for showcases

**1. Scroll-triggered reveal animations**
```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
    }
  });
}, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });
document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
```
CSS:
```css
.reveal { opacity: 0; transform: translateY(30px); transition: opacity 0.7s ease, transform 0.7s ease; }
.reveal.visible { opacity: 1; transform: translateY(0); }
.reveal-delay-1 { transition-delay: 0.1s; }
.reveal-delay-2 { transition-delay: 0.2s; }
```

**2. Terminal mockup**
```
┌──────────────────────────┐
│ ● ● ●   hermes — zsh   │
├──────────────────────────┤
│ $ hermes install         │
│ ✓ Hermes installed in 12s│
│ $                        │
│          █ (blinking cursor)
└──────────────────────────┘
```
Use CSS-only terminal dots (3 colored circles), a monospace font (JetBrains Mono via Google Fonts or system fallback), and a blinking cursor animation.

**3. Click-to-expand cards**
```html
<div class="feature-card" onclick="this.classList.toggle('active')">
  <div class="feature-preview">Icon + Title + Short description</div>
  <div class="feature-detail">Expanded content: bullet list, details, code</div>
</div>
```
```css
.feature-detail {
  max-height: 0; overflow: hidden;
  transition: max-height 0.5s ease, padding 0.4s ease;
}
.feature-card.active .feature-detail {
  max-height: 300px; padding: 20px 28px;
}
```

**4. Command blocks with copy buttons**
```html
<div class="cmd-block">
  <div class="cmd-block-header">
    <span class="cmd-label">1. Install</span>
    <button class="cmd-copy" onclick="copyCmd(this, 'pip install hermes-agent')">Copy</button>
  </div>
  <code>pip install hermes-agent</code>
</div>
```
```javascript
function copyCmd(btn, text) {
  navigator.clipboard.writeText(text).then(() => {
    btn.textContent = 'Copied!';
    btn.style.color = '#27c93f';
    setTimeout(() => { btn.textContent = 'Copy'; btn.style.color = ''; }, 2000);
  });
}
```

**5. Architecture flow diagram (CSS nodes)**
Use flexbox rows with styled `div` nodes and arrow characters (→, ↓, ↔):
```html
<div class="arch-row">
  <div class="arch-node cyan featured">Core</div>
  <span class="arch-arrow">↔</span>
  <div class="arch-node purple">Provider</div>
</div>
<div class="arch-arrow">↓</div>
<div class="arch-row">
  <div class="arch-node gold">Memory</div>
  <div class="arch-node gold">Skills</div>
</div>
```

**6. Comparison table**
A semantic `<table>` with check/cross marks. On Telegram, Telegram has no table support so use labeled key:value pairs instead. In HTML, use proper `<table>` with `<thead>`/`<tbody>`.

**7. Animated background elements**
- CSS grid overlay for a subtle tech-grid effect
- Floating glow orbs with `filter: blur(120px)` and `animation: glowDrift`
- Generated star particles via JS (create divs with random positions/sizes/durations)

### When to use intersection observer vs click-to-expand
- **Intersection Observer:** For scroll-triggered reveals on page load. Content appears as user scrolls down. Best for sections that should animate in once.
- **Click-to-expand:** For interactive detail disclosure. Content is always in the DOM but hidden behind `max-height: 0`. Best for feature cards where the user chooses to read more.
- Do NOT use both on the same element — they fight.

### Font strategy
- Use `@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300..900&family=JetBrains+Mono:wght@400;500;700&display=swap')` for Google Fonts
- Fallback: `system-ui, -apple-system, sans-serif` for body, `'JetBrains Mono', monospace` for code
- Google Fonts import is the ONE acceptable external dependency for showcase pages (it dramatically improves appearance)

```
┌─────────────────────────────────────┐
│  Setup Screen                       │
│  [Player 1] [Player 2]  ...         │
│  [▶ Start Game]                     │
├─────────────────────────────────────┤
│  Game Board                         │
│  ┌─────┬─────┬─────┬─────┬─────┐   │
│  │ Cat 1│Cat 2│Cat 3│Cat 4│Cat 5│   │
│  ├─────┼─────┼─────┼─────┼─────┤   │
│  │$200 │$200 │$200 │$200 │$200 │   │
│  │$400 │$400 │$400 │$400 │$400 │   │
│  │...  │...  │...  │...  │...  │   │
│  └─────┴─────┴─────┴─────┴─────┘   │
├─────────────────────────────────────┤
│  Clue Overlay                       │
│  [Clue text]                        │
│  [Buzz buttons: P1 P2 P3 P4 P5]   │
│  [✅ Correct / ❌ Wrong]            │
└─────────────────────────────────────┘
```

## Testing checklist

**PRE-DELIVERY HARD CHECK (always run these before telling the user the file is ready):**
- [ ] `wc -l <file>` → expect 300+ lines for showcase, 600+ for game
- [ ] `wc -c <file>` → expect 15KB+ (empty stubs are ~2KB)
- [ ] `head -3 <file>` → expect `<!DOCTYPE html>` + `<html lang=`
- [ ] `tail -3 <file>` → expect `</script>\n\n</body>\n</html>`
- [ ] Visually scan output: hero section present, at least 3 content sections, no placeholder text
- [ ] If any check fails → file is incomplete/stub — rebuild fully

Before delivering, verify every flow:

- [ ] Setup → enter names → Start works
- [ ] Dynamic player count dropdown shows correct inputs (try 2, 3, 5)
- [ ] Board renders with correct categories and values
- [ ] Click a clue → overlay opens with clue text
- [ ] Buzz buttons appear and are clickable
- [ ] Buzz winner gets highlighted, losers dim
- [ ] Correct answer → points added → cell greys out
- [ ] Wrong answer → buzzers re-open for remaining players
- [ ] Daily Double triggers wager prompt
- [ ] Wager limits enforced (min=clue value, max=player score)
- [ ] All 30 clues used → Final Jeopardy triggers
- [ ] Final Jeopardy: wager → answer → reveal works
- [ ] Winner screen shows correct ranking
- [ ] Page refresh preserves game state (localStorage)
- [ ] "Nyt spil" resets everything
- [ ] Keyboard shortcuts (1-5) work for buzzing
- [ ] Responsive at 768px and 480px breakpoints

## Pitfalls

| Pitfall | Solution |
|---------|----------|
| Leaving content blank/placeholder | Generate all questions, answers, and categories yourself. Never ask the user to fill in game content. |
| Timer/realtime sync for local play | Don't implement real-time networking. Local (one-screen) games use "honor system" buzzer — first click wins. |
| Daily Double wager can exceed score | Cap wager input max at `Math.max(player.score, clueValue)` |
| Final Jeopardy with 0-score players | Allow $0 wager. The input min should be 0. |
| Empty cell removal breaks layout | Don't remove used cells — just mark them `used` with CSS styling so the grid doesn't reflow. |
| CSS grid gap on mobile | Use smaller gap (4px) at narrow widths to fit the board. |
| localStorage over 5 MB limit | State objects for games are tiny (~2-5 KB). No concern. |
| Event listeners on used cells | Remove `onclick` or check `if (clue.used) return` at top of handler. |
| Declaring delivery without verifying file content | **CRITICAL — before every delivery:** run `wc -l <file>` (expect 300+ lines for a showcase page, 600+ for a game) and `wc -c <file>` (expect 15KB+). Visually confirm the file opens complete — check the hero section, at least 3 content sections, and the closing `</html>` tag exist. Run `head -3` and `tail -3` on the file. If any of these checks fail, the file is incomplete — rebuild it. Never trust that you "wrote it correctly" — the write might have been truncated, the content might have been stubs, or the tool output might have been fabricated. This pitfall exists because a showcase page was shipped with only a caption and code snippet, wasting the user's time. |

## Example reference

See `references/jeopardy-gaming-sports.md` for a complete 30-clue Jeopardy game with gaming + sports categories, 5-player buzzer system, Daily Doubles, and Final Jeopardy — the full source used as this skill's test fixture.
