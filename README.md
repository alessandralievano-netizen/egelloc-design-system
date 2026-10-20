# egelloC Marketing Design System

The brand system for egelloC's **marketing, social, and internal-resource assets** — statics, YouTube thumbnails, Canva layouts, social posts, decks, and collateral.

egelloC is a college-admissions coaching practice. The audience is **parents of students**, and the whole brand exists to move them from anxiety to strategic confidence. The two personality archetypes are the **Architect** (a plan you can bet your future on) and the **Pathfinder** (the leader you'd follow into a storm). Traits: accessible, enthusiastic, compassionate, empowering, trustworthy, strategic, fun, bold.

A separate design system governs the **product and UX/UI engineering** surfaces. This project does not cover those.

## Sources given

- **Official logo package** (`uploads/egelloC [Official Logo]`, `uploads/egelloC [Official Icons]`): primary lockup (wordmark + "Crack the College Code") and secondary lockup in five colourways each, plus the eagle and key marks — copied into `assets/logo/primary/`, `assets/logo/secondary/`, and `assets/marks/` as **SVG** (PNG kept alongside for the primary lockup). The tiled banner pattern is in `assets/patterns/`.
- **Reference creative**: 8 finished YouTube thumbnails (`uploads/THUMBNAILS/`), `July Admissions Static Creative Request.pdf` (33 pages of statics and carousels), `4-Year Roadmap JULY.pdf` (26 pages), `egelloC 2026 Acceptances [LOGOS].pdf`.
- **Typography direction**: Inter — Extra Bold for headings and titles, Regular for paragraph body.
- Written brand guidelines supplied in the brief: colour palette with hex values and usage rules, typography rules (Gibson; Inter for lightweight internal text), voice/tone and messaging strategy, logo-usage rules, and the "controlled creative flexibility" exception.
- **No codebase, Figma file, deck, photography, or icon set was provided.** Nothing here is reconstructed from memory; anything not supplied is marked as a gap below.

## Index

| Path | What's there |
| --- | --- |
| `styles.css` | The single entry point consumers link. `@import` list only. |
| `tokens/` | `colors.css`, `typography.css`, `spacing.css`, `effects.css`, `motion.css`, `fonts.css` |
| `tokens.json` | The tokens the Design System page shows and edits: colours, type styles, spacing, radii, shadows, border widths (compiled to `tokens.css`) |
| `components/<Component>/` | Per component: `README.md` (guidelines), `<Component>.d.ts` (props), `preview.html` (live preview). The bundle is `components/bundle.js` with `components/bundle.css` and `components/index.d.ts` |
| `assets/logo/` | Secondary wordmark: full colour, black, white, dual yellow/white, dual black/white |
| `assets/marks/` | Eagle mark (yellow/black/white), key mark (full colour, black, white, dual yw, dual bw) |
| `assets/patterns/` | `egelloc-banner-pattern.png` — the tiled "egelloC" texture on yellow |
| `guidelines/` | 23 specimen cards: colour, type, spacing, brand, voice · `ad-audiences.md` (cold vs warm, personas) · `creative-brief.md` (brief-writing procedure) |
| `references/personas/` | Persona Playbooks and Competitive Overview (source for ad audience rules) |
| `components/` | React primitives — see below |
| `templates/` | Ready-to-fill marketing layouts — see below |
| `assets/notes/SKILL.from-standalone.md` | Agent Skills wrapper so this folder works inside Claude Code |

### Components

`core/` — **Button**, **IconButton**, **Card**, **Badge**, **Tag**
`forms/` — **Input**, **Select**, **Checkbox**, **Radio**, **Switch**
`navigation/` — **Tabs**
`feedback/` — **Dialog**, **Toast**, **Tooltip**
`brand/` — **Logo**, **PromiseBlock**, **PatternBand**

Each directory has a `.card.html` showing its states. Every component has a sibling `.d.ts` (props contract) and `.prompt.md` (what/when + usage).

**Intentional additions.** No component library was supplied, so `core`/`forms`/`navigation`/`feedback` are a standard set sized to the brand's needs. Three additions are brand-specific: **Logo** (renders only approved artwork, so nobody hand-rolls a lockup), **PromiseBlock** (encodes the Golden Rule of messaging — a pain point can't ship without its blueprint), and **PatternBand** (the supplied banner pattern as a reusable header device).

### Templates

Six templates, one per format egelloC produces:

- `templates/youtube-thumbnail/` — **1280×720**. Gold-graded photo ground, host cutout right, 104px all-caps Extra Bold headline (white line + yellow line, hard Deep shadow), 92px Deep eagle badge top-right. `layout` tweak switches to the **VS slab** variant (skewed white slab over skewed Deep slab, yellow "VS" disc).
- `templates/static-card/` — **1080×1080** static or carousel card, centre-composed on one full-bleed ground (the left-aligned block structure is equally valid for explanation-heavy cards — see the composition section). Small secondary wordmark (top-left on Deep, top-centre on light), 86px Extra Bold headline, 66px accent payoff line, 34px Regular support, optional Lucide icon, optional CTA block, swipe cue. Tweaks: `ground` (deep / offwhite / yellow), `showIcon`, `showCta`, `showSwipe`.
- `templates/resource-deck/` — **16:9 (1280×720)**, six archetypes: Deep cover with the primary lockup, segment slide (Deep top bar with label + timing, centred content, yellow prompt band), yellow section header, three-card content, two-up comparison, Deep closing CTA.
- `templates/one-pager/` — **Letter (816×1056)**, print-ready: primary lockup header, 6px yellow rule, numbered steps, Deep "what to do this week" callout, credibility footer.
- `templates/landing-page/` — **web, fluid**, the master landing-page architecture. Eleven locked sections: sticky white header (92% white, `#EFEFEA` hairline, 10px blur, 28px wordmark, Regular-400 nav, yellow CTA pill) · hero in two columns with a Deep 24px photo frame carrying the gold radial and coach cutout · acceptance strip (hairlines top and bottom, school names as 17px/800 type, no logos) · pain→blueprint as three Off White cards, each an italic parent quote above a 4px-yellow-ruled blueprint line · coach panel with the cutout on the white + gold radial frame · four 16:11 video cards (Deep ground, bottom scrim, yellow play pill) plus an Off White testimonial panel · certifications hairline with the accreditation lockup slot · two start-free cards, one Yellow one Off White · Off White FAQ accordion, one row open at a time, answer behind a 4px yellow rule · inset Deep closing CTA panel with the eagle mark · hairline footer on white. **Locked:** section order, the two-Deep-panel budget, the web type scale, logo placement, grounds. **Payload:** all copy, video ids, FAQ entries, the school list, the photo slots. Full brief and the engineering notes in `templates/landing-page/README.md`.
- `templates/refund-statement/` — **Letter (816×1056)**, print-ready financial document built on `doc-page` so it exports to PDF as one sheet. Matched to the reference pair in `templates/refund-statement/reference/` (`INV-001033.pdf`, the original invoice, and `Refund_Invoice_2026_RS001033_egelloc.pdf`, the statement produced from it — **the statement is the authority on layout and wording**). Primary full-colour lockup at 56px with a "Refund statement" eyebrow, address block right-aligned, 6px yellow rule, three-column meta grid (issued to / statement number + issue date / program + refund request date), hairline-separated "Services delivered" rows where sessions cancelled by egelloC are named as such and marked "No charge applied", a running-balance "Refund breakdown" table that opens at the invoice's list price and works down through discount, payment received and each deduction so the parent can trace every line back to the invoice they hold, then a Deep callout at 16px radius with the yellow "Total refund due to you" eyebrow, the method sentence in white and the amount at 42px in yellow. Workflow: the invoice supplies billed-to name and contact, program, list price, discounts and amount paid; the statement number mirrors the invoice number with the prefix swapped to `RS-` (INV-001033 → RS-001033); what was delivered, what is deducted and the student's name come from the request — ask if they aren't supplied. **Reconcile out loud:** every difference between invoice and statement is called out to the requester before delivery (in the reference pair the billed-to surname and the enrolment year both differ, as CX corrections), as is any refund total that doesn't follow from the invoice figures. Rules: sentence case throughout; one page always; the domain is always lowercase `egelloc.com`; deductions carry a parenthetical reason where one exists ("Onboarding fee (non-refundable)"); the optional "Additional details" block is off by default and omitted entirely when the brief supplies nothing — never an empty heading or filler; **no CTA pill and no credibility line** — this is a financial document, not ad-facing creative. **Always runs the mandatory intake question set first** — six questions mapped to the template's blanks (student name, what was delivered and cancelled, which services were completed, refund method, issue date, additional details), each pre-filled from the invoice — the refund request date is never asked, since it is always the day the statement is requested. Deduction amounts are never asked either: they are priced from the Refund Value Table in `templates/refund-statement/refund-value-table.md`. Full brief and the question table in `templates/refund-statement/README.md`.

`review/Sample Review.html` renders live samples of the four marketing formats side by side with the reference creative, plus the open questions from the test phase.

**Format rules that hold across all four:** page padding is 64px at 1080 square and 80px on 16:9; the logo appears exactly once per asset; every asset carries Yellow *and* Deep; the credibility line ("UC Berkeley admissions reader · 10,000+ applications reviewed") closes every ad-facing asset; CTAs are yellow pills in uppercase.

---

## Content fundamentals

**Voice.** Warm and direct, never clinical. The live creative reads like a former admissions reader talking straight to one parent: *"A 4.0 won't get your kid into UCLA. The average admitted student has a 4.2."* · *"Good grades only get the file opened."* · *"Same kid. Same effort. The only variable is which year you started."* Short sentences. Concrete numbers. A named credential doing the reassuring — every ad-facing asset closes with "UC Berkeley admissions reader · 10,000+ applications reviewed." Second person — "you," "your student," never "one" or "parents should." The brand speaks as a guide who has already walked the path: "Here's the order we do it in," not "Families may wish to consider."

**The Golden Rule.** Never leave a parent in the passive state. For every *"I understand [pain point]"* there must be a *"Here is the [blueprint]."* The pain point is one sentence, in the parent's own words. The blueprint is specific, sequenced, and finite.

> **Relatable trap** (do not ship): "Junior year is overwhelming. Every parent feels lost right now."
> **Master Navigator** (ship this): "Junior year is overwhelming. Here's the 18-month plan: testing by fall, list by winter, essays by June."

**Sentence craft.** Short declaratives carry the blueprint. Numbers and sequence do the reassuring — "three schools," "twenty minutes," "testing → list → essays." Name the deadline, the count, or the order whenever you can; vague comfort reads as evasion.

**Casing.** Sentence case for headlines, subheads, and captions in decks, one-pagers, statics, and carousels. **On web surfaces — landing pages, marketing pages, web wireframes — headings and card titles run Title Case**, matching `masterclass.egelloc.com`, which is the reference for web. Eyebrows and CTAs stay uppercase everywhere. Web headlines are also full specific sentences rather than short hooks — "College Admissions Coaching for Families Who Refuse to Leave It to Chance", not "Crack the college code" — and cap at 24ch rather than 20ch, since the sentences run longer. Uppercase is used in exactly three places: the eyebrow/audience label ("FOR CALIFORNIA PARENTS"), CTA buttons ("GET THE FREE TRAINING", "SAVE YOUR FREE SEAT"), and **YouTube thumbnail headlines**, which are set all-caps at 96–104px because they are read at 320px wide. Nowhere else.

**Punctuation.** Periods in body copy; headlines usually run without a terminal period. Em dashes sparingly. Question headlines are allowed when the answer is immediately below it — never a question left hanging.

**Buttons and CTAs.** Verb-first and concrete: "Book a strategy call," "See the timeline," "Get the checklist." Not "Learn more," "Submit," or "Click here."

**Emoji.** Not used in brand assets — no emoji in statics, thumbnails, decks, or collateral. Icons carry that job.

**Numbers.** Numerals for anything countable ("3 schools," "18-month plan"). Spell out only at the start of a sentence.

---

## Visual foundations

**Colour.** Every asset must prominently carry **egelloC Yellow #FABF32** and **egelloC Deep #1E1E00** — those two together are the recognition cue. Deep is used *exclusively* as dark background blocks, containers, and shapes, never as a wash across a whole page. Body copy is True Black #000000 (Charcoal #1A1A1A for long digital layouts). Navy #1B2340, Accent Yellow #FBE452, Off White #F8F8F8, and Pure White #FFFFFF support and never lead. Target ratio: roughly 45% white/off-white ground, 25% yellow, 22% Deep, 8% navy (see the "Palette ratio" card). There is no red in the system — error and problem states use Navy.

*Controlled creative flexibility (the "Apple" rule):* a non-brand colour is permitted for a single graphic element that requires realistic or contextual colour (a red apple, a platform icon) as long as it neither clashes nor overpowers. Flag every use of this exception in the delivery note.

**Type.** One family, everywhere: **Inter**. Headings and titles are **Extra Bold (800)** — big and thick. Paragraph body is **Regular (400)**, normal weight. Nothing else. Display sizes (42–104px) run at 800 with −0.025 to −0.03em tracking and 0.94–1.08 line-height. Editorial headings 20–60px at 1.08–1.25. Body 16–17px at 1.55–1.6, measure capped at 66ch. Eyebrows 12–24px, weight 800, uppercase, 0.12–0.14em. No second font, ever.

**Layout.** Generous white ground with a small number of decisive blocks. 64px page padding, 96px between sections, 32px card padding, 32px between blocks inside a card, 16px between paragraphs, 12px between inline items — laid out with flex/grid `gap`, not margins. See "Composition, legibility & logo hierarchy" below for the two alignment structures and when each applies.

**Backgrounds.** Three treatments only: flat white/off-white, a flat Deep or yellow block, or the supplied banner pattern tiled on yellow at ~520–640px tile width. **No gradients as backgrounds** — the only gradient in the system is the Deep scrim over photography. No noise, no textures beyond the banner pattern.

**Imagery.** Warm, bright, real parents and students — daylight, eyes to camera, no cool blue grading, no stock gloss, no grain. **Coach cutouts** are the workhorse: transparent PNGs, arms crossed or mid-gesture, cropped at the bottom edge of the frame so the figure stands on the canvas floor, placed right of centre with a `drop-shadow(-14px 0 28px rgba(30,30,0,.45))` separating them from the ground. Never scale a cutout past its native height, never flip one horizontally, never place one on a busy ground. Three approved grounds: a flat Deep block, the gold radial on Deep, and — **new** — the **gold radial on white** for pages whose two-Deep-panel budget is already spent: `radial-gradient(58% 54% at 50% 68%, rgba(250,191,50,.55), rgba(255,255,255,0) 72%)` on `#FFFFFF`, 16px radius, cutout shadow lightened to `drop-shadow(-14px 0 24px rgba(30,30,0,.18))`. Photography is full-bleed inside its panel and always carries the Deep scrim (`--overlay-scrim`) when type sits on it; white type on unscrimmed photography is not allowed. **No photography was supplied**, so templates use labelled photo slots.

**Corner radii.** Actions are pills (`--radius-pill`). Cards and panels are 16px. Inputs, chips-in-forms and small tiles are 8px; badges on artwork 4px. 24px is reserved for large hero panels. Photo panels inside a fixed-size static (thumbnail, post) go square-cornered so they bleed to the edge.

**Cards.** White ground, 1px `#EBEBE6` hairline border, 16px radius, `0 2px 8px rgba(30,30,0,.08)` shadow, 32px padding. Elevated variants use `0 12px 32px rgba(30,30,0,.14)`. Shadows are always Deep-tinted, never neutral grey or black. Dark and brand cards drop the border entirely. Never a rounded card with a coloured left border as decoration — the 4px yellow rule is a *content* device (it marks the blueprint), not styling.

**Borders and rules.** 1px hairlines separate content. 2px is the outline-button and focus weight. 4px yellow rules mark the blueprint line, the active tab, and section breaks. 6px yellow caps the top of modals.

**Transparency and blur.** Only two uses: the Deep scrim over photography, and a 12px backdrop blur behind modal scrims. No frosted panels, no translucent cards.

**Motion.** Fast and eased, never playful-bouncy. 120ms for hover colour, 200ms for most transitions, 320ms for entrances. `cubic-bezier(.2,.7,.2,1)` standard. Hover on cards and buttons: colour shift, plus at most a −2px lift. Press: `scale(.97)`. Fades and short slides only — no springs, no bounce, no parallax.

**Hover / press states.** Yellow actions darken to `#E8AC1E` on hover, `#D19A15` on press. Deep actions lighten to `#33330A`. Outline and ghost buttons fill with the 12% yellow tint. Links are Navy, moving to Deep on hover, underline retained. Focus is a 2px Navy ring with 1px offset — visible, never removed.

**Logo.** **Never stretch, alter, recolour, outline, crop, rotate, add effects to, or rebuild any logo. Use the supplied file exactly as provided** — set height only and let width follow. Two lockups: the **primary** (wordmark + "Crack the College Code" tagline) introduces the brand — covers, title slides, one-pager headers, card 1 of a carousel; the **secondary** (wordmark only) handles tight and repeat placements — slide footers, corners, later carousel cards. The eagle and key marks stand alone for badges, avatars, and favicons; the thumbnail badge is the yellow eagle centred in a 92px Deep disc. Clear space on all sides is at least 0.5× the logo's height. Minimum widths: primary 140px, secondary 96px, marks 24px. Full-colour on white or Off White only; dual yellow/white on Deep or Navy; black on yellow and on the banner pattern; white only on Deep, Navy, or scrimmed photography — never on yellow (~1.9:1).

---

## Composition, legibility & logo hierarchy

**Legibility first — the reader is a parent in their 40s, usually on a phone.** This outranks every other visual preference and is the one part of this section that is not negotiable.

- High contrast, always: Deep or True Black on white / Off White, or crisp white on Deep or True Black. Never yellow type on white, never white on yellow, never mid-grey body copy on Off White.
- Body copy is never thin and never decorative: Inter Regular 400, and no smaller than 28px on a 1080 square, 24px on a 1080-wide thumbnail, 22px on a 16:9 slide, 12pt in print.
- Generous line spacing: 1.45–1.6 on body, 1.05–1.25 on headings. Never tighter.
- Clear weight jumps only — 800 against 400. No 500/600 half-steps trying to imply hierarchy.
- One idea per asset. If a card needs two paragraphs to land, it is two cards.
- Pure #FABF32 as *type* on white or Off White is ~1.8:1 and fails. On light grounds, emphasis type is Deep or the darkened #C48B00; #FABF32 stays pure for fills, pills, rules and bands.

**Two layout structures — both are ours.** The brand uses centre-composed full-bleed grounds *and* left-aligned block layouts. Neither is the default; the content and the platform decide.

| Reach for | When |
|---|---|
| **Centre-composed**, full-bleed single colour, generous air | High-impact hero graphics, YouTube thumbnails, single-line hooks, payoff and CTA cards — anything read in under two seconds |
| **Left-aligned blocks** | Structured readability: deck body slides, one-pagers, step lists, comparisons, carousel cards carrying real explanation |

Mixing the two inside one carousel or deck is normal and intended — a centre-composed hook card followed by left-aligned explanation cards is a correct sequence, not an inconsistency. Always check the brief and any reference assets attached to the request before choosing.

**Guidelines, not a straightjacket.** The layout formulas, colour ratios and card breakdowns in this system are baseline templates, not rigid rules. Adapt them, combine them, or break the mould when the project calls for it — a unique composition, a mixed alignment, or an alternative structure is the right answer whenever it serves the message better than the formula. What stays fixed: legibility, the two core colours, Inter, and the logo rules. Everything else is judgement, and context wins over formula.

**Anti-cheap polish \u2014 the high-end floor.** Clutter reads as cheap; air reads as authority. These are pass/fail checks before anything ships.

- **The luxury of air.** Nothing touches or crowds the frame edge. Minimum safe margins: **72px** on a 1080\u00d71080 static, **64px** on a 1280\u00d7720 thumbnail, **64px** on a 16:9 slide, **64px** on a Letter one-pager. Headlines, body copy and logos all sit inside that boundary, and the space around them is intentional \u2014 not leftover.\n- **A strict scale, no random sizes.** Type comes from the ramp only (display 104 / 86 / 72 / 60 / 48 / 42, body 17 / 16, eyebrow 24 / 14 / 12). Dominant heading to body should be a clear multiple \u2014 roughly 3\u00d7 or more on statics and thumbnails, never a timid 1.3\u00d7 step that leaves hierarchy ambiguous.\n- **Aspect ratios are locked.** Never stretch, squash, or distort type, logos, icons, or photography. Set one dimension and let the other follow. No horizontal scaling to make a word fit \u2014 change the size or the words.\n- **Intentional colour blocking.** Yellow and Deep do the work, against True Black, Off White and Pure White. Blocks are flat and deliberate. No muddy gradient overlays (the Deep photo scrim is the sole exception), no bevels, no glows, no neon-on-neon. Contrast is sharp and effortless \u2014 if it takes a second to read, it fails.\n- **Shadows are structural, not decorative.** Deep-tinted only, and only where they do a job: card elevation, separating a cutout from its ground, the hard offset on thumbnail display type. No soft grey blurs sprinkled for depth, no shadow on body copy.\n- **Even container padding.** Inside any card or Deep box, padding is equal on all four sides (32px standard, 48px on large panels) and content aligns to a single edge. Nothing should feel trapped against a wall or floating off-axis.\n- **One focal point.** Every asset has a single dominant element \u2014 one headline or one colour block. If two things compete for first read, cut or subordinate one.\n\n**Logo hierarchy.**

| Placement | Variant |
|---|---|
| Deck front covers, formal one-pagers, brand hero headers — where there is ample whitespace to let it breathe | **Primary lockup with tagline** |
| Social statics, carousel cards, YouTube thumbnails, slide footers, any dense or tight space | **Secondary wordmark, or the eagle / key mark** |

The primary lockup is never forced onto a dense graphic. On Deep grounds the wordmark sits small and at reduced presence (white or dual-b&w at ~55–70%) so it identifies without competing with the headline; on Off White and Yellow grounds it sits in black at full strength. **When a brief names a variant, that variant is used — no guessing, and no upgrading to the primary lockup just because there was room.**

**Composition standards.**

- One asset, one ground: Off White, Deep, or Yellow, full-bleed. No gradients behind type, no yellow layered on yellow.
- The heading dominates. The eye travels hook → proof → CTA with nothing competing in between.
- Negative space is a brand asset. A card with one icon, one headline, one support line and empty space is finished, not unfinished.
- Yellow and Deep both appear on every asset, even when the ground is Off White (yellow CTA pill, Deep type).
- Fixed furniture: wordmark top, nav cue ("Swipe →") bottom-right in muted grey, CTA above the credibility line.

---

## Web surface direction (landing pages, web wireframes, marketing sites)

Web surfaces are the one place the brand runs **light**. Statics and thumbnails shout; a page has to be read for
several minutes by a parent on a phone, so the ground stays white and the brand colours arrive as accents and panels.
This is the default look for any landing page, web wireframe or marketing page unless the brief says otherwise.

**Ground and blocking.** Pure White page ground. Off White `#F8F8F8` for grouping panels — stats, feature cards, FAQ
rows, bio blocks — with no border and no shadow. Deep appears as exactly one or two rounded blocks per page (the
closing CTA panel, and optionally a thin announcement strip at the very top). Yellow appears as small accents: one
card, the CTA pills, a 4px rule, a 6px cap on modals. Never a full-bleed Deep or yellow band behind long copy.

**Type scale — smaller than the static scale.** Statics run 86–104px; web runs restrained:

| Role | Size | Weight |
| --- | --- | --- |
| Page headline (H1) | 44–52px | 800, −0.03em, 1.06 |
| Section heading (H2) | 30–36px | 800, −0.025em, 1.12 |
| Sub-section / card title | 18–20px | 800, −0.015em, 1.35 |
| Body | 16–17px | 400, 1.6, max 66ch |
| Eyebrow | 11–12px | 800, uppercase, 0.14em |

Headlines are big by proportion, not by absolute size — the air around them does the work. Never larger than 52px on
a page H1, and never a heading that fills its column edge to edge: cap headings at 20–24ch.

**Section rhythm.** Every section opens with an 11–12px uppercase eyebrow in `#C48B00` above the heading
("What's inside", "The wake-up call", "FAQ"). 112px between sections, 56–64px page padding, 24px radius on large
panels, 16px on cards, pills on actions.

**Furniture.** Sticky white header (92% white, 1px `#EFEFEA` bottom hairline) with the secondary wordmark left and a
small CTA right. Hairline footer on white, not a black bar. Closing CTA is a rounded Deep panel inset from the page
edges, centre-composed, with the credibility line under the button.

**Borders and text colour on web.** Hairlines are `#EFEFEA`. Body copy `#1A1A1A`; secondary copy `#6B6B5E` and no
lighter (anything lighter fails contrast on white). Emphasis and headings are Deep `#1E1E00`. Yellow is never type.

**What this direction rules out.** Bordered-and-shadowed cards stacked down the page, 60px+ headings, bold weight on
supporting copy, full-width colour bands between every section, and more than one focal element per section.

---

## Web surfaces — landing pages, marketing pages, web wireframes

Web is the one place the brand runs **light**. Statics and thumbnails shout; a page has to be read for several minutes by a parent on a phone, so the ground stays white and the brand colours arrive as accents and panels. This is the default for any landing page, marketing page or web wireframe unless the brief says otherwise.

**Ground and blocking.** Pure White page ground. Off White `#F8F8F8` for grouping panels — stats, feature cards, FAQ rows, bio blocks — with no border and no shadow. Deep appears as exactly **one or two rounded blocks per page** (the closing CTA panel, and optionally a thin announcement strip at the top). Yellow appears as small accents: one card, the CTA pills, a 4px rule, a 6px cap on modals. Never a full-bleed Deep or yellow band behind long copy.

**Type scale — smaller than the static scale.** Statics run 86–104px; web runs restrained.

| Role | Size | Weight |
| --- | --- | --- |
| Page headline (H1) | 44–52px | 800, −0.03em, 1.06 |
| Section heading (H2) | 30–36px | 800, −0.025em, 1.12 |
| Sub-section / card title | 18–20px | 800, −0.015em, 1.35 |
| Body | 16–17px | 400, 1.6, max 66ch |
| Eyebrow | 11–12px | 800, uppercase, 0.14em |

Headlines are big by proportion, not by absolute size — the air around them does the work. Never larger than 52px on a page H1, and never a heading that fills its column edge to edge: cap headings at 24ch.

**Section rhythm.** Every section opens with an 11–12px uppercase eyebrow in `#C48B00` above the heading ("What's Inside", "The Wake-Up Call", "FAQ"). 112px between sections, 56–64px page padding, 24px radius on large panels, 16px on cards, pills on actions.

**Furniture.** Sticky white header — `rgba(255,255,255,.92)`, 1px `#EFEFEA` bottom hairline, 10px backdrop blur — with the secondary wordmark at 28px left and a small CTA right. Nav links are Regular 400, not 800; bold nav reads heavy against a 400-body page. Hairline footer on white, not a black bar. Closing CTA is a rounded Deep panel inset from the page edges, centre-composed, with the credibility line under the button.

**Borders and text colour.** Hairlines are `#EFEFEA`. Body copy `#1A1A1A`; secondary copy `#6B6B5E` and no lighter — anything lighter fails contrast on white. Emphasis and headings are Deep `#1E1E00`. Yellow is never type.

**Ruled out on web.** Bordered-and-shadowed cards stacked down the page, 60px+ headings, bold weight on supporting copy, full-width colour bands between every section, and more than one focal element per section.

**Engineering rules for every web build.**

1. **`box-sizing: border-box` reset.** Padded flex children with a percentage basis overflow their row without it — three 33.333% cards with 32px padding wrap 2 + 1.
2. **Even rows without media queries.** Wrap on `flex: 0 1 calc(100%/n - gap)` with a matching `max-width` and a `min-width`, not `grid-template-columns: repeat(auto-fit, minmax(...))`. Both auto-fit and `flex-grow: 1` leave an orphan card at mid widths — grow lets the wrapped item absorb all remaining free space, which on an `aspect-ratio` card becomes a full-width block. `min-width` still wins over `max-width`, so mobile is unaffected.
3. **Logos are never stretched at the element box either.** An `<img>` that is a direct child of a flex *column* stretches to the column width by default, letterboxing the artwork and knocking it out of alignment. `align-self: flex-start` on every logo `<img>` in a flex column — the "never stretch the logo" rule applies to the box, not just the artwork.
4. **Never author an `<img src>` from a template hole.** The raw `{{ … }}` string is fetched as a URL during the streaming pass and errors on every load. Use a literal `src`, or build the element in the logic class.
5. **Responsive without breakpoints.** `clamp()` on type and section padding, `flex-wrap`, and `aspect-ratio` cover desktop through mobile in one pass.

---

## Template locking — end-user asset generation

Two audiences use this system, and they get different permissions. Full rules in `assets/notes/CLAUDE.from-standalone.md`.

**The design-system owner** may change anything: grids, layouts, master templates, tokens, components.

**Component and type tweaks.** Surface-level typographic adjustment is permitted — font weight within the family's authorized range, and fine-tuning a font size for context. The range is scoped, because the 400/800 contrast is much of what makes a static recognizable at thumbnail size: **Regular 400** for body, supporting lines and nav; **Extra Bold 800** for headlines, subheads, card titles, eyebrows, CTAs and figures; **Medium 500 only** for small dense type under 14px — table headers, data labels, eyebrows on light grounds — never on a heading or on body copy. What stays locked is the *proportions*: the type scale ratios, the spacing scale, line-height as a proportion of font size, and layout element ratios. When a size changes, the component's internal proportions and container layout scale proportionally with it per the tokens — line-height keeps its ratio, padding and gaps move with the type step, sibling sizes in the same scale move with it so the hierarchy holds. An arbitrary size change that leaves the surrounding proportions where they were is a proportional break and is refused. Full rule in `assets/notes/CLAUDE.from-standalone.md` ("Component tweaks").

**Copy is the requester's call.** Wording someone supplies is used **verbatim** — formatted and fitted, never rewritten because another phrasing sounds better. Write the copy in the brand voice when they have none; flag it and offer one alternative when the tone is too aggressive or leaves a parent in the passive state; say what will happen when a line does not fit and offer a trim or a size step. Then set whichever they choose. The compliance notice covers structure, layout and brand — never wording.

**Everyone generating assets from it** may change the **payload only** — text copy, dynamic images, tabular data, localized messaging, inside each template's predefined dynamic content zones. Once a template is selected for a request, four things are locked: its layout architecture, aspect ratio, grid framework and container dimensions; the font families, base sizes and weights defined for that asset type; logo sizing, placement and header/footer structure; and background and primary brand colours.

If an asset request asks for a structural, layout, or brand change: don't apply it, apply the valid content changes, output the asset in the strict master layout, and open the reply with the compliance notice in `assets/notes/CLAUDE.from-standalone.md`.

---

## Asset intake — always ask first

Never start an asset without the purpose/goal, the audience, and the platform/format with dimensions. That rule extends to **filling a template's blanks**: when a template has fields the source material can't supply, put them to the requester as a structured question form and wait, rather than inventing plausible values.

**The template structure is the fixed base. Questions only fill its blanks** — they never restructure the layout, reorder sections, or add ones the template doesn't have. Read whatever source was supplied first (an invoice, a brief, a transcript), pre-fill each question with what that source already told you, and ask only for what's genuinely missing. The question set changes per request and per person; the structure does not.

Answers that contradict the source are corrections, not errors: carry them through, and flag every one to the requester before delivery.

`templates/refund-statement/README.md` holds the worked example of this — the seven questions that map to that template's blanks.

---

## Ads — audience temperature and persona

Graphics (internal resources, general social, collateral) can be briefed freely. **Ads are different: the company has already defined who they are for**, so every ad needs two answers before design starts. Full rules: `guidelines/ad-audiences.md`. Brief-writing procedure (for the marketing team writing briefs): `guidelines/creative-brief.md`. Sources: `references/personas/` (Persona Playbooks, Competitive Overview).

- **Temperature — COLD or WARM.** Describes the audience, not the mood. Cold = has never engaged with egelloC: qualify in 2 seconds (audience + topic in eyebrow or first line), credibility line on every unit, typography as hero, open the loop without answering the how. Warm = already knows the brand and the coach: lead with the outcome, Off White flat ground, italic-bold payoff line, coach on the CTA card only, no fear hooks.
- **Persona — P1, P2, P3 or ALL.** Temperature sets the ad's job; persona sets vocabulary, proof and register. P1 first-gen immigrant: warm, jargon-free, light ground, sequence devices, no prestige language. P2 2nd-gen college-educated: then-vs-now data, authority ground, no urgency. P3 competitive California: zip-code and school specificity, editorial dark, concise, never "affordable" or comparisons to DIY/counselors. ALL defaults to P2 register.

On-creative rules that apply to every ad: say "free live training", never "webinar"; no dates or times; results claims keep their qualifiers (98.4% of long-term students admitted to one of their top-10 choices). The default rules in this readme stay in force for every format and apply whenever a brief is silent. When a brief explicitly asks for a departure from a default (casing, CTA shape, credibility line, size), build it as briefed and list the departure in the delivery note. Palette tokens, Inter, logo integrity, legibility floors and the anti-cheap checks still hold. Coach Tony (`coach-tony-*`) and Coach David (`coach-david-*`) are different people; use the one the brief names. The coach photos are a stock library: templates ship with a default, and a graphic swaps in the specific coach it needs.

If an ad request doesn't state temperature and persona, ask for both in the intake form.

---

## Iconography

**Lucide is the approved icon set** (`https://unpkg.com/lucide@0.544.0/dist/umd/lucide.js`). No icon font, sprite sheet, or SVG library was supplied in the brand sources, and Lucide matches the brand's needs best of the freely-licensed sets: a consistent 2px stroke, rounded caps and joins, geometric construction that sits comfortably next to the wordmark's geometry, and an outline-only style that keeps yellow and Deep doing the colour work. Rules for use:

- Line icons only, 2px stroke, `currentColor`. Never mix filled and outline glyphs in one layout.
- 20px inside buttons and inline with body copy, 24px standalone, 32–48px as a feature glyph inside a card.
- Icons take Deep on light grounds, Yellow on Deep grounds, Deep on yellow grounds. Never a multicolour icon.
- Icons support labels; they don't replace them. Never an icon-only nav item without a tooltip.
- **No emoji** as iconography, and no Unicode dingbats (✓, →, ★) standing in for icons in production artwork — use the real glyph. Plain `→` inside running body text is fine.
- Third-party platform logos (YouTube, Instagram, LinkedIn) use their own official brand colour under the controlled-flexibility rule, and that use should be flagged.

**The eagle badge.** On thumbnails and video-facing assets the brand's own mark acts as the watermark: `assets/marks/eagle-yellow.svg` centred in a 92px Deep disc, top-right, 32–36px from the edges. That badge is part of every thumbnail.

If egelloC has a licensed icon set, drop it into `assets/icons/` and this section should be rewritten around it.

---

## Gaps and open items

1. **Photography — partial.** `assets/photography/` holds eight coach photos (David: arms-crossed polo, arms-crossed quarter-zip, seated in cap, plus three 16:9 expression headshots — `coach-david-headshot-smile`, `-surprised`, `-thinking` — for thumbnail reactions; Tony: arms-crossed cutout, plus one on-location wood-wall frame). The YouTube thumbnail template now uses David's arms-crossed polo cutout live. **Still missing:** any parent/student imagery, and location/office photography. Chart panels remain slots.
2. **Reference creative on file.** `references/` holds the finished assets these templates were matched against: `slide-16x9.png`, `static-offwhite-scorecard.png`, `static-deep-table.png`, `carousel-deep-hook.png`, `carousel-offwhite-icon.png`, `carousel-yellow-payoff.png`, `carousel-offwhite-cta.png`, `carousel-deep-portrait.png`. The two source PDFs were read as text, so their copy is captured accurately but their exact Canva padding is not. The 2026 Internship Brochure is filed alongside them — `references/internship-brochure-2026.pdf`, page captures in `references/brochure/`, and an analysis of its conventions in `references/internship-brochure-2026.md`. It is long-form reference only, not a template. Six live YouTube thumbnails are in `references/thumbnails/`, with analysis and open conflicts in `references/thumbnails/README.md`.
3. **Test phase open.** `review/Sample Review.html` renders all four formats live beside the reference creative, with the open contrast and sizing questions listed at the bottom. The system is not final until those are signed off.
4. **No product/marketing website source**, so this system contains no UI kits. If marketing links to a site or app, attach the codebase or Figma file.
