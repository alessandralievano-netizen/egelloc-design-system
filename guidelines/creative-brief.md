---
name: creative-brief
description: Generate professional, designer-ready creative briefs for Meta ad campaigns — static ads and carousels. Use this skill whenever the user asks for a creative brief, designer brief, or wants to communicate visual direction to a designer. Also trigger when the user wants to create Meta static ads or carousels, refresh existing creatives, or plan a new ad set — even if they don't use the word "brief" explicitly. Trigger on phrases like "I need to send this to my designer", "brief a creative", "we need new ads", "create a brief for X campaign", "what should this ad look like", or "help me plan this ad set". Always outputs both a .md and a .pdf file. Never outputs inline only.
---

# Creative Brief Skill

Generate complete, designer-ready creative briefs for Meta static ads and carousels, executable on the first pass by a designer or Claude Design.

## What This Skill Produces

Two downloadable files — `.md` and `.pdf` — containing:
- A required brief header (audience temperature, brief type, control file, destination…) and a brand reference section
- For every creative unit: strategy, exact copy (word for word, not to be altered), visual direction, numbered hierarchy, ASCII layout sketch, "Do not" list
- A deliverables + assets checklist

**Output rule:** Always generate both `.md` and `.pdf`. Save both to `/mnt/user-data/outputs/` and deliver both to the user. Never output inline only.

**File naming:** `[Brand]_[Campaign]_Creative_Brief_[YYYY-MM]` (no extension — applied to both files)

**PDF generation:** Load the `pdf` skill before generating the PDF and follow its method.

---

## Step 0 — Precedence (read first)

For egelloC work, three sources govern a brief. When they conflict:

1. **The egelloC Marketing Design System wins on everything visual and structural** — colour tokens, Inter 400/800, the `static-card` template, logo hierarchy, legibility floors, the credibility line, anti-cheap checks.
2. **The Cold vs Warm rules in this skill win on audience decisions** — which ground, how much to explain, what Tony does, what the hook may do, carousel sequencing, new concept vs iteration.
3. **The brief wins on copy.** Copy is set verbatim.

Never invent a new hex value, font or logo rule. Describe colour by **role** (dark / light / brand ground, accent, emphasis); the designer maps roles to tokens (see Token translation in Step 5).

---

## Step 1 — Intake

Extract from conversation context first — only ask for what's genuinely missing. Valid messaging sources: written copy, video scripts, winning ad copy, headlines, webinar scripts, any campaign material.

**Required — extract or confirm:**
- What is being advertised? (webinar / free live training, lead magnet, offer)
- **Audience temperature: COLD or WARM** (audience, not mood — see Step 2)
- Who is the audience? (who, grade, state, persona) and awareness stage
- **Brief type:** NEW CONCEPT · COPY ITERATION · BACKGROUND ROUND · RESIZE
- **Control file** — required for any iteration, round or resize
- Destination (registration page URL, lead form, DM)
- Meta formats (feed statics, carousels, both) and sizes (default 1080×1080)
- CTA (the action the ad drives)
- Existing messaging to adapt (scripts, winning copy) and source script ID if from a video batch
- Brand assets the designer already has (logo files, Design System, Tony cut-outs/photos, mockups)
- What's currently running that we should avoid repeating
- Any legal/compliance limits on claims

**Format-specific probes (only if needed):**
- Statics: how many ads; proven hook to adapt; primary visual (text-only, Tony photo, illustration, mockup); single campaign or several ad sets with different audiences
- Carousels: how many cards; educational (one idea per card) or narrative; content series it draws from; hook-card concept (question, bold claim, list teaser, story opener); what the CTA card leads to

**Messaging extraction rule:** If the user provides scripts or copy, extract the hook, key claims and CTA directly. Do not ask them to re-summarize.

**If most context is already in the conversation:** skip asking — extract it and state assumptions at the top of the document. If audience temperature isn't stated for an egelloC webinar, assume COLD and flag "Confirm".

---

## Step 2 — Cold vs Warm: the audience rules

**Cold and warm describe the audience, not the mood.** A cold ad on a cream ground with a reassuring register is still a cold ad. Use the word "warm" in a brief only in the AUDIENCE TEMPERATURE field.

| | Cold | Warm |
|---|---|---|
| Who | California parents (mainly of 9th–10th graders) who have never engaged with egelloC | FB/IG engagers who already know egelloC and Coach Tony |
| Awareness | Unaware → problem-aware | Product-aware |
| They're asking | "Is this for me? Who is this? Why care?" | "Is this one worth my 90 minutes?" |
| Ad's job | Qualify → earn trust → open loop → register | Show payoff → open curiosity loop → register |
| Kind of brief | Mostly new concepts, 2 treatments each | Mostly iterations of a proven winner; visual locked |
| First 2 seconds say | Who it's for + topic (CA parents · 9th/10th · UC/college admissions) | The outcome (acceptances, schools, "5 families got in") |
| Eyebrow / qualifier | Almost always — or the headline names audience + topic | No |
| Credibility | Load-bearing: credibility line or badge on every unit | Light: results + Tony's face carry trust |
| Proof type | Insider credential, shocking stat, the reader's process (8 minutes, 2 vs 6, 60 seconds) | Outcomes: school names, acceptance letters |
| Coach Tony | Credibility cue, not hero. In carousels appears late (usually card 4 of 5). Text-only treatment always briefed alongside photo | Familiar face on the CTA card |
| Emotional register | Chosen per ad: hard truth, quiet dread, insider mystery, recognition, reassurance. Discomfort allowed — must resolve | Hope + curiosity. Aspirational, restrained. No fear agitation |
| Hook moves | Myth-bust · stat shock · insider mystery · regret/time · recognition scene · objection reversal | Surprise reversal ("broken profiles → they all got in") · outcome-first ("Stanford said yes") |
| Default ground | Picked by emotional job (below). Dark common | Light, flat Off White. No gradient/texture |
| Visual hero | The headline. Typography-first; max one supporting device | Headline + one emotional illustration, or pure typography |
| Payoff line | Emphasis on 1–3 words inside the headline | Distinct italic-bold (Inter 800 italic) payoff line under the list |
| CTA wording | "Save your free seat" · "Get the free training" · "Register free" · "Show me how (free)" | "Free live training" · "Register free" |
| Open loop | Never answer the "how" — name it, tease it | Never resolve "what happened" — show the result, withhold the method |

### Cold rules
- **Qualify inside 2 seconds** — eyebrow or first headline line names audience + topic. If the eyebrow is dropped, the headline must name the topic.
- **Credibility on every unit** — *UC Berkeley admissions reader · 10,000+ applications reviewed* closes every cold asset (or sits as a small badge above the headline on photo treatments). Quiet credential, never a giant stat block.
- **Ground by emotional job:**

| Emotional job | Ground (role → token) | Text | Typical hooks |
|---|---|---|---|
| Authority / hard truth / quiet dread | Dark → `--deep` (or `--black` for max starkness) | White, emphasis Yellow | "89% get rejected", "I never met them" |
| Empathy / hope / reassurance | Light → `--off-white` | Deep/Black, emphasis Deep or `#C48B00` | The calm version |
| Curiosity / urgency / punch | Brand → `--yellow` | Deep/Black only | Payoff cards, "find the kid" |

Never yellow type on a light ground; never white type on yellow.
- **Typography is the hero** — headline ~55% of frame; at most one supporting device that *proves* the headline (circled 4.0, 2-vs-6 split, two map pins, closed folder).
- **Two treatments per concept** — Text-only (no photography) + Photo (Tony cut-out right of centre, standing on frame floor, Deep-tinted shadow, credibility badge; headline shifts left). A brief may say **no Tony** when restraint is the point (dramatic/mysterious scenes).
- **Cold never:** stock photos of stressed students/crying parents/campuses/laptops · showing the method (essays, applications, screens) · generic urgency imagery (alarm clocks, stopwatches, sirens) · the word "webinar" on creative · dates or times on creative.

### Warm rules
- **Lead with the outcome** — school names (Stanford, Berkeley, Cornell, USC, Carnegie Mellon) get weight.
- **Light, flat, editorial** — "not an inspirational poster".
- **One emotional anchor or none** — a single flat illustration (hands opening a yellow envelope, ACCEPTED stamp) or pure type. Never student photography; no decoration around the anchor.
- **Italic-bold payoff line** visibly different from the list above it. No second font family.
- **Iterate, don't redesign** — the control is a locked template; only named copy zones change. Never re-break lines by shrinking type — add a line.
- **Warm never:** fear/anxiety hooks paired with success visuals · re-explaining Tony at length · resolving the open loop.

> Warm rules come from a small sample (two briefs from one webinar). Treat them as a starting pattern; note deviations.

---

## Step 3 — Strategic Layer (per unit)

Define strategy before any visual direction. One table per unit.

| Element | Define This |
|---|---|
| **Angle** | Myth-bust / Pain-first / Story / Authority / Curiosity-insider / Aspiration / Contrarian / Benefit-led / Outcome / Surprise reversal |
| **Emotional job** | Cold: authority-hard-truth · empathy-hope · curiosity-urgency. Warm: outcome-hope · surprise-reversal |
| **Emotional trigger** | Fear of loss / Curiosity / Hope / Trust / Urgency / Surprise / Relief / Guilt (light) |
| **Awareness stage** | Unaware → story/surprising fact · Problem aware → agitate · Solution aware → mechanism · Product aware → offer/proof · Most aware → deal/final objection |
| **Job of this ad** | One sentence: stop scroll / open loop / build trust / close offer |

**Rule:** Every ad has ONE job. State it explicitly. Briefs that try to do everything produce creative that does nothing.

### Angle quick guide
- **Myth-busting** — unaware/problem-aware. Common belief → contradict → open loop. Avoid with already-skeptical audiences.
- **Pain-first** — problem-aware. Name pain precisely → agitate → way out. Avoid for cold-unaware entry; never for WARM.
- **Story** — unaware. Scene → tension → lesson → reader. Avoid when audience is in action mode.
- **Authority/Proof** — cold audiences needing trust. Credential → insider insight → their situation.
- **Curiosity/Insider loop** — the insight must be genuinely surprising, not obvious, or the brand loses trust.
- **Aspiration/Identity** — warm and some unaware. Avoid when pain is acute.
- **Contrarian** — saturated audiences. Avoid if it needs too much explanation to land.
- **Benefit-led/Offer** — product-aware/warm; as a closer, not a cold first impression.

### Trigger pairings
Fear of loss → Pain-first, Myth-bust · Curiosity → Insider, Contrarian · Hope → Aspiration, Benefit-led · Trust → Authority · Urgency → Pain-first, specific timelines · Surprise → Contrarian, Myth-bust · Relief → Aspiration, Benefit-led · Guilt (light) → Pain-first, carefully.

### Recommended mixes
- **Cold webinar registration:** Primary Pain-first or Myth-bust + Fear of loss/Curiosity · Secondary Authority + Trust · Closer Aspiration + Hope
- **Warm webinar registration:** Primary Outcome/Surprise reversal + Hope/Curiosity · Secondary Benefit-led ("5 families. 1 pattern. 90 minutes.") · No fear
- **Cold lead magnet:** Story or Myth-bust + Fear of loss/Curiosity · Aspiration + Hope · Benefit-led + Trust
- **Organic awareness:** Curiosity/Insider + Surprise · Aspiration + Hope · avoid heavy pain-first

---

## Step 4 — Copy Blocks

The designer never invents or interprets copy. Put *"Do not alter wording"* at the top of every copy block.

**Static:**

| Element | Text |
|---|---|
| Eyebrow | text or none (cold: usually audience qualifier, e.g. "FOR CALIFORNIA PARENTS OF 9TH & 10TH GRADERS") |
| **Headline** | The visual hero, with [brackets] around emphasis words |
| Sub / body | 1–2 lines max |
| Payoff line | text or none (warm: italic bold) |
| Credibility | default line / badge / none — **cold must not be none** |
| CTA | exact wording, action-oriented |

**Carousel:** `Card | Role | Headline | Body | Ground (role) | Swipe/CTA`. Note any temperature arc in one line.

**Copy iteration:** list only the zones that change per version and state "everything else matches the control".

**Copy conventions:**
- **Emphasis in [brackets]** — only bracketed words get the accent; 1–3 words per headline. Accent colour follows the ground (yellow only on dark grounds).
- Say **"free live training"**, never "webinar", on creative.
- **No dates or times** on creative — the landing page handles logistics.
- No emoji or Unicode ticks — use Lucide `check` / `arrow-right` glyphs.
- One idea per unit. If a static needs two paragraphs, it's a carousel.
- Label A/B variants explicitly: VERSION A / VERSION B.

---

## Step 5 — Visual Direction

Specific enough that a designer in another city executes it without a call. Cover:

- **Ground** — by role (dark / light / brand), never a hex. Flat unless stated. If photo: subject, mood, composition, what not to use.
- **Layout** — zones (top/middle/bottom or left/right), what lives where, proportions (e.g. headline ~55%), alignment.
- **Typography** — Inter 800 headlines, 400 body. Size dominance, which words get emphasis and how, body weight/colour relative to headline. Casing per Design System.
- **Imagery / treatment** — text-only (state "no imagery, typography is the visual hero") / Tony photo / both / illustration / mockup. For photos: subject, angle, expression, wardrobe, what to avoid. For mockups: placement, size, angle, shadow. For illustration: style and what it depicts. State **Tony usage explicitly**: none · photo treatment · card N only.
- **Supporting device** — one item, or none. It proves the headline, never competes.
- **Brand elements** — logo placement and colourway per Design System (dual yellow/white on Deep/Navy, black on Yellow, full colour on Off White); credibility line/badge; brand colour as ground, accent or CTA.
- **CTA** — Design System yellow pill, uppercase (unless the control is a locked warm template using a rectangle — keep the control).
- **Mood** — 2–3 precise adjectives + what to avoid aesthetically. "Modern" alone is not direction.

### Token translation (when a source brief names a hex or font)

| Brief says | Use (DS) |
|---|---|
| Yellow/gold/amber — `#F5B800`, `#F5C200`, `#F5C518`, `#F5C842`, `#FABF32` | `--yellow` #FABF32 |
| Navy/near-black — `#1C2340`, `#1a1a2e`, `#0D1B2A`, `#0E0E0E`, `#1A1A1A`, `#1E1E00` | Dark → `--deep` #1E1E00. `--navy` #1B2340 only where navy is needed as a distinct field |
| Black `#000000` | `--black` |
| Cream/off-white — `#F5F0E8`, `#F5F2ED`, `#FAF7F2`, `#F5F5F0`, `#F8F8F8` | `--off-white` #F8F8F8 |
| White | `--white` #FFFFFF |
| Muted grey on dark | White for body on Deep; muted grey only for swipe cue |
| Calibri, Montserrat, "bold sans" | Inter 800 / 400 |
| Red X, red stamp, red bars | No red in the system. Navy for problem states, or the DS "Apple rule" for one realistic element — **flag it** |

---

## Step 6 — Carousel Architecture

**Cold (4–5 cards) — dark bookends, light middle:**

| Card | Role | Ground |
|---|---|---|
| 1 | Hook — headline only + swipe cue | Dark |
| 2–3 | Agitate / reframe / the trap — the viewer's own thoughts read back | Light |
| 4 | Turn + tease or insider reveal — Tony appears here if at all; teases named, never explained | Light |
| 5 | Offer — free live training + CTA | Dark |

A brief may instead run a **temperature arc** (warm photo → cold stark → warm resolution, or dense card vs airy card). Honour it: the contrast between cards is the message, so cards must not look alike.

**Warm (4 cards):**

| Card | Role |
|---|---|
| 1 | Scroll-stopper — broken profiles → surprise reversal (the card that gets iterated) |
| 2 | Mechanism — what the reader needs to see |
| 3 | Personal stakes — "does your kid follow the pattern or break it?" |
| 4 | CTA — Tony photo + compressed offer + CTA |

Cards 1–3 text-only, centred; Tony on card 4 only.

**All carousels:** every card works standalone (users can enter from any card); one idea per card; progress dots top-right (active = Yellow); swipe cue bottom-right in muted grey; first card is the only one that must stop the scroll.

---

## Step 7 — Visual Hierarchy

Numbered, one line per element, in the order the eye travels:
```
1. Headline — dominant, first read
2. Supporting device / Tony — proves the headline
3. Credibility line or badge
4. CTA
```

---

## Step 8 — Layout Sketch

ASCII diagram for every unit (every card for carousels). Non-negotiable — removes all spatial ambiguity.

Conventions: `[brackets]` = visual elements · plain text = copy · ALL CAPS = dominant text · note the ground role above the sketch.

```
Ground: dark
┌─────────────────────────────┐
│ [logo — top left, small]     │
│ FOR CALIFORNIA PARENTS OF    │
│ 9TH & 10TH GRADERS           │
│                              │
│  THE HEADLINE WITH           │
│  [EMPHASIS] WORDS            │
│                              │
│  [one supporting device]     │
│  UC Berkeley admissions      │
│  reader · 10,000+ apps       │
│  [CTA — yellow pill]         │
└─────────────────────────────┘
```

---

## Step 9 — What NOT To Do

3–5 specific "do not" lines per unit — the failure modes *this* concept invites, not generic filler. Include the relevant cold/warm "never" items. Examples:
- "Do not use stock photos of stressed students or crying parents — keep it typographic"
- "Do not show an essay or application — the 'how' stays in the training"
- "Do not reduce headline size to fit — add a line instead"
- "Do not add decorative gradients or patterns — flat colour only"
- "Do not pair this success visual with a fear line" (warm)
- "Do not resolve the curiosity gap in the visual — tension drives the click"

---

## Step 10 — Iteration Briefs

**COPY ITERATION** — name the control file; list only changing zones per version; "everything else matches the control".

**BACKGROUND ROUND** — copy, font and layout frozen, pixel-identical. Produce the grounds other than the control's:

| Control ground | Produce |
|---|---|
| Deep | Off White · Yellow · Navy (if approved as a test field) |
| Off White | Deep · Yellow · Navy |
| Yellow | Deep · Off White · Navy |

Text/emphasis colours change only where legibility requires it; emphasis stays on the same words; logo follows DS colourways.

**RESIZE** — re-flow inside the DS template; never stretch. Strip any date/time from older creative before reuse.

---

## Step 11 — Deliverables Checklist

Close every brief with:

```
## Deliverables

### Static Ads ([X] total)
- [ ] [Unit ID — name] — text-only — 1080×1080 — PNG
- [ ] [Unit ID — name] — Tony photo — 1080×1080 — PNG

### Carousels ([X] total)
- [ ] [Unit ID — name] — [X] cards — 1080×1080 per card — PNG per card + PDF for review

### Assets — confirmed with designer
- [x] [asset the designer already has]

### Assets — needed before starting
- [ ] [asset still to be provided]
```

### Format specs

| Placement | Size | Notes |
|---|---|---|
| Feed square (default) | 1080×1080 | Text + key visuals in centre 80% |
| Feed portrait | 1080×1350 | Preferred on mobile when specified |
| Landscape | 1200×628 | Only when specified |
| Stories/Reels | 1080×1920 (or 1440×2560) | Keep top 14% and bottom 20% clear; active area centre 66%. Only when requested |
| Carousel card | Same as feed | Up to 10 cards |

PNG for text-heavy ads, JPG acceptable for photo-dominant. Max 30MB. 9:16 statics: mention safe zones and flag that the DS has no 9:16 static template yet.

---

## Brief Template

Every brief starts with:
```
CAMPAIGN:             [e.g. "Beyond the GPA" free live training]
AUDIENCE TEMPERATURE: COLD | WARM
AUDIENCE:             [who, grade, state, persona]
AWARENESS STAGE:      [unaware | problem-aware | solution-aware | product-aware]
BRIEF TYPE:           NEW CONCEPT | COPY ITERATION | BACKGROUND ROUND | RESIZE
CONTROL FILE:         [link — required for iterations/rounds/resizes]
DESTINATION:          [registration page URL]
FORMAT / SIZE:        [1080×1080 default …]
UNITS:                [S1 static (text-only + photo), C1 carousel 5 cards, …]
SOURCE SCRIPT:        [script ID, if any]
ASSUMPTIONS:          [anything inferred — mark "Confirm"]
```

Followed by a short **Brand reference** section (Design System link, logo colourways, credibility line, Tony assets available), then one block per unit:
```
UNIT [ID] — [STATIC | CAROUSEL] — "[working name]"

STRATEGY        Angle · Emotional job · Trigger · Awareness · Job of this ad
COPY            (Do not alter wording) Eyebrow · Headline [emphasis] · Sub · Payoff · Credibility · CTA
VISUAL          Ground (role) · Treatment · Tony usage · Supporting device · Layout · Typography · Brand · Mood
HIERARCHY       1. … 4. CTA
SKETCH          ASCII
DO NOT          3–5 lines
```

---

## Brief Quality Checklist

Before generating output files, verify:

- [ ] Header complete; AUDIENCE TEMPERATURE stated as COLD or WARM (no other use of "warm")
- [ ] Brief type stated; control file linked for iterations/rounds/resizes
- [ ] Assumptions stated at top if intake was inferred
- [ ] Brand reference section at the top of the document
- [ ] Every unit has its own section: strategy, copy ("do not alter"), visual direction, hierarchy, ASCII sketch, Do-not list
- [ ] Visual direction covers ground, layout, typography, imagery, brand, mood
- [ ] Emphasis marked in [brackets], 1–3 words
- [ ] Grounds named by role, no new hex values
- [ ] Tony usage explicit per unit
- [ ] Cold: audience + topic visible in 2 seconds; credibility on every unit; text-only + photo treatments briefed
- [ ] Warm: outcome-first headline; no fear hook with a success visual; control locked
- [ ] No "webinar", no dates/times, no emoji, no stock student photos on creative
- [ ] CTA wording explicit in every unit
- [ ] Sizes listed; 9:16 mentions safe zones
- [ ] Deliverables checklist separates confirmed vs needed assets
- [ ] No vague direction left unresolved
- [ ] Both `.md` and `.pdf` saved to `/mnt/user-data/outputs/` and delivered

---

## Open Decisions (flag in briefs until resolved)

1. Background-round colour fields — briefs used Navy `#1a1a2e`, `#FAF7F2`, `#F5C200`; mapped to DS tokens until confirmed.
2. Credibility line on warm creative — DS requires it; warm winners omit it. Default: follow the control, flag.
3. CTA shape — DS pill vs warm winners' full-width yellow rectangle. Default: pill for new concepts, keep the control's shape for iterations.
4. Headline casing — some cold briefs use all caps; DS says sentence case on statics. Default: DS, flag.
5. 9:16 statics — no DS template yet.
6. Majors Webinar and Winner Ads Fast Iterations — assumed cold; confirm.
