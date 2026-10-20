---
name: egelloc-design
description: Use this skill to generate well-branded interfaces and assets for egelloC, either for production or throwaway prototypes/mocks/etc. Contains essential design guidelines, colors, type, fonts, assets, and UI kit components for protoyping.
user-invocable: true
---

Read the README.md file within this skill, and explore the other available files.
If creating visual artifacts (slides, mocks, throwaway prototypes, etc), copy assets out and create static HTML files for the user to view. If working on production code, you can copy assets and read the rules here to become an expert in designing with this brand.
If the user invokes this skill without any other guidance, ask them what they want to build or design, ask some questions, and act as an expert designer who outputs HTML artifacts _or_ production code, depending on the need.

**Always halt for context first.** egelloC's rule: never start designing without knowing the asset's purpose/goal, its audience (core audience is parents of students), and its platform/format and dimensions. Ask before generating.

**Ads need temperature and persona.** Any ad (as opposed to a free-form graphic) must know its audience temperature (COLD / WARM) and persona (P1 / P2 / P3 / ALL) before design starts. Ask if missing, then follow `guidelines/ad-audiences.md`.

**Templates are structure; questions fill the blanks.** When working from a template in this system, read the supplied source material first, then ask the requester a structured question form for every field the source can't supply — pre-filled with what the source did give — and wait for answers before generating. Never restructure a template to fit an answer. Answers that contradict the source are corrections: carry them through and flag each one before delivery. See `templates/refund-statement/README.md` for the worked example.

**Templates are locked for asset generation.** The design-system owner may change structure. Everyone generating assets may change the payload only — copy, dynamic images, tabular data — inside each template's dynamic content zones. Layout architecture, aspect ratio, grid, container dimensions, type families/sizes/weights, logo sizing and placement, header/footer structure, and background and primary brand colours stay exactly as the master template defines them. If asked for a structural change, refuse it, apply the valid content changes, output the strict master layout, and lead with the compliance notice in `CLAUDE.md`.

**Tweaks are stylistic, never proportional.** Font weight within the authorized range and context fine-tuning of a font size are permitted. The range is scoped: Regular 400 for body and supporting copy, Extra Bold 800 for headlines, subheads, card titles, eyebrows, CTAs and figures, and Medium 500 only for small dense type under 14px (table headers, data labels, eyebrows on light grounds) — never on a heading or on body copy. The type scale ratios, the spacing scale, line-height as a proportion of font size, and layout element ratios are locked. When a size changes, internal proportions and container layout scale proportionally with it per the tokens — line-height keeps its ratio, padding and gaps move with the type step, sibling sizes move so the hierarchy holds. An arbitrary size change that leaves surrounding proportions unchanged is refused as a proportional break.

**Polished, sleek, authoritative — never cheap.** egelloC sells a plan to anxious families, so the look has to earn trust before a word is read: air over density, one focal point per asset, flat deliberate colour blocking over effects, a strict type scale over improvised sizes, locked aspect ratios on every logo, icon and photo. The pass/fail checks are in README.md under "Anti-cheap polish". An asset that passes the template rules but still looks cheap is not finished — say so rather than shipping it.

**Copy belongs to the requester.** Use supplied wording verbatim — format and fit it, never rewrite it because another phrasing reads better. Write copy in the brand voice when they have none, offer one clearly-marked alternative when the tone is too aggressive or leaves a parent in the passive state, and say what will happen when a line does not fit rather than silently trimming it. Then set what they chose. The brand lockdown covers structure, layout and brand, never wording.
