# CLAUDE.md

Project guidance for Claude Code working in this repository.

## What this is

The personal academic website for **Abigail Fuesler**, Ph.D. student in Forest
and Conservation Sciences at the University of Montana, researching recreation
allocation on public lands.

It is a **single self-contained static page**: `index.html` holds all markup,
CSS, and JavaScript. There is no build step, no framework, no package manager,
no dependencies. Deployed via GitHub Pages at **abigailfuesler.com**.

The audience is search committees, academic collaborators, and agency partners
(USDA Forest Service, NPS). The page has one job: make a reader immediately
understand who she is and what she studies, and remember it a week later.

## Hard rules

These are not preferences. Do not violate them without asking first.

1. **Keep it one file.** Do not split into partials, add a bundler, introduce a
   framework, or add npm dependencies. No build step. If a change seems to
   require tooling, stop and ask.
2. **Do not remove or redesign the permit motif.** The masthead identity block
   is styled as a backcountry use permit. It is the conceptual signature of the
   site and it ties directly to her research subject (who gets the permit). It
   is not decoration.
3. **Do not restructure the CSS.** No conversion to Tailwind, no utility
   classes, no reorganizing the token system. Edit values in place.
4. **Never use em-dashes** in any content, comment, or commit message. Use
   commas, colons, or a rewritten sentence.
5. **Do not invent facts.** Publications, titles, coauthors, venues, dates, and
   links are drawn from her verified record. Never add, reword, or "improve" a
   citation. If something looks wrong or incomplete, flag it, do not fix it.
6. **Content lives in the data arrays**, at the bottom of `index.html` under
   `EDIT YOUR CONTENT HERE`: `PUBLICATIONS`, `GALLERY`, `NEWS`. Add or change
   entries there, never by hand-writing markup into the sections.
7. **Preserve the plain-language comments.** The header comment block and the
   inline instructions exist so Abi can update the site herself without knowing
   code. Keep them accurate when behavior changes.

## Design system

Do not introduce colors, fonts, or effects outside this system.

### Palette (CSS custom properties in `:root`)

| Token       | Hex       | Use                                  |
|-------------|-----------|--------------------------------------|
| `--ink`     | `#17160F` | Masthead and footer bands, body text |
| `--paper`   | `#ECE5D2` | Page background, manila field stock  |
| `--paper-2` | `#E4DBC3` | Recessed panels and cards            |
| `--brown`   | `#463726` | Routed Forest Service sign brown     |
| `--pine`    | `#2F4034` | Deep forest green                    |
| `--gold`    | `#B47E2B` | The single accent. Use sparingly.    |
| `--cream`   | `#F5F0E1` | Type on dark bands                   |
| `--line`    | `#C9BE9F` | Hairline rules on paper              |
| `--muted`   | `#6B6047` | Secondary text                       |

`--gold` is the only accent color. If gold starts appearing in more than a few
places per screen, it has stopped being an accent. Pull it back.

### Type

- **Archivo** (`--font-display`), weights 700 to 900: name, section headings,
  nav mark. Signage weight, tight tracking.
- **Source Serif 4** (`--font-serif`): body copy, publication titles, tagline.
- **Space Mono** (`--font-mono`): eyebrows, labels, permit block, captions,
  metadata. Always uppercase with wide letter-spacing in these roles.

Three families is the ceiling. Do not add a fourth.

### Visual language

National park brochure bands crossed with a routed wooden trail sign. Reference
points: NPS Unigrid, USFS signage, field notebooks, topographic maps. Warm and
printed, not glassy or techy.

## Motion

Deliberately minimal. Exactly two effects exist:

1. Topographic contour lines draw in once on page load.
2. Sections fade up once on scroll, via `IntersectionObserver` and `.reveal`.

**Do not add more animation.** No parallax, no hover-lift on cards, no counters,
no typewriter effects, no gradient shifts, no scroll-linked scaling. Excess
motion is the clearest tell of a generated site and the fastest way to make this
look unserious to an academic audience. `prefers-reduced-motion` must keep
working.

## Quality floor

Every change must hold these:

- Responsive to 360px wide with no horizontal scroll
- Visible keyboard focus (`:focus-visible`, gold outline) on all interactive elements
- `prefers-reduced-motion: reduce` disables both animations
- Semantic headings in order, no skipped levels
- Real `alt` text on every image
- Works with JavaScript disabled for core content where reasonable
- Passes WCAG AA contrast on all text

## Image fallbacks

Portraits and gallery plates use `onerror` handlers that swap in designed
placeholders when a photo file is missing. This is intentional so the site never
looks broken before the real photos land. Keep the fallbacks working when
touching image markup.

## Commits

Small, scoped, descriptive. One concern per commit. Present tense, sentence
case, no em-dashes.

Good: `Tighten masthead spacing on mobile`
Bad: `updates`

## When in doubt

Prefer restraint. The site is meant to feel edited, not maximal. Chanel's rule
applies: before shipping, take one thing off. If a change would make the page
louder rather than clearer, do not make it, and say why.
