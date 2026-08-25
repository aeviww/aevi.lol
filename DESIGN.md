# elytrya.icu — design notes

## The world: "field manual"

A printed technical manual / studio ledger rather than a dark developer template.
Warm paper, black ink, one signal colour, and a strict split of voices:

- **serif** (Georgia stack) — the human voice: headlines, lede, prose, project names
- **monospace** — the apparatus: labels, section numbers, table columns, meta, keys

The page reads top to bottom as numbered sections of a document
(`01 intro`, `02 toolkit`, `03 work`, `04 about`, `05 contact`), not as a stack of
identical cards.

## Non-negotiables

| Decision | Reason |
| --- | --- |
| No webfonts | Georgia + system mono are everywhere, cost 0 kb and never flash. |
| Two families, two weights | The voice split does the work, not a type zoo. |
| `--radius: 0.125rem` | Print corners. Nothing looks like a default UI kit card. |
| One accent (`--brand`, vermilion) | Signal only: hovers, one italic word, the arrows. |
| Alternating bands | Rhythm comes from paper tone changes, not from divider lines. |
| Grain overlay on `.shell` | Kills the flat-screen look; 240-byte inline SVG. |
| No global `* { transition }` | Motion is authored per element, or it isn't motion. |

## Anti-references (what the previous version did)

- every section: `max-w-[760px]` + identical padding + identical mono eyebrow
- four gradient hairline dividers doing the job of layout
- pill chips (`rounded-full border bg-card/40`) for the stack
- one hover treatment reused everywhere (`-translate-y-0.5` + brand border)
- fade-up reveal on literally every block

All five are gone. The signature moves now are: the spec sheet in the hero, the
three-column stack table, the numbered project index with a tint sweep, the
ledger numerals in *about*, and the inverted ink band for contact.

## Type scale

- display `clamp(40px, 7vw, 82px)` serif, `-0.03em`, italic accent word in brand
- page title `clamp(34px, 5vw, 58px)`
- section title `clamp(22px, 2.4vw, 30px)` with a mono number and a rule
- body 17px / 1.62–1.68, measure capped at 52–64ch
- apparatus 10.5–12px mono, `letter-spacing: 0.12–0.18em`, uppercase

## Layout

- `--measure: 1180px`, `--gutter: clamp(20px, 4.2vw, 56px)`, `.wrap-narrow: 820px`
- hero: asymmetric `1.35fr / 0.85fr` — copy left, spec sheet right
- toolkit: real `<table>`, three columns (tool / used for / since)
- work: index rows `num | name + desc | lang · stars | arrow`
- about: prose + ledger; contact: statement + links, inverted
- one breakpoint at 960px (collapse asymmetry), one at 720px (single column)

## Colour

| Token | Light | Dark |
| --- | --- | --- |
| background | `40 24% 94%` paper | `28 8% 8%` |
| foreground | `26 12% 12%` ink | `40 16% 91%` |
| brand | `14 84% 44%` vermilion | `18 88% 58%` |
| band (contact) | `26 14% 10%` | `28 8% 12%` |

Body text and all mono labels are checked against their own band for WCAG AA;
the brand colour is used on paper only where it clears 4.5:1, and as a hover /
border / underline signal elsewhere.

## Motion

- `rise` on hero entrance (staggered 60ms), `reveal` on scroll for lists only
- hovers: tint sweep + 12px indent on rows, arrow nudge, underline in brand
- easter eggs kept: portrait squish, self-link shake + confetti, konami CRT mode
- everything inside `@media (prefers-reduced-motion: reduce)` collapses to none
