# Design: Школа КАЙФа (bekaif, тестовая копия)

The locked system. Every Hallmark run reads this first and pages share it. Change it on purpose; the file is the rule.

## System
- Genre: editorial
- Shape of the first page: Manifesto (school home); each page names its own shape in its stamp
- Theme: brand, from «Визуальный стандарт Ани Громовой» 10.10.2026 (песок 60, гранат 25, графит 10, латунь 5)
- Axes: light/display-heavy/chromatic-garnet · posture: committed (garnet field for bands and covers)

## Tokens
`tokens.css` is the source of truth. The roles:
```css
:root {
  --color-paper: oklch(93.4% 0.020 65);  --color-paper-2: oklch(97% 0.013 71);  --color-paper-3: oklch(89.9% 0.027 69);
  --color-ink: oklch(24.5% 0.008 31);  --color-ink-2: oklch(38.1% 0.015 37);  --color-muted: oklch(46.5% 0.016 32);  --color-rule: oklch(83% 0.032 67);
  --color-accent: oklch(42.5% 0.142 10);  --color-accent-ink: oklch(93.4% 0.020 65);  --color-focus: oklch(46.4% 0.175 12);
  --color-field: oklch(42.5% 0.142 10);  --color-night: oklch(17.8% 0.007 34);  --color-brass: oklch(52% 0.094 72);  --color-brass-light: oklch(79.5% 0.098 77);
  --font-display: "Unbounded", "Montserrat", sans-serif;  --font-body: "Golos Text", system-ui, sans-serif;  --font-outlier: "PT Mono", monospace;
  --radius-card: 20px;  --radius-input: 12px;  --radius-pill: 999px;  --rule-hair: 1px;  --shadow-card: none;
}
```
The spacing scale, the type scale, the easings and the durations are the scaffold's and live in `tokens.css`; the display steps sit one step down because Unbounded is a wide face.

## Type
- Unbounded 700 for every head, one colour per level (h2 garnet on sand, sand on garnet or night). Heads of one to three words may be set in capitals (`.caps`), never tracked, line-height 1.04 or more.
- Golos Text 400 and 500 for everything else, labels included, sentence case.
- PT Mono only for figures: prices, dates, counts, step numbers.
- Google Fonts with the cyrillic subset; three weights in running use (400, 500, 700).

## Controls
- Primary: garnet fill, sand text, 12px radius, 52px tall
- Secondary: outline in `--color-rule-2`, same radius and height; on garnet or night the primary inverts to a sand plate

## Surfaces
- Bands climb different rungs: whitespace, a hairline, the plate (`--color-paper-2`), the deep sand (`--color-paper-3`), the garnet field, the night footer. Never a bordered box in a well, never a card in a card, no shadows.
- Brass is one detail a screen at most (on sand only `--color-brass`, on garnet or night only `--color-brass-light`).

## Motion
- Character: calm; one reveal a page from visible, scoped under `.js`; under reduced motion everything ends at once.

## Chrome
- Nav: edge-aligned, the wordmark «Школа КАЙФа» with «Анны Громовой», the page's own anchors, no button.
- Footer: mast on night ground, the wordmark large over contacts and documents, the legal line beneath.

## House waivers
These recur by design and are inherited, not re-argued page by page:
- 49b: the legal names of the documents and the /efir/ chapter titles may wrap to two lines at 320px (waived once in `site.css`).
- Link pages (`link.html`, `love.html`) are one 30-36rem column read on a phone: payment tiles taller than 52px (39b), a hero shorter than the screen (44c, 79) and hairlines instead of section gaps (59).
- Legal documents keep their clause heads small (78, waived in `legal.css`); their body text is never edited, only set.

## Exports
`tokens.css`, `base.css`, `site.css` and `legal.css` (the Long Document layer for the legal pages and contacts) in this folder. Tailwind, DTCG or shadcn blocks are added here on request, per `export-formats.md`.
