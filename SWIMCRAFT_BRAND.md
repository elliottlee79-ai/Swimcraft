# Swimcraft — brand & style guide (v1)

**Updated:** 18 Aug 2026 (54th session) · **Owner:** Harbledown Digital

> ⚠ **THE OWNER LINE ABOVE WAS CORRECTED ON 18 AUGUST 2026 AND THE ERROR IS RECORDED
> RATHER THAN TIDIED AWAY (rule 28).** It had read "Ltd" since 1 July. The business is
> **Elliott Lee, a sole trader trading as Harbledown Digital** — which is what terms.html,
> privacy.html and the whole OSA pack have always said. CONTEXT recorded this document as
> the odd one out at the 48th and 49th sessions and it stayed wrong for six more.
> ⚠ **AND IT WAS NOT THE ONLY HOME.** `package.json` carried "Ltd" twice — in `author`
> and in `build.copyright`, the second of which is stamped into the packaged .exe's file
> properties, so it was a legal claim shipping inside every build. Both corrected in the
> same delivery. **Found by reading package.json for an unrelated reason**, which is the
> argument for sweeping every home of a fact at once rather than the one you tripped over.
**Purpose:** the single source of truth for Swimcraft's colours, type, and wordmark —
shared by the **game** (App.jsx + components) and the **website**
(swimcraft.harbledowndigital.com) and any Steam art. When a value changes, change it
**here first**, then in the one place each surface reads it from (see §5). Keep the
changelog (§6) current so the two surfaces never drift.

---

## 1. Brand in one line
Your **swim**, **crafted.** The two-tone wordmark encodes the product: *swim* (the
angler's water — bone) + *craft* (the making — olive). It ties straight to the
photo-to-venue hook.

---

## 2. Colours (locked)

Hex is the source of truth. In the game these map to CSS variables in `index.css`;
the website should use the **same hex** (ideally the same variable names).

### Brand core
| Name | Hex | Token | Role |
|---|---|---|---|
| **Swim Bone** | `#E6DCC6` | `--brand-bone` | Wordmark "swim"; light display text on dark grounds |
| **Craft Olive** | `#4E6B30` | `--brand-olive` | Wordmark "craft"; primary brand green |
| **Ink** | `#10150D` | `--ink` | The wordmark's ground; darkest surface |

### Supporting palette (from index.css — the live values; carry the same hex to the web)
| Name | Hex | Token | Role |
|---|---|---|---|
| Gold | `#C9A84C` | `--gold` | Values, highlights, key numbers |
| Gold Light | `#F0D080` | `--gold-light` | Emphasis / brighter gold |
| Accent Sage | `#8FAA6B` | `--accent` | UI accent green (buttons, active) |
| Text | `#E8F0E0` | `--text` | Body / UI text |
| Muted | `#8AA880` | `--muted` | Secondary text |
| Deep | `#1A1F14` | `--deep` | App background (darkest surface) |
| Mid | `#2A3420` | `--mid` | Raised surface / modal ground |
| Surface | `#344A28` | `--surface` | Panel surface |
| Water 1 | `#3A5A48` | `--water1` | Water tone |
| Water 2 | `#4A7A6D` | `--water2` | Water tone (lighter) |
| Card bg | `rgba(26,31,20,0.85)` | `--card-bg` | Card background |
| Border | `rgba(143,170,107,0.25)` | `--border` | Hairline border |

> Note: **Ink `#10150D`** (the wordmark ground) is a touch darker than the app
> background `--deep #1A1F14` — both are intentional and both are now tokens.

### Contrast note (important for the website)
The bone/olive wordmark is designed for the **dark Ink ground**. On a **light**
background, "swim" in bone nearly disappears — so keep the logo on a dark surface
wherever possible (game HUD, website hero panel, Steam capsule). For unavoidable
light-bg use, swap "swim" to `--ink` (or `--deep`) and keep "craft" olive — that's
the **light-ground lockup** (see §4).

---

## 3. Typography — fonts as swappable tokens

The whole point: **one token per font role**, so a font swap is a one-line change
that percolates everywhere. Today the game hardcodes three families inline in ~29
places — the wiring step (§5) replaces those with the tokens below.

| Token | Font (current) | Fallback stack | Used for |
|---|---|---|---|
| `--font-brand` | **Alfa Slab One** | `'Bitter', Georgia, serif` | Wordmark, hero/display titles |
| `--font-display` | **Bitter** | `Georgia, 'Times New Roman', serif` | Headings / section titles |
| `--font-ui` | **Bitter** (400/500/600/700) | `Georgia, serif` | UI, body, labels, buttons |
| `--font-editorial` | Bitter | `Georgia, serif` | Long-form / editorial serif |

⚠ **`--font-display` CHANGED ON THE WEBSITE, 18 Aug 2026 (fifty-fifth session), ELLIOTT'S CALL.**
It was a high-contrast editorial serif with hairline strokes, and it made the site read thin and,
in his words, *"a little bit documenty"*. It is now **Bitter**, the slab that was already sitting
in this table as `--font-editorial` and which the website had never loaded. A slab heading agrees
with Alfa Slab One's slab wordmark, which is what "cozier, like the logo" means in type terms.

⚠ **THREE CONSEQUENCES, ALL DELIBERATE.**
- **`--font-brand`'s fallback moved with it.** The old stack named a font the site no longer
  loads, so the fallback described something that could not happen. Bitter is also a far better
  stand-in for Alfa Slab One than a high-contrast serif ever was — both are slabs.
- **The Lato 300 weight is no longer loaded.** Nothing on any page asked for `font-weight:300`,
  checked before removal, so it was pure page weight — and a 300 available to a future edit is
  how thinness creeps back in.
- **`--font-editorial` and `--font-display` now name the same family.** That is one word for two
  roles (rule 33) and it is tolerated rather than tidied: the roles are still genuinely
  different — one is headings, one is long-form body — and collapsing them would remove the seam
  that lets either move independently later. Recorded so the next reader knows it was seen.

⚠ **AND THE SAME DAY, `--font-ui` FOLLOWED IT. ELLIOTT TOOK THE WARMEST OPTION: BITTER FOR
BODY AS WELL AS HEADINGS, AND THE HUMANIST SANS IS GONE FROM THE SITE ENTIRELY.**

⚠ **THE WEBSITE IS NOW SINGLE-FAMILY, AND THAT IS THE THING TO UNDERSTAND ABOUT IT.** All three
text tokens name Bitter; only the wordmark differs. That is a real and deliberate look — it is
what "cozy" usually is in type — but it means **the contrast between a heading and the paragraph
under it no longer comes from the typeface.** It has to come from size and weight instead.

⚠ **SO EVERY HEADING RULE GAINED AN EXPLICIT WEIGHT IN THE SAME EDIT, AND WITHOUT THAT THE SWAP
WOULD HAVE FLATTENED THE PAGE.** Not one of the sixteen heading rules across the five pages
carried a `font-weight`, so every one of them was rendering at 400 — invisible while headings were
a different family, fatal the moment they were not. Section headings are now 700; the hero tagline
and the confidence ladder's rungs are 600, because 700 at that size shouts.

⚠ **THE TOKEN VOCABULARY HAS COLLAPSED TO ONE FAMILY AND THE SEAMS ARE KEPT ANYWAY.**
`--font-display`, `--font-ui` and `--font-editorial` now all resolve to Bitter, which is three
words for one thing (rule 33). The tokens stay separate on purpose: they are the only mechanism
by which any one role can move again without touching the others, and collapsing them to a single
token would be a one-line saving that costs the ability to change your mind.

⚠ **WHAT TO WATCH ON THE BANK, SO IT IS NOT DISCOVERED FROM A COMPLAINT:** a slab at body size in
a dark theme reads heavier than a sans did. If the long pages — the venue creators guide in
particular — feel dense, the levers in order are **line-height first** (currently 1.7 on the guide
pages, 1.6 on the home page) and **body size second**. The font is not the lever; it is the choice.

⚠ **THE GAME HAS NOT MOVED AND SITE AND GAME NOW DISAGREE.** `index.css` still carries the old
`--font-display`. The change was scoped to the website by request. **This is drift with a known
cause and a known fix, not an accident** — it is recorded here rather than left for someone to
discover from a screenshot. It closes either by changing the game's token to match or by Elliott
deciding the two surfaces should differ on purpose.

- **Alfa Slab One ships one weight (400)** and it's heavy by design — perfect for the
  wordmark and big display moments, **not** for body text. Keep `--font-ui` (Lato) for
  anything you read at small sizes.
- **To switch the brand font later:** change the `@font-face` `src` + the
  `--font-brand` value in `index.css` (and the website's CSS). Everything using
  `var(--font-brand)` updates at once. Nothing else to touch.

### `@font-face` (local file)
Place `AlfaSlabOne-Regular.ttf` at `src/assets/fonts/` (game) and `/fonts/` (website).
```css
@font-face {
  font-family: 'Alfa Slab One';
  src: url('./assets/fonts/AlfaSlabOne-Regular.ttf') format('truetype');
  font-weight: 400;
  font-display: swap;
}
```
> Ship the `.ttf` (~40 KB). **Only add a `woff2` `src` line once you've actually
> generated the `.woff2`** — listing a woff2 that doesn't exist makes the Vite dev
> server return `index.html` for it and the browser throws an OTS decode error
> (`invalid sfntVersion`). Converting to woff2 later halves the download; when you do,
> add it as a first `src` entry. Alfa Slab One is **single-weight (400)** — never set
> `font-weight:700` on the wordmark or the browser fakes bold and it smears. Keep
> `OFL.txt` alongside the font (SIL Open Font Licence — free commercial use; ship it).

---

## 4. The wordmark

- **Text:** `swimcraft` — one word. **Lowercase** is the primary lockup; an
  **uppercase** lockup (`SWIMCRAFT`) is available for tight/caps contexts.
- **Font:** `--font-brand` (Alfa Slab One).
- **Two-tone (dark ground — default):** `swim` = **Swim Bone `#E6DCC6`**,
  `craft` = **Craft Olive `#4E6B30`**, set on **Ink `#10150D`**.
- **Light-ground lockup:** `swim` = **Ink `#10150D`** (or `--deep`), `craft` = Olive.
- **Clear space:** keep padding around the wordmark ≥ the height of the lowercase "s".
- **Don't:** add shadows/glows/gradients · stretch or condense · recolour the two tones ·
  place the bone lockup on a light background · separate "swim" and "craft".

The wordmark is text set in the brand font, so it stays editable. When you want a
portable logo asset (SVG with outlined paths + a transparent PNG for Steam), say the
word and I'll generate them from the `.ttf` so they render anywhere without the font
installed.

---

## 5. How it percolates (implementation)

**Colours** already work this way — they're CSS variables in `index.css` consumed as
`var(--token)`. Add `--brand-bone`, `--brand-olive`, `--ink` there.

**Fonts** need the same treatment (the missing piece):
1. Add the four `--font-*` tokens + the `@font-face` to `index.css` `:root`.
2. Replace the ~29 inline `fontFamily:'Lato,sans-serif'` / `'Playfair Display,serif'`
   / `'Bitter,Georgia,serif'` across `App.jsx`, `VenueCreator.jsx`, `Tacklebox.jsx`,
   `BaitBox.jsx` with `fontFamily:'var(--font-ui)'` / `'var(--font-display)'` /
   `'var(--font-editorial)'`, and the **wordmark** spot(s) with `'var(--font-brand)'`.
3. Website: mirror the same `@font-face`, the same `--font-*` tokens, and the same
   colour hex, so both surfaces read one vocabulary.

After that, a font or colour change is a single edit in `index.css` (and its website
twin) — it percolates to every screen.

> **Status: wired ✓ (1 Jul 2026).** `index.css` now defines the four `--font-*`
> tokens + the `@font-face` for Alfa Slab One + `--brand-bone/--brand-olive/--ink`.
> All inline `fontFamily` across `App.jsx`, `VenueCreator.jsx`, `Tacklebox.jsx`,
> `BaitBox.jsx` and the CSS classes now read `var(--font-*)`. The wordmark (landing,
> topbar ×3, dock header) is unified two-tone bone/olive on `--font-brand`.
> **To use it, drop `AlfaSlabOne-Regular.ttf` into `src/assets/fonts/`** (and the
> optional `.woff2`) — the `@font-face` path already points there.

### Logo assets
Portable wordmark generated from the TTF (outlined — no font needed to render):
- `swimcraft-wordmark.svg` — two-tone vector, transparent (web / any scale)
- `swimcraft-wordmark.png` — 2753×548, transparent (Steam / overlays)
- `swimcraft-wordmark-ink.png` — same on the Ink ground (`#10150D`)

---

## 6. Changelog
- **v1.1 — 1 Jul 2026:** Fonts tokenised end-to-end (`--font-brand/display/ui/editorial`)
  + `@font-face` for Alfa Slab One in `index.css`; all inline/CSS families now
  `var(--font-*)`; wordmark unified two-tone bone/olive on the brand font across all
  five sites. Supporting palette filled with real `index.css` hex. Logo assets
  (SVG + 2 PNG) generated. A font/colour swap is now a one-line edit.
- **v1 — 1 Jul 2026:** Initial lock. Wordmark = Alfa Slab One, two-tone bone/olive.
  Brand colours **locked**: Swim Bone `#E6DCC6`, Craft Olive `#4E6B30` (chosen from a
  darker-green preview), Ink `#10150D`. Supporting palette captured from the game.
  Font-token system defined (pending wiring).
  *Open:* paste real `--gold-light/--deep/--surface/--card-bg/--border` hex from
  `index.css` so this doc holds the exact numbers, then do the font-token wiring (§5).
