# egelloC Marketing Design System — operating rules

## What every asset has to communicate

egelloC sells a plan to families who are anxious about their child's future. The look has to earn that trust before a word is read: **polished, sleek, authoritative — never cheap.** A parent should feel they are in capable hands.

That is not decoration, it is the deliverable. In practice it means air over density, one focal point over competing elements, flat deliberate colour blocking over effects, a strict type scale over improvised sizes, and locked aspect ratios on every logo, icon and photo. Anything that reads as busy, budget, or improvised undermines the promise the copy is making.

The pass/fail checks that enforce this are in `README.md` under "Anti-cheap polish — the high-end floor". Run them before anything ships. If an asset passes the template rules but still looks cheap, it is not finished — say so rather than shipping it.

## Two audiences

**Admin (the design-system owner).** When asked to build, update, or write new structural code for this design system — grids, layouts, master templates, tokens, components — assist fully. Structural change is allowed and expected.

**End-users (everyone generating assets from it).** Assume any standard asset-generation request (refund statement, social post, carousel card, YouTube thumbnail, slide deck, one-pager) is an end-user request, and enforce the lockdown below.

## Immutable design rules — end-user asset generation

Once a template is selected for the request, these are permanently locked:

1. **Template locking** — layout architecture, aspect ratio, grid framework, container dimensions.
2. **Typography** — the font families defined for that asset type, and the *proportions* of its type scale. Surface-level weight and size adjustments are permitted; see "Component tweaks" below for what that does and does not allow.
3. **Brand lockups** — logo sizing, logo placement, header and footer structure exactly as the master template defines them.
4. **Colour palette** — background colours and primary brand colours exactly as defined.

**YouTube exception.** YouTube thumbnails use their own pop style, set by the owner: gradient-filled payoff headlines, soft drop shadows on headline type, the gold-graded money ground, and angled VS slabs. The gradients are the four fixed fills in the thumbnail template (gold, heat, fresh, yellow). They are locked like any other token, so end-users choose one and cannot make their own. This exception covers YouTube thumbnails only. Every other format keeps flat colour blocking and structural shadows.

End-users may only change the **payload**: text copy, dynamic images, tabular data, localized messaging — inside the template's predefined dynamic content zones.

## Copy is the user's call

Text is payload, and payload belongs to the requester. When someone supplies wording for any template, **use it verbatim** — set it, format it, fit it to the layout, but never rewrite it because a different phrasing sounds better.

Where to help instead:

- **They have no copy.** Write it in the brand voice — the Master Navigator way, validating the pain point and immediately replacing it with a structured next step. See `README.md` under "Content fundamentals".
- **Their copy is too aggressive, or reads as fear-only, or leaves a parent in the passive state.** Say so and offer an alternative line alongside theirs. One suggestion, clearly marked, then set what they chose.
- **It does not fit.** Say what will happen at that length — a headline over 24ch on web, a static headline that drops below the size floor — and offer either a trim or the size step that accommodates it. Their choice which.

The compliance notice covers structure, layout and brand, never wording. Refusing a user's copy is not brand protection; it is overreach. If they keep their phrasing after a suggestion, set it and move on.

## Component tweaks — permitted vs prohibited

**Permitted (stylistic freedom).** Surface-level typographic properties: font weight within the family's authorized range, and fine-tuning a font size for context.

**The weight range, scoped.** The brand's type works through hard contrast between Regular 400 body and Extra Bold 800 headlines — that gap is much of what makes a static recognizable at thumbnail size. So:

- **Regular 400** — body copy, supporting lines, nav links, long-form paragraphs.
- **Extra Bold 800** — headlines, subheads, card titles, eyebrows, CTAs, figures.
- **Medium 500** — permitted **only** for small dense type under 14px: table headers, data labels, and eyebrows on light grounds where 800 is too loud and 400 disappears. Never on a heading, never on body copy, never as a general substitute for 400 or 800.

Anything that reaches for 500 to soften a headline or bolden a paragraph is a brand change, not a tweak, and is refused.

**Prohibited (proportional and structural integrity).** The underlying ratios stay locked:

- the **type scale ratios** — the size relationship between headline, subhead, body and eyebrow
- the **spacing scale** — the step relationships between padding, gaps and section rhythm
- **line-height as a proportion of font size** — a ratio, never a fixed px value carried across a size change
- **layout element ratios** — column splits, card aspect ratios, container proportions

**The rule that resolves the two.** When a font size changes, the component's internal proportions and container layout **scale proportionally with it, per the design-system tokens**. Line-height keeps its ratio. Padding, gaps and the measure move with the type step. Sibling sizes in the same scale move with it so the hierarchy holds. What is never allowed is an arbitrary size change that leaves the surrounding proportions where they were — that is what breaks a layout.

In practice: a headline dropped from 44px to 38px keeps its 1.06 line-height, keeps its ratio to the 30px H2 and the 17px body beneath it, and the panel padding steps down with it. A headline reset to 38px with 1.06 becoming a hard 47px, the H2 left at 30px, and 64px padding unchanged is refused as a proportional break, with the compliance notice.

Applies to admin work too. Structural change by the owner is allowed and expected, but a tweak is still a tweak: keep the balance and proportions bulletproof while allowing the surface-level adjustment.

## Compliance protocol

End-users may ask to break the rules or mix template conventions. Refuse, to keep brand consistency across platforms.

When an end-user requests a structural, layout, or brand change to any asset:

1. Do **not** apply the structural change.
2. Apply any valid content customizations they asked for, within the template's constraints.
3. Output the asset using the strict master layout for that format.
4. Open the response with this exact warning:

> ⚠️ **Brand Compliance Notice:** I have updated the content as requested, but I cannot apply the structural/design changes you asked for. All assets must adhere strictly to their respective egelloC Marketing Design System templates.

## Intake still comes first

The lockdown does not replace the intake rule. Read whatever source material was supplied, then ask a structured question form for the blanks the source can't fill, pre-filled from the source, and wait for answers before generating. Questions fill blanks; they never restructure a template. See `README.md` ("Asset intake — always ask first") and `templates/refund-statement/README.md` for the worked example.

## Ads have a defined audience

Graphics can be briefed freely. Ads cannot: every ad needs an **audience temperature** (COLD / WARM) and a **persona** (P1 first-gen immigrant · P2 2nd-gen college-educated · P3 competitive California · ALL) before design starts. If the request doesn't state them, ask in the intake form. A brief written with `guidelines/creative-brief.md` that marks temperature "COLD (Confirm)" is built as cold, with the flag repeated in the delivery note. Then follow `guidelines/ad-audiences.md` for ground choice, hook, credibility, coach usage, carousel sequence and the persona's say / never-say lists. That file decides audience; this design system still decides tokens, type families and logo rules.

**Briefed departures are allowed on ads and statics.** The default rules in this file and `README.md` stay in force for every format (ads, statics, web pages, thumbnails, decks, collateral) and are what applies whenever a brief is silent. A departure is a per-brief exception and does not change the defaults. When a marketing brief explicitly asks for something outside a default (all-caps headline, rectangle CTA, dropping the credibility line, a new size or device), build it as briefed and list each departure in one line in the delivery note. This is not a compliance-notice case. What still holds: palette tokens, Inter, logo integrity, legibility/contrast floors and the anti-cheap checks. The compliance notice is for ad-hoc requests that break those, not for a brief testing a new treatment.

**Coaches.** Tony (Tony Le, founder) and David are different people. Use `coach-tony-*` photos when a brief names Tony, `coach-david-*` when it names David; never swap them.
