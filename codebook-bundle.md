# Once Codebook v1.0 — Distribution Bundle

> Single-file distribution of the entire Once Codebook v1.0 specification.
> Repository: https://github.com/sudhinkrishna/once-profile
> Bundle generated: 2026-04-26
> License: MIT

---

## What this file is

This is the **entire Once Codebook v1.0** in one document — README, all 20
psychological parameter definitions, all 270 lookup codes (S/T/X/C), the JSON
schemas, and the standard prompts — concatenated in the order an AI should
read them.

## Why it exists

The canonical codebook lives as 25+ files across folders on GitHub. Most AI
assistants (free ChatGPT, custom GPTs, locally hosted models, anything with
unreliable web access) cannot fetch a multi-file repository at runtime. This
bundle solves that — you can paste it directly into any chat, attach it to a
Claude Project / ChatGPT custom GPT / Gemini Gem, or feed it to a local model.

## How to use it

**With an AI that can browse:** point it at this single file's raw URL and
proceed with the build prompt at the end.

**With an AI that can't browse:** paste this entire file as your first message
(or attach it as a file), then send the build prompt as your second message.

The build prompt is at the bottom of this bundle, ready to use.

## What's in this bundle (in order)

1. README — overview, encoding syntax, parameter index
2. Parameters P01–P20 — full tier definitions for all 80 sub-dimensions
3. Codebook S — 150 behavioural signals
4. Codebook T — 60 triggers
5. Codebook X — 60 expressions
6. Codebook C — consistency scale
7. Schema — dimension record JSON + worked example
8. Prompts — build, update, compare

## What's NOT in this bundle

- `review/` — community proposal governance, not part of the spec
- `.git/` history


==============================================================================
  PART 1 — README
==============================================================================

# Once Profile Codebook

> A universal open standard for encoding human compatibility profiles.

---

## What is this?

The Once Codebook is an open specification for representing who someone is — across **20 psychological parameters**, **80 sub-dimensions**, and **270 behavioural signal codes** — in a structured format that any AI can read, build, and compare.

It was designed for [Once](https://github.com/once-profile) — a weekly matchmaking app that connects one person to one other person every week, based on deep compatibility rather than surface-level preferences. But the codebook itself is open. Any AI, any platform, any developer can use it.

---

## The problem it solves

Every time you start a conversation with a new AI — ChatGPT, Gemini, Claude, Perplexity — it knows nothing about you. You start from zero. The Once Codebook gives you a portable, structured profile that any AI can read and immediately understand.

More importantly, it gives matchmaking systems a common language for compatibility — one that goes far deeper than "likes hiking" or "wants kids."

---

## How it works

A Once profile is built in three layers:

### Layer 1 — Detailed natural language profile
An AI observes your conversations over time and builds a rich natural language description of who you are across 20 parameters. No questions asked. Pure observation.

### Layer 2 — Structured dimension records
Each sub-dimension is stored as a structured record referencing codes from the codebook:

```json
{
  "id": "P1a",
  "pos": "B",
  "int": 4,
  "con": "C3",
  "bsig": ["S001", "S002", "S005"],
  "trg": ["T002"],
  "exp": ["X001"],
  "conf": 3,
  "upd": "20260424"
}
```

### Layer 3 — Encoding string
The entire profile compressed into a portable alphanumeric string:

```
P1a·B4★ P1b·B3★ P1c·B4★ P1d·C3★ | P2a·B4~ P2b·C3~ ...
```

---

## Codebook v1.0 — What's included

### Primary series

| Series | Name | Description | Count |
|--------|------|-------------|-------|
| **P** | Psychological parameters | 20 parameters × 4 sub-dimensions | 80 sub-dims |
| **D** | Descriptive dimensions | Factual attributes — location, profession, interests | 12 dims |

### Lookup series

| Series | Name | Description | Seed count |
|--------|------|-------------|------------|
| **S** | Behavioural signals | Observable behaviours inferred from conversation | 150 codes |
| **T** | Triggers | What someone can't tolerate — reveals values | 60 codes |
| **X** | Expressions | How values and traits manifest in behaviour | 60 codes |
| **C** | Consistency scale | How stable a trait is across contexts | C1–C5 |
| **CONF** | Confidence markers | Signal strength per dimension | ★ ~ ? |

**Total seed codes: 270**

### Reserved for v2

| Series | Name | Description |
|--------|------|-------------|
| **R** | Relationship history | Past relationship patterns and learnings |
| **G** | Growth signals | What someone is actively building toward |
| **M** | Match outcome data | Real-world match success signals |

---

## The 20 psychological parameters

| Code | Parameter | Sub-dimensions |
|------|-----------|----------------|
| P1 | Values and worldview | Political orientation, gender role views, moral framework, social justice orientation |
| P2 | Emotional temperament | Expressiveness, emotional stability, empathy level, sensitivity to criticism |
| P3 | Life goals | Where they want to live, relationship type, personal growth priority, timeline urgency |
| P4 | Social style | Introvert vs extrovert, social circle size, need for alone time, social spontaneity |
| P5 | Intellect and curiosity | Curiosity breadth, love of learning, debate style, creative thinking |
| P6 | Conflict style | Confrontation comfort, resolution approach, forgiveness speed, stubbornness |
| P7 | Attachment style | Base type, closeness comfort, independence need, trust building speed |
| P8 | Practical lifestyle | Travel, financial habits, daily rhythm, living style |
| P9 | Love language | Primary give, primary receive, affection frequency, physical affection comfort |
| P10 | Anger and mood management | Expression style, trigger sensitivity, cooldown time, mood contagion |
| P11 | Altruism and kindness | Generosity, stranger kindness, cause orientation, reciprocity expectation |
| P12 | Dominance vs submissiveness | Decision-making, opinion assertiveness, compromise willingness, leadership |
| P13 | Sense of humour | Style, frequency, self-deprecation comfort, humour boundaries |
| P14 | Emotional availability | Openness timing, vulnerability comfort, support style, emotional bandwidth |
| P15 | Family orientation | Want children, family centrality, parenting style, extended family involvement |
| P16 | Ambition and career | Career centrality, ambition level, work-life balance, financial ambition |
| P17 | Spirituality and religion | Religious identity, practice frequency, partner expectation, spiritual worldview |
| P18 | Physical lifestyle | Fitness orientation, health consciousness, substance use, outdoor vs indoor |
| P19 | Communication style | Directness, conversation depth, digital communication, listening style |
| P20 | Openness to change | Adaptability, opinion flexibility, risk tolerance, growth mindset |

---

## Encoding syntax

Each sub-dimension is encoded as:

```
P[parameter number][sub-dimension letter]·[Tier][Level][Confidence]
```

**Example:** `P5a·A5★`
- `P5` — Parameter 5 (Intellect and curiosity)
- `a` — Sub-dimension a (Curiosity breadth)
- `A` — Tier A (highest end of spectrum)
- `5` — Level 5 (maximum intensity within tier)
- `★` — Strong signal (confirmed across multiple conversations)

### Tiers (A–E)
Tier meaning is **dimension-specific** — A means the highest intensity position on that dimension's unique spectrum. Each parameter file defines what A through E means for each sub-dimension.

### Levels (1–5)
Granularity within a tier. 5 = strongest expression of that tier position.

### Confidence markers

| Marker | Meaning | Match weight |
|--------|---------|--------------|
| ★ | Strong signal — confirmed clearly across multiple signals | 100% |
| ~ | Inferred — reasonable inference from indirect signals | 50% |
| ? | Unknown — insufficient data, excluded from matching | 0% |

### Consistency scale (C codes)

| Code | Meaning |
|------|---------|
| C1 | Rigid — never wavers |
| C2 | Stable — rarely shifts |
| C3 | Evidence-responsive — shifts with good reason |
| C4 | Contextual — varies by situation |
| C5 | Volatile — shifts frequently |

---

## Using this codebook with any AI

Point any AI with web access at this repository and use this prompt:

```
Read the Once Codebook at github.com/once-profile/codebook.

Using the full specification — P parameters, D dimensions, 
S/T/X codes, C consistency scale, and confidence markers — 
build my Once profile from our conversation history.

Rules:
- Do NOT ask me any questions
- Observe only from what I have naturally said
- Assign confidence honestly — use ? when uncertain
- Output my full encoding string
- Below it, note which S codes you found strongest 
  and which dimensions need more signal

Begin.
```

---

## Repository structure

```
once-profile/
├── README.md                    — This file
├── SPEC.md                      — Full encoding specification
├── CHANGELOG.md                 — Version history
├── CONTRIBUTING.md              — How to propose new codes
│
├── parameters/
│   ├── P01_values_worldview.md
│   ├── P02_emotional_temperament.md
│   └── ... P03 through P20
│
├── codebook/
│   ├── S_signals.md             — 150 behavioural signal codes
│   ├── T_triggers.md            — 60 trigger codes
│   ├── X_expressions.md         — 60 expression codes
│   └── C_consistency.md         — Consistency scale
│
├── schema/
│   ├── dimension_record.json    — Schema for one sub-dimension
│   ├── profile_record.json      — Schema for a complete profile
│   └── example_profile.json     — Anonymised example
│
├── prompts/
│   ├── build_profile.md         — Prompt to build a profile
│   ├── update_profile.md        — Prompt to update a profile
│   └── compare_profiles.md      — Prompt to compare two profiles
│
└── review/
    ├── proposed_codes.md        — Community proposals awaiting review
    └── rejected_codes.md        — Rejected codes with reasons
```

---

## Contributing

The codebook grows through community review — not open-ended expansion. New S, T, and X codes can be proposed via pull request to `review/proposed_codes.md`.

Every proposal must include:
- Proposed code ID (next available number)
- Description (maximum 15 words)
- Which P parameters it applies to
- An example of how it would appear in natural conversation

The Once team reviews all proposals within 7 days. Approved codes are merged into the main codebook with the next minor version. Rejected codes are moved to `rejected_codes.md` with a reason.

**Before proposing:** check existing codes carefully. Duplicates will be rejected.

---

## Versioning

Every profile record stores the codebook version it was built against. This ensures old profiles remain valid when the codebook updates.

- **Patch (v1.0.x)** — Typo fixes, description clarifications. No profile migration needed.
- **Minor (v1.x.0)** — New codes added. Existing profiles unaffected.
- **Major (v2.0.0)** — Breaking changes to schema or parameters. Migration guide provided.

---

## Licence

The Once Codebook is released under the [MIT Licence](LICENSE). Use it freely. Build on it. Give credit.

---

*Built by [Once](https://github.com/once-profile) — one person, one week, one real connection.*


==============================================================================
  PART 2 — PARAMETERS (P01–P20)
==============================================================================

The 20 psychological parameters. Each parameter has 4 sub-dimensions (a, b, c, d), each with a 5-tier scale (A–E) and 5 intensity levels (1–5). When building a profile, every sub-dimension must be assigned a tier+level+confidence — or marked `?` if signal is insufficient.


------------------------------------------------------------------------------
FILE: parameters/P01_values_worldview.md
------------------------------------------------------------------------------

# P1 — Values and Worldview

Values and worldview describe a person's fundamental orientation toward
politics, ethics, gender, and social justice. These are among the strongest
predictors of long-term compatibility.

**Dealbreaker potential: High**
**Codebook version:** v1.0

---

## P1a — Political orientation

| Tier | Description |
|------|-------------|
| A | Strongly progressive / left — ideology-driven, activist orientation |
| B | Centre-left — leans progressive, evidence-responsive, non-ideological |
| C | Genuinely centrist — case by case, resists both sides |
| D | Centre-right — leans conservative, pragmatic |
| E | Strongly conservative / right — ideology-driven, tradition-focused |

**Matching:** Seek similarity. A and E are likely dealbreaker mismatch.

---

## P1b — Gender role views

| Tier | Description |
|------|-------------|
| A | Fully egalitarian — actively challenges traditional roles in all contexts |
| B | Largely egalitarian — comfortable with equality, some traditional comfort |
| C | Balanced — context-dependent, neither traditional nor fully egalitarian |
| D | Leans traditional — some modern acceptance, mostly conventional |
| E | Strongly traditional — clear defined roles, non-negotiable |

**Matching:** Seek similarity. Large gaps create friction in daily life.

---

## P1c — Moral framework

| Tier | Description |
|------|-------------|
| A | Pure consequentialist — outcomes and impact matter most |
| B | Balanced — evidence, ethics, and outcomes considered together |
| C | Principled — rules and principles matter but with nuance |
| D | Duty-based — clear moral rules, less flexible |
| E | Dogmatic — fixed moral code, non-negotiable, often religious |

**Matching:** B and C are broadly compatible. A and E are likely mismatch.

---

## P1d — Social justice orientation

| Tier | Description |
|------|-------------|
| A | Activist — deeply involved, cause-driven, systemic focus |
| B | Engaged — aware, vocal when it matters, not activist |
| C | Aware — informed but largely private about it |
| D | Passive — limited engagement, personal focus only |
| E | Disengaged or opposed to social justice framing |

**Matching:** Seek similarity on A and E ends. B/C broadly compatible.


------------------------------------------------------------------------------
FILE: parameters/P02_emotional_temperament.md
------------------------------------------------------------------------------

# P02 — Emotional Temperament

Emotional temperament describes how a person experiences, expresses, and
regulates feelings day to day. It governs the emotional rhythm of a
relationship and is one of the strongest predictors of daily friction.

**Dealbreaker potential:** Medium
**Codebook version:** v1.0

---

## P02a — Expressiveness

| Tier | Description |
|------|-------------|
| A | Wears every emotion openly — laughter, tears, anger all visible in real time |
| B | Generally expressive — shows feelings naturally, not performative |
| C | Selectively expressive — open with close people, reserved otherwise |
| D | Reserved — keeps most feelings private, expresses only when significant |
| E | Highly contained — rarely shows emotion, processes internally, can read as flat |

**Matching:** Adjacent tiers compatible. A with E creates persistent miscommunication — A feels stonewalled, E feels overwhelmed.

---

## P02b — Emotional stability

| Tier | Description |
|------|-------------|
| A | Rock-steady — even-keel through stress, rarely emotionally reactive |
| B | Mostly stable — handles most things calmly, occasional ups and downs |
| C | Moderate — normal emotional responses to circumstances |
| D | Reactive — moods shift with events, recovery takes effort |
| E | Volatile — strong emotional swings, hard to predict day to day |

**Matching:** Seek similarity. A with E is likely mismatch — the steady one feels pulled into chaos, the volatile one feels unseen.

---

## P02c — Empathy level

| Tier | Description |
|------|-------------|
| A | Highly empathic — picks up subtle emotional shifts often before words |
| B | Strongly empathic — actively notices and responds to others' feelings |
| C | Standard — empathetic when situation calls for it |
| D | Cognitive empathy — understands feelings logically more than feels them |
| E | Low empathy — struggles to read or respond to emotional cues |

**Matching:** Seek similarity. Gaps wider than two tiers leave one partner feeling emotionally unseen.

---

## P02d — Sensitivity to criticism

| Tier | Description |
|------|-------------|
| A | Highly sensitive — even soft critique cuts deep, takes time to recover |
| B | Sensitive — feels critique strongly but processes it constructively |
| C | Balanced — accepts fair critique, pushes back on unfair |
| D | Low sensitivity — takes critique pragmatically, moves on quickly |
| E | Largely unfazed — rarely affected by criticism, can read as dismissive |

**Matching:** A with D or E creates ongoing friction — the sensitive partner needs care, the insensitive one struggles to provide it.


------------------------------------------------------------------------------
FILE: parameters/P03_life_goals.md
------------------------------------------------------------------------------

# P03 — Life Goals

Life goals describe the shape of the future a person is building toward —
where they want to live, what kind of relationship they want, how central
self-development is, and how quickly they want major milestones. Mismatched
life goals are the most common reason long-term relationships fail.

**Dealbreaker potential:** High
**Codebook version:** v1.0

---

## P03a — Where they want to live

| Tier | Description |
|------|-------------|
| A | Locked-in to current city — strong roots, no intention to move |
| B | Prefers a specific country or region — willing to move within it |
| C | Open — willing to relocate for work, partner, or opportunity |
| D | Internationally mobile — happy to live anywhere with right reasons |
| E | Nomadic — actively wants no fixed home, moves frequently by choice |

**Matching:** Critical alignment for cohabiting. A with D or E is a likely dealbreaker.

---

## P03b — Relationship type

| Tier | Description |
|------|-------------|
| A | Marriage, traditional structure — defined long-term, expects family |
| B | Marriage, modern — committed long-term, flexible on roles and family |
| C | Long-term partnership — committed but marriage not essential |
| D | Open commitment — exclusive but no long-term lock-in expected |
| E | Casual or non-monogamous — multiple partners or no exclusivity expectation |

**Matching:** Seek similarity. A with E is incompatible. Adjacent tiers can work with explicit conversation.

---

## P03c — Personal growth priority

| Tier | Description |
|------|-------------|
| A | Growth is core identity — actively learning, training, evolving year-round |
| B | High priority — regular learning and self-work, not all-consuming |
| C | Steady — grows when needed, otherwise lives life as it comes |
| D | Stable — content with current self, occasional growth phases |
| E | Static — rejects personal growth framing as overrated or unnecessary |

**Matching:** A with D or E creates tension — the growth-oriented partner can feel held back or alone in the work.

---

## P03d — Timeline urgency

| Tier | Description |
|------|-------------|
| A | Urgent — wants marriage, kids, house in next 1–2 years |
| B | Soon — clear timeline of 2–5 years for major milestones |
| C | Moderate — 5–7 year horizon, flexible on order and timing |
| D | Slow — no rush, lets life unfold organically |
| E | No timeline — actively rejects milestone framing |

**Matching:** Critical to align. Mismatched timelines are the most common cause of late-stage breakups. Treat A with D/E as dealbreaker.


------------------------------------------------------------------------------
FILE: parameters/P04_social_style.md
------------------------------------------------------------------------------

# P04 — Social Style

Social style describes how a person draws and spends social energy — whether
they're recharged by people or by solitude, how large a circle they
maintain, and how spontaneous they are about plans. It governs the daily
rhythm of cohabitation more than almost any other parameter.

**Dealbreaker potential:** Medium
**Codebook version:** v1.0

---

## P04a — Introvert vs extrovert

| Tier | Description |
|------|-------------|
| A | Strong extrovert — energised by people, drained by solitude |
| B | Mild extrovert — prefers company, comfortable alone |
| C | Ambivert — balanced, depends on mood and context |
| D | Mild introvert — recharges alone, enjoys company in moderation |
| E | Strong introvert — deeply needs solitude, social events are taxing |

**Matching:** Adjacent tiers compatible. A with E creates fundamental rhythm conflict — every weekend is a negotiation.

---

## P04b — Social circle size

| Tier | Description |
|------|-------------|
| A | Wide network — dozens of close-ish friends, constant social plans |
| B | Broad — 15–25 people they actively maintain |
| C | Mid-sized — 8–15 close friends, plus acquaintances |
| D | Tight — 3–7 close friends, doesn't seek more |
| E | Minimal — 1–3 deeply close people, no broader circle |

**Matching:** Loose. Different sizes can coexist if both partners respect the other's circle.

---

## P04c — Need for alone time

| Tier | Description |
|------|-------------|
| A | Minimal — rarely needs alone time, prefers company always |
| B | Some — likes solitude occasionally, defaults to company |
| C | Balanced — alternates regularly between alone and social |
| D | High — needs daily solitude, protects alone time fiercely |
| E | Maximal — solitude is core to functioning, social time is rationed |

**Matching:** Adjacent tiers fine. A with D or E creates daily friction over how evenings and weekends are spent.

---

## P04d — Social spontaneity

| Tier | Description |
|------|-------------|
| A | Loves spontaneity — drops plans, says yes to last-minute invites |
| B | Open — comfortable with spontaneous plans, prefers some notice |
| C | Mixed — likes some spontaneity, plans most things |
| D | Plans-first — prefers scheduling, mild spontaneity OK |
| E | Rigid — strong preference for scheduled, dislikes last-minute changes |

**Matching:** Adjacent tiers fine. A with E creates ongoing friction in everyday decisions.


------------------------------------------------------------------------------
FILE: parameters/P05_intellect_curiosity.md
------------------------------------------------------------------------------

# P05 — Intellect and Curiosity

Intellect and curiosity describe how a person engages with ideas — how broadly
their interests range, how strongly they're driven to learn, how they handle
disagreement of ideas, and how creatively they think. Long-term partners
need a roughly compatible intellectual rhythm to keep talking after the
honeymoon phase ends.

**Dealbreaker potential:** Medium
**Codebook version:** v1.0

---

## P05a — Curiosity breadth

| Tier | Description |
|------|-------------|
| A | Polymath — deeply curious across many unrelated fields |
| B | Broad — multiple active interests across domains |
| C | Focused-broad — 2–3 main domains, occasional excursions |
| D | Focused — primarily interested in 1–2 areas, deep within them |
| E | Narrow — one or two interests, content with that |

**Matching:** Loose. Both partners need *some* curiosity, but breadth itself isn't critical — depth-focused partners can pair well with broad ones.

---

## P05b — Love of learning

| Tier | Description |
|------|-------------|
| A | Constant learner — always reading, taking courses, picking up skills |
| B | Active — regular reading and learning, structured habits |
| C | Steady — learns as needed for work and interests |
| D | Pragmatic — learns when there's a clear reason, not for its own sake |
| E | Static — content with current knowledge, sees learning as work |

**Matching:** Seek similarity. A with E creates intellectual loneliness — the learner feels they've outgrown the partner.

---

## P05c — Debate style

| Tier | Description |
|------|-------------|
| A | Loves debate — actively seeks intellectual sparring, plays devil's advocate |
| B | Engages — willing to debate when it matters, civil and curious |
| C | Discusses — explores ideas conversationally, avoids combat |
| D | Avoids debate — prefers agreement or polite disagreement |
| E | Rejects debate — sees argument as unpleasant, not productive |

**Matching:** A with D or E creates sharp friction — A wants the spar, the other experiences it as aggression.

---

## P05d — Creative thinking

| Tier | Description |
|------|-------------|
| A | Highly generative — constantly producing novel ideas, prototypes, frames |
| B | Creative — frequently has original takes and ideas |
| C | Selectively creative — original in specific domains, conventional in others |
| D | Practical — values working ideas over novel ones |
| E | Conventional — strongly prefers established approaches |

**Matching:** Loose. A with D can actually work well — the creative partner generates, the practical partner ships.


------------------------------------------------------------------------------
FILE: parameters/P06_conflict_style.md
------------------------------------------------------------------------------

# P06 — Conflict Style

Conflict style describes how a person handles disagreement and rupture in
close relationships — whether they engage or avoid, how they resolve, how
quickly they forgive, and how rigidly they hold positions. Compatibility
here determines whether arguments resolve or accumulate.

**Dealbreaker potential:** Medium-High
**Codebook version:** v1.0

---

## P06a — Confrontation comfort

| Tier | Description |
|------|-------------|
| A | Seeks confrontation — addresses issues immediately, even welcomes them |
| B | Comfortable confronting — raises issues clearly when they matter |
| C | Confronts when needed — prefers to avoid but will engage |
| D | Avoids confrontation — hopes issues resolve themselves, raises them late |
| E | Conflict-averse — suppresses to maintain peace, even at personal cost |

**Matching:** A with E creates a chase-withdraw pattern that rarely heals on its own. Adjacent tiers compatible.

---

## P06b — Resolution approach

| Tier | Description |
|------|-------------|
| A | Direct problem-solver — focuses on what to fix, action-oriented |
| B | Discusses thoroughly — wants to understand before fixing |
| C | Mixed — adapts approach to situation |
| D | Emotional first — needs feelings acknowledged before solutions |
| E | Withdraws to process — needs space, returns once calm |

**Matching:** A with D needs translation work — A reads D as stuck, D reads A as cold. A with E generates frustration on both sides.

---

## P06c — Forgiveness speed

| Tier | Description |
|------|-------------|
| A | Quick to forgive — moves past hurt fast, doesn't hold grudges |
| B | Forgives readily — needs acknowledgment, then moves on |
| C | Moderate — forgives with time and visible repair effort |
| D | Slow — forgiveness takes weeks, repeated apologies needed |
| E | Holds long — bookmarks hurts, raises them in future conflicts |

**Matching:** A with E feels exhausting from both sides. Adjacent tiers manageable.

---

## P06d — Stubbornness

| Tier | Description |
|------|-------------|
| A | Highly flexible — readily updates position when shown new view |
| B | Open — willing to shift on most things |
| C | Selectively firm — holds ground on values, flexible on rest |
| D | Stubborn — rarely changes position once formed |
| E | Immovable — fixed positions, sees changing mind as weakness |

**Matching:** Two stubborn partners (D-D, D-E, E-E) deadlock often. A with D usually balances well.


------------------------------------------------------------------------------
FILE: parameters/P07_attachment_style.md
------------------------------------------------------------------------------

# P07 — Attachment Style

Attachment style describes how a person bonds in close relationships, drawn
loosely from attachment theory. It shapes the underlying emotional
architecture of the relationship — how close, how independent, how trusting,
how soon.

**Dealbreaker potential:** Medium-High
**Codebook version:** v1.0

---

## P07a — Base attachment type

| Tier | Description |
|------|-------------|
| A | Anxious — seeks frequent reassurance, fears distance |
| B | Anxious-leaning secure — secure most of the time, anxious under stress |
| C | Secure — comfortable with intimacy and autonomy |
| D | Avoidant-leaning secure — secure but values independence highly |
| E | Avoidant — uncomfortable with deep intimacy, distances when close |

**Matching:** Secure (C) pairs well with all. A with E is the classic anxious-avoidant trap and rarely resolves without active work.

---

## P07b — Closeness comfort

| Tier | Description |
|------|-------------|
| A | Wants very high closeness — daily contact, shared time, fused life |
| B | High closeness — frequent contact, mostly shared rhythm |
| C | Balanced — close but with separate space |
| D | Lower closeness — values relationship but with strong own life |
| E | Minimal closeness — comfortable with significant distance |

**Matching:** Adjacent tiers compatible. A with D or E creates daily strain.

---

## P07c — Independence need

| Tier | Description |
|------|-------------|
| A | Highly independent — needs significant autonomous space, separate friends, separate hobbies |
| B | Independent — values own life within partnership |
| C | Balanced — interdependent |
| D | Companionable — prefers shared activities and joint decisions |
| E | Strongly companionable — most things done together |

**Matching:** Mismatch produces the same daily strain as P07b mismatch — they're closely linked.

---

## P07d — Trust building speed

| Tier | Description |
|------|-------------|
| A | Trusts quickly — open early, gives benefit of doubt |
| B | Trusts readily — opens up over weeks |
| C | Moderate — trusts gradually over months |
| D | Slow — trust takes a year or more, tested first |
| E | Guarded — trust takes years, may never fully open |

**Matching:** A with E creates a frustrating dynamic — A feels held at distance, E feels rushed.


------------------------------------------------------------------------------
FILE: parameters/P08_practical_lifestyle.md
------------------------------------------------------------------------------

# P08 — Practical Lifestyle

Practical lifestyle describes the day-to-day texture of how someone lives —
travel, money, schedule, home. Surface-level on the surface, but daily
friction compounds and is one of the top reasons cohabitation fails.

**Dealbreaker potential:** Medium
**Codebook version:** v1.0

---

## P08a — Travel

| Tier | Description |
|------|-------------|
| A | Travels constantly — multiple trips a year, primary form of life experience |
| B | Travels often — several meaningful trips a year |
| C | Travels regularly — annual holiday, occasional weekend trips |
| D | Travels rarely — prefers home, occasional trips for events |
| E | Travel-averse — actively dislikes travel, prefers staying put |

**Matching:** Adjacent tiers fine. A with D or E creates ongoing planning friction.

---

## P08b — Financial habits

| Tier | Description |
|------|-------------|
| A | Highly disciplined — budgets, tracks, invests, optimises |
| B | Disciplined — saves regularly, plans purchases, mostly tracked |
| C | Balanced — sensible without rigidity, occasional indulgence |
| D | Loose — spends without much tracking, sometimes overspends |
| E | Impulsive — buys on whim, debt-prone, no planning |

**Matching:** A with E is high-friction — money habits encode values about future. Seek similarity.

---

## P08c — Daily rhythm

| Tier | Description |
|------|-------------|
| A | Strong morning person — up early, productive AM, sleeps early |
| B | Mostly morning — earlier rhythm, flexible |
| C | Standard — mid-day rhythm, adjusts to circumstance |
| D | Mostly evening — slow start, productive afternoon and evening |
| E | Strong night person — peaks late, sleeps late, hates mornings |

**Matching:** A with E means partners barely overlap awake. Mid-tier mismatches workable.

---

## P08d — Living style

| Tier | Description |
|------|-------------|
| A | Highly tidy — organised, minimalist, everything in place |
| B | Tidy — clean and ordered, comfortable with some lived-in feel |
| C | Balanced — moderately tidy, periodic resets |
| D | Casual — comfortable with mess, tidies when needed |
| E | Cluttered — high tolerance for chaos, finds tidiness restrictive |

**Matching:** A with D or E is a daily-irritant mismatch — one of the most common cohabitation failures.


------------------------------------------------------------------------------
FILE: parameters/P09_love_language.md
------------------------------------------------------------------------------

# P09 — Love Language

Love language describes how a person prefers to give and receive affection.
Misalignment here means love feels "sent but not received" — both partners
caring deeply but neither feeling cared for. Note that P09a and P09b are
**categorical** (not ordinal); P09c and P09d are ordinal frequency/intensity
scales.

**Dealbreaker potential:** Low-Medium (workable with awareness)
**Codebook version:** v1.0

---

## P09a — Primary give *(categorical)*

| Tier | Description |
|------|-------------|
| A | Acts of service — shows love through doing things for partner |
| B | Quality time — gives undivided attention and presence |
| C | Words of affirmation — expresses love verbally and explicitly |
| D | Physical touch — gives love through hugs, contact, closeness |
| E | Gifts — gives love through thoughtful objects and gestures |

**Matching:** Categorical, not graded. Compatibility = your give matches partner's receive (P09b), not tier similarity.

---

## P09b — Primary receive *(categorical)*

| Tier | Description |
|------|-------------|
| A | Acts of service — feels loved when partner does things for them |
| B | Quality time — feels loved through undivided attention |
| C | Words of affirmation — feels loved through explicit verbal affirmation |
| D | Physical touch — feels loved through hugs, contact, closeness |
| E | Gifts — feels loved through thoughtful objects and gestures |

**Matching:** Categorical. Goal: each partner's give (P09a) covers the other's receive (P09b). Mismatch is workable but requires active translation.

---

## P09c — Affection frequency

| Tier | Description |
|------|-------------|
| A | Constant — affection multiple times an hour when together |
| B | Frequent — affection many times daily |
| C | Regular — affection daily, naturally woven into routine |
| D | Occasional — affection a few times a week |
| E | Rare — minimal expressed affection, prefers it implicit |

**Matching:** Adjacent tiers compatible. A with E creates one feeling smothered, the other starved.

---

## P09d — Physical affection comfort

| Tier | Description |
|------|-------------|
| A | Highly affectionate physically — constant touch when together |
| B | Affectionate — frequent hugs, hand-holding, closeness |
| C | Comfortable — affection when natural, not constant |
| D | Selective — physical affection in private only or specific contexts |
| E | Reserved — uncomfortable with most physical affection |

**Matching:** A with E is among the most reliably incompatible mismatches — physical disconnection corrodes intimacy fast.


------------------------------------------------------------------------------
FILE: parameters/P10_anger_mood_management.md
------------------------------------------------------------------------------

# P10 — Anger and Mood Management

Anger and mood management describes how a person processes and externalises
anger and negative moods. It determines whether bad days affect just one
person or spread through the whole household.

**Dealbreaker potential:** Medium
**Codebook version:** v1.0

---

## P10a — Expression style

| Tier | Description |
|------|-------------|
| A | Externalised — anger comes out openly, loudly, sometimes physically (slamming doors etc.) |
| B | Verbal expression — anger expressed in words, sharp but contained |
| C | Direct but measured — names the anger, manages tone |
| D | Internalised — feels anger but doesn't express, broods |
| E | Suppressed — denies anger even to self, surfaces sideways |

**Matching:** A with D or E is high-friction — A reads E as cold and avoidant, E reads A as scary or unsafe.

---

## P10b — Trigger sensitivity

| Tier | Description |
|------|-------------|
| A | Highly triggerable — small frustrations spark big reactions |
| B | Easily triggered — frequent low-grade frustration |
| C | Moderate — normal range of triggers |
| D | Hard to trigger — requires significant cause |
| E | Very hard to trigger — almost never reaches anger |

**Matching:** Seek similarity. A with E creates dynamic where small things become big arguments.

---

## P10c — Cooldown time

| Tier | Description |
|------|-------------|
| A | Instant — anger flashes and dissipates in minutes |
| B | Quick — back to normal within an hour |
| C | Moderate — needs hours to fully settle |
| D | Slow — needs a day, sometimes longer |
| E | Lingering — anger and resentment can persist for days or weeks |

**Matching:** Adjacent tiers fine. A with E means apologies and repair may not land before next conflict starts.

---

## P10d — Mood contagion

| Tier | Description |
|------|-------------|
| A | Highly contagious — bad mood spreads to whole household quickly |
| B | Contagious — partner usually notices and absorbs |
| C | Moderate — affects partner when significant |
| D | Contained — keeps moods personal mostly |
| E | Sealed — moods stay entirely internal, partner often doesn't notice |

**Matching:** A with E creates an asymmetry — one absorbs, the other never realises they're transmitting.


------------------------------------------------------------------------------
FILE: parameters/P11_altruism_kindness.md
------------------------------------------------------------------------------

# P11 — Altruism and Kindness

Altruism and kindness describe how much attention a person gives to others'
wellbeing — both close people and strangers. The patterns here reveal the
moral baseline of the relationship.

**Dealbreaker potential:** Low-Medium
**Codebook version:** v1.0

---

## P11a — Generosity

| Tier | Description |
|------|-------------|
| A | Highly generous — gives time, money, attention freely without keeping score |
| B | Generous — regularly gives, comfortable doing so |
| C | Balanced — generous within reason, expects basic reciprocity |
| D | Cautious — gives selectively, after assessment |
| E | Self-protective — minimal giving, prioritises own needs strongly |

**Matching:** A with E creates resentment — A feels used over time, E feels pressured.

---

## P11b — Stranger kindness

| Tier | Description |
|------|-------------|
| A | Universally kind — treats strangers warmly, helps freely |
| B | Kind — friendly to strangers, helps when asked |
| C | Polite — civil but reserved with strangers |
| D | Detached — minimal engagement with strangers |
| E | Cold — actively avoids stranger interactions, sometimes rude |

**Matching:** Loose, but large gaps reveal value differences that show up daily (waitstaff, drivers, service workers).

---

## P11c — Cause orientation

| Tier | Description |
|------|-------------|
| A | Strongly cause-driven — donates, volunteers, organises around causes |
| B | Engaged — supports causes financially or vocally |
| C | Aware — informed, occasional support |
| D | Detached — limited engagement with broader causes |
| E | Disengaged — rejects cause-orientation as performative |

**Matching:** Loose unless one partner is A and the other E — that's a values clash.

---

## P11d — Reciprocity expectation

| Tier | Description |
|------|-------------|
| A | No expectation — gives without any tracking of return |
| B | Low expectation — appreciates return but doesn't require |
| C | Balanced — comfortable with rough reciprocity over time |
| D | Tracks — keeps loose mental ledger of give and take |
| E | Strict — expects clear return on every gift or favour |

**Matching:** A with E is high-friction — A finds E transactional, E finds A naive.


------------------------------------------------------------------------------
FILE: parameters/P12_dominance_submissiveness.md
------------------------------------------------------------------------------

# P12 — Dominance vs Submissiveness

This parameter describes how a person navigates power dynamics — who
decides, who leads, how easily they assert or yield. It determines whose
preferences shape daily life and how decisions get made.

**Dealbreaker potential:** Medium
**Codebook version:** v1.0

---

## P12a — Decision-making

| Tier | Description |
|------|-------------|
| A | Strongly decisive — takes charge, makes calls quickly |
| B | Decisive — comfortable making decisions, open to input |
| C | Collaborative — prefers joint decisions |
| D | Defers — comfortable with partner deciding most things |
| E | Strongly deferential — actively prefers partner makes decisions |

**Matching:** A-D and B-E pairings work well — complementary. A-A and E-E problematic at extremes.

---

## P12b — Opinion assertiveness

| Tier | Description |
|------|-------------|
| A | Highly assertive — voices opinions strongly, even unpopular ones |
| B | Assertive — shares opinions readily, civil |
| C | Balanced — shares when relevant, holds back when not |
| D | Reserved — shares opinions selectively, with close people |
| E | Quiet — rarely shares opinions, lets others lead |

**Matching:** Mismatch is workable when complementary (A-D), but creates loneliness if too far apart on shared decisions.

---

## P12c — Compromise willingness

| Tier | Description |
|------|-------------|
| A | Highly compromising — yields readily for harmony |
| B | Compromising — finds middle ground willingly |
| C | Balanced — compromises on small things, holds line on principles |
| D | Resistant — compromises only when forced |
| E | Uncompromising — sees compromise as defeat |

**Matching:** A with E creates "always giving" dynamic — A burns out. Seek similarity in middle range.

---

## P12d — Leadership

| Tier | Description |
|------|-------------|
| A | Natural leader — takes charge in groups, shapes outcomes |
| B | Leads when needed — comfortable in lead role, doesn't seek it |
| C | Dual — leads or follows depending on context |
| D | Prefers to follow — comfortable in supporting roles |
| E | Strongly follower — uncomfortable leading, defers to others |

**Matching:** Adjacent tiers compatible. A with A can clash if both want lead at home.


------------------------------------------------------------------------------
FILE: parameters/P13_sense_of_humour.md
------------------------------------------------------------------------------

# P13 — Sense of Humour

Sense of humour describes how a person uses, receives, and lives with humour.
P13a (style) is **categorical**; the rest are ordinal. The shared-laugh test
is one of the most predictive markers of long-term satisfaction.

**Dealbreaker potential:** Low-Medium
**Codebook version:** v1.0

---

## P13a — Style *(categorical)*

| Tier | Description |
|------|-------------|
| A | Witty / wordplay — quick, clever, language-based |
| B | Observational — sees absurdity in everyday life |
| C | Absurdist — surreal, weird, non-sequitur |
| D | Dry / deadpan — flat delivery, ironic, understated |
| E | Slapstick / physical — broad, visual, exaggerated |

**Matching:** Categorical. Compatibility = both partners enjoying the same style. A with E often miss each other's jokes entirely.

---

## P13b — Frequency

| Tier | Description |
|------|-------------|
| A | Constant — humour woven through almost every interaction |
| B | Frequent — jokes daily, light atmosphere |
| C | Moderate — humour as natural part of conversation |
| D | Occasional — laughs when situation calls for it |
| E | Sparse — humour rare, can read as serious or grim |

**Matching:** Adjacent tiers fine. A with E creates tonal mismatch — one feels heavy, the other feels manic.

---

## P13c — Self-deprecation comfort

| Tier | Description |
|------|-------------|
| A | Highly self-deprecating — readily jokes about own flaws |
| B | Self-deprecating — comfortable with light self-mocking |
| C | Balanced — self-aware humour without self-flagellation |
| D | Self-protective — uncomfortable joking about self |
| E | Defensive — bristles at any joke aimed at self |

**Matching:** Mismatched levels create friction — one finds the other thin-skinned, the other finds the first cruel.

---

## P13d — Humour boundaries

| Tier | Description |
|------|-------------|
| A | Few limits — comfortable with edgy, dark, taboo humour |
| B | Mostly open — open to most humour, some no-go zones |
| C | Mainstream — comfortable with broad humour, avoids edge |
| D | Conservative — prefers gentle humour, avoids dark or edgy |
| E | Strict — humour about identity, trauma, religion off-limits |

**Matching:** A with D or E is a values flag — humour boundaries reveal what someone takes seriously.


------------------------------------------------------------------------------
FILE: parameters/P14_emotional_availability.md
------------------------------------------------------------------------------

# P14 — Emotional Availability

Emotional availability describes how readily a person shows up emotionally
for a partner — willingness to open up, sit with vulnerability, and provide
support. Distinct from love language (P09); this is about *capacity*, not
*style*.

**Dealbreaker potential:** Medium-High
**Codebook version:** v1.0

---

## P14a — Openness timing

| Tier | Description |
|------|-------------|
| A | Opens up immediately — vulnerable from early conversations |
| B | Opens up readily — vulnerability emerges within weeks |
| C | Moderate — opens up over months as trust builds |
| D | Slow to open — vulnerability comes after a year or more |
| E | Rarely opens — keeps emotional life largely private even long-term |

**Matching:** A with E creates an asymmetry that often doesn't resolve — A discloses, E withholds.

---

## P14b — Vulnerability comfort

| Tier | Description |
|------|-------------|
| A | Highly comfortable — at ease showing fear, sadness, doubt |
| B | Comfortable — vulnerable when situation calls for it |
| C | Selective — vulnerable about specific things, guarded on others |
| D | Uncomfortable — manages vulnerability with humour or deflection |
| E | Avoidant — actively avoids vulnerable disclosure |

**Matching:** Seek similarity in the middle range. A with E rarely feels safe for either party.

---

## P14c — Support style

| Tier | Description |
|------|-------------|
| A | Active emotional support — listens deeply, sits with feelings, doesn't fix |
| B | Engaged support — listens and offers measured perspective |
| C | Practical support — offers help and solutions readily |
| D | Brief support — offers acknowledgment then moves on |
| E | Minimal support — uncomfortable with emotional labour |

**Matching:** Mismatch on this is the silent killer — partners can love each other while consistently failing to support each other.

---

## P14d — Emotional bandwidth

| Tier | Description |
|------|-------------|
| A | Vast — can hold heavy emotional weight for long periods |
| B | High — handles most emotional needs comfortably |
| C | Moderate — supportive within normal range |
| D | Limited — gets overwhelmed by sustained emotional intensity |
| E | Low — minimal capacity, withdraws when emotions run high |

**Matching:** Critical to match. Two A's risk co-rumination; A with E creates carer-carried dynamic.


------------------------------------------------------------------------------
FILE: parameters/P15_family_orientation.md
------------------------------------------------------------------------------

# P15 — Family Orientation

Family orientation describes how a person relates to family — their own,
their partner's, and a potential family of their own. The decisions encoded
here shape the actual life two people build together.

**Dealbreaker potential:** High
**Codebook version:** v1.0

---

## P15a — Want children

| Tier | Description |
|------|-------------|
| A | Definitely yes — wants children, often multiple |
| B | Probably yes — leans toward children with right circumstances |
| C | Open — could go either way, depends on partner and life |
| D | Probably not — leans toward no children |
| E | Definitely no — clearly does not want children, often firm |

**Matching:** Critical. A with E is an almost certain dealbreaker — one of the few truly binary compatibility checks.

---

## P15b — Family centrality

| Tier | Description |
|------|-------------|
| A | Family is central — frequent contact, family informs major decisions |
| B | Close — regular contact, family considered in big choices |
| C | Balanced — family important but partnership comes first |
| D | Independent — affectionate but boundaried, infrequent contact |
| E | Distant — limited family relationships by choice or circumstance |

**Matching:** Mismatch creates friction over holidays, in-laws, decisions. Seek similarity.

---

## P15c — Parenting style

| Tier | Description |
|------|-------------|
| A | Highly involved / structured — engaged parenting, clear rules, hands-on |
| B | Engaged / balanced — present and involved, mix of structure and freedom |
| C | Balanced — moderately involved, child-led where possible |
| D | Free-range — light hand, child-led, fewer rules |
| E | Hands-off — believes in independence early, minimal intervention |

**Matching:** Only relevant if both partners are P15a A or B. A with E creates parenting friction — must align before having children.

---

## P15d — Extended family involvement

| Tier | Description |
|------|-------------|
| A | Highly involved — extended family central to weekly life |
| B | Involved — regular contact and gatherings |
| C | Moderate — visits and calls, not constant |
| D | Limited — formal occasions only |
| E | Detached — minimal extended family contact |

**Matching:** Loose. Mismatches workable if both partners respect each other's preference.


------------------------------------------------------------------------------
FILE: parameters/P16_ambition_career.md
------------------------------------------------------------------------------

# P16 — Ambition and Career

Ambition and career describe how central work is to someone's identity, how
driven they are, and how they think about money. Career mismatch shows up
in time, energy, and money decisions across the whole relationship.

**Dealbreaker potential:** Medium
**Codebook version:** v1.0

---

## P16a — Career centrality

| Tier | Description |
|------|-------------|
| A | Career is identity — work defines self, much of life organised around it |
| B | Career is core — important to identity, alongside other priorities |
| C | Career is significant — meaningful but balanced with rest of life |
| D | Career is means — provides for life rather than defines it |
| E | Career is incidental — work is something to do, not something to be |

**Matching:** Adjacent tiers compatible. A with D or E creates time and value mismatches — A works late, the other waits.

---

## P16b — Ambition level

| Tier | Description |
|------|-------------|
| A | Highly ambitious — actively chasing growth, status, scale |
| B | Ambitious — driven, regular advancement goals |
| C | Moderate — wants to do well, not all-consumed |
| D | Comfortable — content with stability, modest growth |
| E | Anti-ambition — actively rejects climb, prefers ease |

**Matching:** Seek similarity. A with E creates fundamental life-direction mismatch.

---

## P16c — Work-life balance

| Tier | Description |
|------|-------------|
| A | Strong work focus — long hours, work bleeds into life |
| B | Tilted to work — work is priority but with limits |
| C | Balanced — clear separation, both important |
| D | Tilted to life — work is contained, life takes precedence |
| E | Strong life focus — work is small slice, life is the centre |

**Matching:** A with D or E creates daily availability mismatch — partners want different evenings and weekends.

---

## P16d — Financial ambition

| Tier | Description |
|------|-------------|
| A | Wealth-focused — explicitly building toward significant wealth |
| B | Comfort-plus — wants comfortable life with margin |
| C | Comfortable — wants security and decency |
| D | Sufficiency — wants enough, not more |
| E | Anti-materialist — actively rejects wealth focus |

**Matching:** A with D or E creates ongoing money tension — different definitions of "enough."


------------------------------------------------------------------------------
FILE: parameters/P17_spirituality_religion.md
------------------------------------------------------------------------------

# P17 — Spirituality and Religion

Spirituality and religion describe how religion or spirituality shapes a
person's life and what they need from a partner on this front. Often the
source of family conflict and big-decision friction (weddings, children,
holidays).

**Dealbreaker potential:** High
**Codebook version:** v1.0

---

## P17a — Religious identity

| Tier | Description |
|------|-------------|
| A | Devout — faith is central, identity-defining, organises life |
| B | Practising — observant, important to identity |
| C | Cultural — identifies with tradition, light practice |
| D | Lapsed / non-practising — born into faith, not practising |
| E | Atheist / non-religious — no religious identification |

**Matching:** Critical for some, irrelevant for others. A with E is dealbreaker for most A's.

---

## P17b — Practice frequency

| Tier | Description |
|------|-------------|
| A | Daily — regular religious practice (prayer, study, ritual) |
| B | Weekly — observes weekly practices |
| C | Festival-based — major holidays and life events |
| D | Occasional — irregular, life-event triggered |
| E | None — no religious practice |

**Matching:** Mismatch shows up in daily rhythm — A's life pauses for practice, E's doesn't.

---

## P17c — Partner expectation

| Tier | Description |
|------|-------------|
| A | Must share faith fully — same religion, same practice level |
| B | Must be compatible — same broad tradition, similar level |
| C | Open with respect — different faiths fine, mutual respect required |
| D | Indifferent — partner's faith is their own business |
| E | Prefer secular partner — would find religious partner difficult |

**Matching:** Hardest constraint wins. A or E partner sets the floor for compatibility.

---

## P17d — Spiritual worldview

| Tier | Description |
|------|-------------|
| A | Strong supernatural worldview — afterlife, divine intervention, fixed truth |
| B | Believing but flexible — open to mystery, less specific doctrine |
| C | Spiritual but not religious — meaning-seeking, not doctrine-based |
| D | Secular with openness — naturalist with respect for unknowns |
| E | Strict materialist — only what's empirically verifiable counts |

**Matching:** A with E creates fundamental disagreement on what's real. Adjacent tiers compatible.


------------------------------------------------------------------------------
FILE: parameters/P18_physical_lifestyle.md
------------------------------------------------------------------------------

# P18 — Physical Lifestyle

Physical lifestyle describes the body-level texture of how someone lives —
fitness, food, substances, indoors vs outdoors. Mismatches here erode
shared activity and create slow-burn resentment.

**Dealbreaker potential:** Low-Medium
**Codebook version:** v1.0

---

## P18a — Fitness orientation

| Tier | Description |
|------|-------------|
| A | Athlete-level — daily training, fitness is central to life |
| B | Strongly active — regular exercise multiple times a week |
| C | Moderately active — exercise as habit, not central |
| D | Casually active — occasional exercise |
| E | Sedentary — minimal exercise, no fitness habit |

**Matching:** Adjacent tiers fine. A with E creates lifestyle mismatch on activities, energy, planning.

---

## P18b — Health consciousness

| Tier | Description |
|------|-------------|
| A | Highly health-focused — tracks food, sleep, supplements |
| B | Health-aware — eats well, sleeps well, low effort |
| C | Moderate — health-conscious in broad strokes |
| D | Casual — eats what tastes good, occasional health attention |
| E | Indifferent — no particular health focus |

**Matching:** A with E creates daily friction over food, routines, indulgences.

---

## P18c — Substance use

| Tier | Description |
|------|-------------|
| A | Abstainer — no alcohol, smoking, recreational substances |
| B | Light — occasional drink, no smoking, no other substances |
| C | Moderate — social drinking, no other use |
| D | Regular — frequent drinking, occasional other use |
| E | Heavy — daily drinking or regular substance use |

**Matching:** A with D or E is a values flag and often dealbreaker. Seek similarity.

---

## P18d — Outdoor vs indoor

| Tier | Description |
|------|-------------|
| A | Strongly outdoor — hikes, travel, adventure-seeking |
| B | Outdoor-leaning — enjoys outdoor activities frequently |
| C | Balanced — both equally |
| D | Indoor-leaning — comfortable indoors, occasional outdoor |
| E | Strongly indoor — rarely seeks outdoor activity |

**Matching:** Loose. Different preferences workable if respected.


------------------------------------------------------------------------------
FILE: parameters/P19_communication_style.md
------------------------------------------------------------------------------

# P19 — Communication Style

Communication style describes how a person communicates day to day —
bluntness, depth, channel preferences, listening. Determines whether
messages land or distort across the whole relationship.

**Dealbreaker potential:** Medium
**Codebook version:** v1.0

---

## P19a — Directness

| Tier | Description |
|------|-------------|
| A | Highly direct — says exactly what they think, doesn't soften |
| B | Direct — clear and honest, with some tact |
| C | Balanced — direct on important things, polite on small |
| D | Indirect — softens, uses hints and context |
| E | Highly indirect — relies heavily on subtext, dislikes blunt speech |

**Matching:** A with E often miscommunicates — A's clarity reads as harsh, E's hints don't land.

---

## P19b — Conversation depth

| Tier | Description |
|------|-------------|
| A | Deep-only — small talk feels meaningless, wants meaningful exchange |
| B | Depth-leaning — enjoys deep conversation regularly |
| C | Mixed — depth and small talk both have place |
| D | Surface-leaning — comfortable mostly with light conversation |
| E | Surface-only — uncomfortable with emotional or philosophical depth |

**Matching:** Seek similarity. A with E creates one feeling unmet, the other feeling pushed.

---

## P19c — Digital communication

| Tier | Description |
|------|-------------|
| A | Heavy texter — constant messaging when apart |
| B | Frequent — multiple times daily |
| C | Regular — daily check-ins |
| D | Light — sparse messaging, prefers in-person or calls |
| E | Minimal — rarely texts, prefers offline |

**Matching:** Adjacent tiers fine. A with E creates one feeling neglected, the other feeling smothered.

---

## P19d — Listening style

| Tier | Description |
|------|-------------|
| A | Deep listener — fully attentive, holds space, reflects back |
| B | Strong listener — attentive, engages thoughtfully |
| C | Balanced — listens well, sometimes parallel-talks |
| D | Half-listener — present but distracted, common interruptions |
| E | Poor listener — frequently misses content, jumps to own response |

**Matching:** Critical. Two poor listeners (D-E or E-E) rarely build deep intimacy. A pairs well across tiers.


------------------------------------------------------------------------------
FILE: parameters/P20_openness_to_change.md
------------------------------------------------------------------------------

# P20 — Openness to Change

Openness to change describes how readily a person updates beliefs, takes
risks, and embraces new circumstances. Determines how a relationship
handles life transitions, disruption, and growth over time.

**Dealbreaker potential:** Low
**Codebook version:** v1.0

---

## P20a — Adaptability

| Tier | Description |
|------|-------------|
| A | Highly adaptable — thrives on change, finds routine stifling |
| B | Adaptable — handles change well, settled by routine |
| C | Balanced — adapts when needed, prefers stability |
| D | Routine-preferring — uncomfortable with frequent change |
| E | Change-averse — strongly prefers continuity, struggles with disruption |

**Matching:** Adjacent tiers fine. A with E creates conflict during life transitions (moves, jobs, kids).

---

## P20b — Opinion flexibility

| Tier | Description |
|------|-------------|
| A | Highly flexible — readily updates positions when shown new information |
| B | Flexible — open to changing views with strong evidence |
| C | Balanced — holds positions, updates with reason |
| D | Firm — slow to update positions |
| E | Fixed — rarely updates positions regardless of evidence |

**Matching:** A pairs well with most. E with E can deadlock.

---

## P20c — Risk tolerance

| Tier | Description |
|------|-------------|
| A | High risk — comfortable betting big, embraces uncertainty |
| B | Moderate-high — takes calculated risks regularly |
| C | Balanced — risks weighed carefully, taken when worthwhile |
| D | Low risk — prefers safe paths, cautious with money and decisions |
| E | Highly risk-averse — strongly prefers certainty, struggles with uncertainty |

**Matching:** A with E shows up in big decisions — career, finance, moves. Adjacent tiers fine.

---

## P20d — Growth mindset

| Tier | Description |
|------|-------------|
| A | Strong growth mindset — sees abilities as developed, embraces challenge |
| B | Growth-leaning — believes improvement is possible, works for it |
| C | Balanced — mix of growth and fixed thinking |
| D | Fixed-leaning — sees abilities as largely innate |
| E | Strong fixed mindset — abilities seen as set, struggles seen as exposing limits |

**Matching:** A pairs broadly. Two E's together can stagnate.


==============================================================================
  PART 3 — LOOKUP CODEBOOKS (S / T / X / C)
==============================================================================

These are the lookup tables referenced from each dimension record. Use S codes for observed behaviours, T for triggers (what the person rejects), X for expressions (how values manifest), and C for the consistency rating of the dimension.


------------------------------------------------------------------------------
FILE: codebook/S_signals.md
------------------------------------------------------------------------------

# S Codes — Behavioural Signals

Behavioural signals are observable patterns inferred from natural conversation.
Each S code represents a specific, detectable behaviour that an AI can identify
without asking direct questions.

**Total seed codes:** 150
**Codebook version:** v1.0

---

## S001–S020 — Intellectual behaviour

| Code | Description |
|------|-------------|
| S001 | Engages with complex topics analytically rather than emotionally |
| S002 | Challenges their own ideological side when evidence demands |
| S003 | Distinguishes between policy outcomes and political rhetoric |
| S004 | Debates religion and philosophy as intellectual exercise |
| S005 | Updates views when presented with contradicting evidence |
| S006 | Pursues multiple skills and disciplines simultaneously |
| S007 | Goes deep into subjects rather than staying at surface level |
| S008 | Seeks out original sources rather than secondary commentary |
| S009 | Actively sharpens arguments for real-life debates |
| S010 | Frames problems in unconventional ways before solving |
| S011 | Reads widely across unrelated domains and connects them |
| S012 | Asks follow-up questions that reveal genuine curiosity |
| S013 | Enjoys thought experiments and hypothetical reasoning |
| S014 | References historical context when analysing current events |
| S015 | Builds mental models rather than memorising facts |
| S016 | Comfortable sitting with ambiguity and unresolved questions |
| S017 | Synthesises ideas from different fields into new frameworks |
| S018 | Prefers understanding first principles over surface rules |
| S019 | Engages with opposing viewpoints to stress-test own thinking |
| S020 | Notices patterns across seemingly unrelated domains |

---

## S021–S040 — Social behaviour

| Code | Description |
|------|-------------|
| S021 | Gravitates toward one-on-one over group conversations |
| S022 | Maintains few but deep long-term friendships |
| S023 | Comfortable with extended periods of solitude |
| S024 | Recharges energy through alone time after social interaction |
| S025 | Adapts communication style naturally to different audiences |
| S026 | Comfortable in social settings without needing to be centre |
| S027 | Observes social dynamics rather than performing in them |
| S028 | Builds trust gradually before opening up personally |
| S029 | Actively listens without redirecting conversation to self |
| S030 | Remembers details others shared in previous conversations |
| S031 | Prefers small gatherings over large social events |
| S032 | Comfortable with silence in conversation without filling it |
| S033 | Notices when others are uncomfortable before they say so |
| S034 | Spontaneous socially within a loose structure |
| S035 | Warm toward strangers without being performatively friendly |
| S036 | Drives conversation toward depth naturally |
| S037 | Uncomfortable with purely transactional social interaction |
| S038 | Gives full attention in conversation — doesn't multitask |
| S039 | Uncomfortable in large crowds or overstimulating environments |
| S040 | Initiates plans occasionally but doesn't need to lead socially |

---

## S041–S060 — Emotional behaviour

| Code | Description |
|------|-------------|
| S041 | Processes emotions internally before expressing them |
| S042 | Remains calm under pressure or frustrating situations |
| S043 | Expresses care through actions more than words |
| S044 | Notices emotional undercurrents in conversation |
| S045 | Comfortable sitting with others in difficult emotions without fixing |
| S046 | Doesn't catastrophise when things go wrong |
| S047 | Recovers from setbacks by reframing and moving forward |
| S048 | Expresses frustration through analysis rather than outburst |
| S049 | Comfortable being emotionally vulnerable with trusted people |
| S050 | Doesn't hold grudges — moves forward after resolution |
| S051 | Responds to criticism constructively rather than defensively |
| S052 | Separates emotional reaction from logical response in conflict |
| S053 | Genuinely curious about others' emotional experiences |
| S054 | Doesn't project own emotional state onto others |
| S055 | Gives space to others when they need it without taking it personally |
| S056 | Affected by others' moods but not destabilised by them |
| S057 | Acknowledges own mistakes without excessive self-criticism |
| S058 | Comfortable with emotional ambiguity in relationships |
| S059 | Expresses warmth subtly rather than effusively |
| S060 | Seeks to understand before seeking to be understood |

---

## S061–S080 — Values in action

| Code | Description |
|------|-------------|
| S061 | Teaches or mentors voluntarily without career incentive |
| S062 | Gives time and energy generously without keeping score |
| S063 | Treats strangers with the same dignity as people they know |
| S064 | Avoids performative altruism — gives quietly |
| S065 | Holds ethical positions consistently across different groups |
| S066 | Willing to be unpopular when defending a principled position |
| S067 | Actively notices systemic issues rather than only personal ones |
| S068 | Holds humour to ethical limits — doesn't punch down |
| S069 | Respects autonomy of others to make their own choices |
| S070 | Consistent behaviour whether or not being observed |
| S071 | Acknowledges complexity rather than defaulting to simple answers |
| S072 | Prioritises honesty over comfort in conversations |
| S073 | Takes responsibility for mistakes without deflecting |
| S074 | Applies same standards to self as to others |
| S075 | Engages with opposing views charitably before criticising |
| S076 | Distinguishes between personal discomfort and actual harm |
| S077 | Actively works to reduce own cognitive biases |
| S078 | Comfortable with moral complexity and grey areas |
| S079 | Values fairness over strict rule-following when they conflict |
| S080 | Expresses care through consistency rather than grand gestures |

---

## S081–S100 — Ambition and work

| Code | Description |
|------|-------------|
| S081 | Pursues long-term goals across multiple parallel tracks |
| S082 | Builds deliberately rather than rushing to visible outcomes |
| S083 | Researches decisions thoroughly before committing |
| S084 | Comfortable with delayed gratification for larger goals |
| S085 | Seeks mastery not just competence in chosen domains |
| S086 | Career ambition coexists with strong non-work identity |
| S087 | Spots inefficiencies in systems and wants to fix them |
| S088 | Generates original ideas across multiple domains |
| S089 | Takes initiative without waiting to be directed |
| S090 | Comfortable leading when needed but doesn't seek authority |
| S091 | Evaluates work by impact not just completion |
| S092 | Invests in credentials and qualifications strategically |
| S093 | Willing to do unglamorous work toward meaningful goals |
| S094 | Guards personal time fiercely despite high ambition |
| S095 | Comfortable with uncertainty during long execution phases |
| S096 | Motivated by growth and learning not just status or money |
| S097 | Pivots ideas readily without attachment to original version |
| S098 | Thinks in systems and second-order consequences |
| S099 | Builds tools and frameworks to solve recurring problems |
| S100 | Seeks feedback actively to improve rather than validate |

---

## S101–S120 — Lifestyle and habits

| Code | Description |
|------|-------------|
| S101 | Travels immersively — seeks experience not just destinations |
| S102 | Spends considerately — researches value before committing |
| S103 | Health-conscious — actively manages diet and physical wellbeing |
| S104 | Drawn to outdoor and nature environments over indoor comfort |
| S105 | Lives with moderate structure — not rigid but not chaotic |
| S106 | Invests in tools and equipment that support creative pursuits |
| S107 | Leans minimalist in living environment — quality over quantity |
| S108 | Builds healthy habits deliberately after period of neglect |
| S109 | Values experience-based spending over material acquisition |
| S110 | Engages with local culture deeply when travelling |
| S111 | Morning or evening person — has clear energy rhythm |
| S112 | Uses technology purposefully rather than passively |
| S113 | Maintains multiple active creative or intellectual hobbies |
| S114 | Plans travel and experiences carefully in advance |
| S115 | Comfortable eating alone or doing activities solo |
| S116 | Financial decisions driven by long-term security not short-term comfort |
| S117 | Keeps physical space organised and intentional |
| S118 | Has strong aesthetic sensibility applied to daily choices |
| S119 | Aspires to expand geographic experience actively |
| S120 | Comfortable with physical discomfort in service of experience |

---

## S121–S140 — Relationship behaviour

| Code | Description |
|------|-------------|
| S121 | Committed to long-term relationships over casual connection |
| S122 | Values intellectual compatibility as core relationship need |
| S123 | Needs both deep closeness and personal autonomy simultaneously |
| S124 | Shows care through consistent presence over grand gestures |
| S125 | Honest with partners even when uncomfortable |
| S126 | Supports partner's independent growth and ambitions |
| S127 | Resolves conflict through discussion not withdrawal or explosion |
| S128 | Doesn't idealise partner — sees them clearly and accepts them |
| S129 | Shares intellectual interests with partner as bonding mechanism |
| S130 | Comfortable with partner having separate friendships and space |
| S131 | Builds relationship gradually — doesn't rush intimacy |
| S132 | Expresses love through quality time and shared experience |
| S133 | Takes relationship decisions seriously — not impulsive |
| S134 | Comfortable discussing relationship dynamics openly |
| S135 | Doesn't use humour to deflect from serious relationship


------------------------------------------------------------------------------
FILE: codebook/T_triggers.md
------------------------------------------------------------------------------

# T Codes — Triggers

Triggers are things a person cannot tolerate — patterns, behaviours, or attitudes
that activate a strong negative response. They are inferred from conversation, not
self-reported. Triggers reveal values more reliably than positive signals because
people rarely perform their dealbreakers.

**Total seed codes:** 60
**Codebook version:** v1.0

---

## T001–T010 — Intellectual triggers

| Code | Description |
|------|-------------|
| T001 | Performative intelligence — sounding smart over being smart |
| T002 | Ideology prioritised over evidence in argument |
| T003 | Intellectual incuriosity — no interest in learning or depth |
| T004 | Dismissing complex topics without engaging with them |
| T005 | Refusing to update views when shown clear evidence |
| T006 | Conflating opinion with fact in discussion |
| T007 | Using authority as substitute for reasoning |
| T008 | Intellectual dishonesty — arguing in bad faith |
| T009 | Oversimplifying nuanced topics for comfort |
| T010 | Taking intellectual credit for others' ideas |

---

## T011–T020 — Social triggers

| Code | Description |
|------|-------------|
| T011 | Performative social behaviour — performing for audience not connecting |
| T012 | Constant need for social validation and external approval |
| T013 | Inability to maintain depth in conversation |
| T014 | Redirecting every conversation back to self |
| T015 | Treating surface-level interaction as sufficient connection |
| T016 | Social one-upmanship — competing rather than connecting |
| T017 | Gossiping about absent people as primary social currency |
| T018 | Inability to be comfortable with silence |
| T019 | Treating introversion as a problem to be fixed |
| T020 | Discomfort when others receive more attention |

---

## T021–T030 — Emotional triggers

| Code | Description |
|------|-------------|
| T021 | Flattery used as substitute for honest feedback |
| T022 | Emotional manipulation to influence outcomes |
| T023 | Weaponising vulnerability to avoid accountability |
| T024 | Dismissing others' emotional experiences as invalid |
| T025 | Chronic victimhood — patterns without self-reflection |
| T026 | Explosive anger disproportionate to situation |
| T027 | Stonewalling — complete emotional shutdown in conflict |
| T028 | Passive aggression as primary conflict mode |
| T029 | Holding grudges long after resolution |
| T030 | Confusing emotional intensity with emotional depth |

---

## T031–T040 — Values triggers

| Code | Description |
|------|-------------|
| T031 | Hypocrisy — different standards for self vs others |
| T032 | Performative altruism — giving for visibility not impact |
| T033 | Punching down — using humour to demean vulnerable groups |
| T034 | Dishonesty through omission rather than direct lying |
| T035 | Treating rules as for others, not for self |
| T036 | Moral cowardice — staying silent when position demands speaking |
| T037 | Confusing wealth or status with character or worth |
| T038 | Treating kindness as weakness rather than strength |
| T039 | Casual cruelty toward people with less power |
| T040 | Refusing accountability by deflecting blame consistently |

---

## T041–T050 — Ambition and work triggers

| Code | Description |
|------|-------------|
| T041 | Wasted potential — chronic underachievement without reflection |
| T042 | Entitlement — expecting outcomes without putting in effort |
| T043 | Taking credit for collaborative work individually |
| T044 | Chronic complaining without action or attempt to change |
| T045 | Confusing busyness with productivity or purpose |
| T046 | Defining self entirely through job title or salary |
| T047 | Sabotaging others to advance rather than competing fairly |
| T048 | Inability to finish what is started — serial abandonment |
| T049 | Dismissing others' ambitions as unrealistic or naive |
| T050 | Fear of failure used as permanent excuse for inaction |

---

## T051–T060 — Relationship triggers

| Code | Description |
|------|-------------|
| T051 | Controlling behaviour disguised as care or concern |
| T052 | Treating partner's independence as threat rather than strength |
| T053 | Using relationship as identity rather than part of identity |
| T054 | Inconsistency — different person in public vs private |
| T055 | Keeping score in relationship — transactional rather than generous |
| T056 | Dismissing partner's interests as unimportant or trivial |
| T057 | Jealousy expressed as accusation rather than vulnerability |
| T058 | Inability to apologise genuinely without qualification |
| T059 | Using past relationship trauma to justify present behaviour |
| T060 | Expecting partner to fulfil all social and emotional needs |


------------------------------------------------------------------------------
FILE: codebook/X_expressions.md
------------------------------------------------------------------------------

# X Codes — Expressions

Expressions describe how a person's values, traits, and dimensions manifest
in observable behaviour. Where S codes describe what someone does, X codes
describe how they do it — the channel through which who they are comes out.

**Total seed codes:** 60
**Codebook version:** v1.0

---

## X001–X010 — Intellectual expression

| Code | Description |
|------|-------------|
| X001 | Through debate and structured argumentation |
| X002 | Through building systems, frameworks and mental models |
| X003 | Through teaching and sharing knowledge with others |
| X004 | Through research and deep reading before forming views |
| X005 | Through asking questions rather than asserting answers |
| X006 | Through writing — journaling, essays, documentation |
| X007 | Through connecting ideas across unrelated domains |
| X008 | Through product and solution design thinking |
| X009 | Through analysis of data and patterns |
| X010 | Through critiquing and stress-testing existing ideas |

---

## X011–X020 — Emotional expression

| Code | Description |
|------|-------------|
| X011 | Through humour and wit — deflects and connects simultaneously |
| X012 | Through physical presence and quality time |
| X013 | Through acts of service — doing things rather than saying things |
| X014 | Through deep listening and full attention |
| X015 | Through remembering small meaningful details about others |
| X016 | Through understated warmth rather than effusive affection |
| X017 | Through consistency and reliability over time |
| X018 | Through written words — messages, letters, notes |
| X019 | Through sharing meaningful recommendations — books, music, film |
| X020 | Through showing up without being asked in difficult moments |

---

## X021–X030 — Creative expression

| Code | Description |
|------|-------------|
| X021 | Through photography and visual observation of the world |
| X022 | Through music — listening, curating, or playing |
| X023 | Through cinema and film as primary cultural language |
| X024 | Through design — aesthetic choices in everyday life |
| X025 | Through storytelling and narrative in conversation |
| X026 | Through cooking and food as creative and cultural act |
| X027 | Through travel as primary mode of experiencing the world |
| X028 | Through building things — products, tools, systems |
| X029 | Through language — wordplay, writing, multilingual expression |
| X030 | Through astronomy and engagement with the natural world |

---

## X031–X040 — Social expression

| Code | Description |
|------|-------------|
| X031 | Through one-on-one deep conversation over group interaction |
| X032 | Through observation of others rather than performance |
| X033 | Through dry understated humour in social settings |
| X034 | Through facilitating others' ideas rather than leading |
| X035 | Through introducing people to each other across networks |
| X036 | Through generosity with time and attention to close circle |
| X037 | Through asking questions that make others feel genuinely seen |
| X038 | Through planning experiences and gatherings for others |
| X039 | Through volunteering and community involvement quietly |
| X040 | Through mentoring and guiding those earlier in their journey |

---

## X041–X050 — Values expression

| Code | Description |
|------|-------------|
| X041 | Through consistency between private and public behaviour |
| X042 | Through defending unpopular positions when principle demands |
| X043 | Through quiet giving without seeking recognition |
| X044 | Through holding ethical positions across different groups equally |
| X045 | Through owning mistakes directly without deflection |
| X046 | Through treating all people with equal dignity regardless of status |
| X047 | Through financial choices that reflect stated priorities |
| X048 | Through honest feedback even when comfort would be easier |
| X049 | Through long-term thinking in short-term decisions |
| X050 | Through respecting others' autonomy even when disagr


------------------------------------------------------------------------------
FILE: codebook/C_consistency.md
------------------------------------------------------------------------------

# C Codes — Consistency Scale

Consistency describes how stable a trait or dimension is across different
contexts, moods, and time periods. A high consistency score means the
behaviour appears reliably regardless of situation. A low score means it
is highly context-dependent or volatile.

**Total codes:** 5
**Codebook version:** v1.0

---

| Code | Name | Description |
|------|------|-------------|
| C1 | Rigid | Never wavers — same regardless of context, mood, or audience |
| C2 | Stable | Rarely shifts — consistent across most situations |
| C3 | Evidence-responsive | Holds firm but shifts with good reason or new information |
| C4 | Contextual | Varies meaningfully by situation, relationship, or environment |
| C5 | Volatile | Shifts frequently — inconsistent across contexts |

---

## Usage

Each dimension record includes a consistency code alongside the position and intensity:

```
P5a·A5★ + C2
```

This means: Parameter 5a, tier A, level 5, strong signal, and the trait is stable (rarely shifts).

---

## Notes

- Consistency is not inherently good or bad. C1 on P20a (adaptability) would mean
  extremely rigid — likely a negative signal. C1 on P1a (values) might mean deeply
  principled — a positive signal depending on context.
- Consistency is assessed by the AI from how frequently and uniformly a signal
  appears across different conversation contexts.
- A dimension cannot have a consistency code if its confidence marker is ? (unknown).


==============================================================================
  PART 4 — JSON SCHEMA AND EXAMPLE
==============================================================================

Profile data is stored as JSON. The dimension_record schema defines a single sub-dimension entry; example_profile shows a complete profile across all 80 sub-dimensions for reference.


------------------------------------------------------------------------------
FILE: schema/dimension_record.json
------------------------------------------------------------------------------

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "Once Dimension Record",
  "description": "Schema for a single sub-dimension record in a Once compatibility profile",
  "version": "1.0.0",
  "type": "object",
  "required": ["id", "conf"],
  "properties": {
    "id": {
      "type": "string",
      "description": "Sub-dimension identifier e.g. P1a, P5c",
      "pattern": "^P([1-9]|1[0-9]|20)[a-d]$"
    },
    "pos": {
      "type": "string",
      "description": "Position on the dimension-specific spectrum. Plain language e.g. centre-left, secure, ambivert",
      "nullable": true
    },
    "tier": {
      "type": "string",
      "description": "Tier letter A-E on the dimension-specific spectrum",
      "enum": ["A", "B", "C", "D", "E"],
      "nullable": true
    },
    "int": {
      "type": "integer",
      "description": "Intensity level 1-5 within the tier",
      "minimum": 1,
      "maximum": 5,
      "nullable": true
    },
    "con": {
      "type": "string",
      "description": "Consistency code C1-C5",
      "enum": ["C1", "C2", "C3", "C4", "C5"],
      "nullable": true
    },
    "bsig": {
      "type": "array",
      "description": "Behavioural signal codes from S_signals.md that support this dimension",
      "items": {
        "type": "string",
        "pattern": "^S[0-9]{3}$"
      }
    },
    "trg": {
      "type": "array",
      "description": "Trigger codes from T_triggers.md relevant to this dimension",
      "items": {
        "type": "string",
        "pattern": "^T[0-9]{3}$"
      }
    },
    "exp": {
      "type": "array",
      "description": "Expression codes from X_expressions.md relevant to this dimension",
      "items": {
        "type": "string",
        "pattern": "^X[0-9]{3}$"
      }
    },
    "conf": {
      "type": "integer",
      "description": "Confidence level: 1=unknown(?), 2=inferred(~), 3=strong signal(★)",
      "enum": [1, 2, 3]
    },
    "src": {
      "type": "array",
      "description": "Source conversation references that surfaced this signal",
      "items": {
        "type": "string"
      }
    },
    "upd": {
      "type": "string",
      "description": "Last updated date in YYYYMMDD format",
      "pattern": "^[0-9]{8}$"
    },
    "oq": {
      "type": "array",
      "description": "Open questions — what the AI still needs to learn to improve this dimension",
      "items": {
        "type": "string"
      }
    }
  }
}
```


------------------------------------------------------------------------------
FILE: schema/example_profile.json
------------------------------------------------------------------------------

```json
{
  "profile_id": "ANON_001",
  "codebook_version": "1.0.0",
  "created": "2026-04-24",
  "last_updated": "2026-04-24",
  "encoding": "P1a·B4★ P1b·B3★ P1c·B4★ P1d·C3★ | P2a·B4~ P2b·C3~ P2c·C4~ P2d·B3~ | P3a·B3★ P3b·C4★ P3c·A5★ P3d·B3★ | P4a·B3~ P4b·B2~ P4c·C3~ P4d·B3~ | P5a·A5★ P5b·A5★ P5c·B4★ P5d·A4★ | P6a·B3~ P6b·B3~ P6c·C3~ P6d·B3~ | P7a·A4~ P7b·B3~ P7c·B3~ P7d·B3~ | P8a·E3★ P8b·B3★ P8c·C3~ P8d·B2~ | P9a·B3? P9b·C3? P9c·B3? P9d·B3? | P10a·B2? P10b·B3? P10c·B3? P10d·B3? | P11a·B4★ P11b·B4★ P11c·B3★ P11d·B3★ | P12a·B3~ P12b·B4★ P12c·B3~ P12d·B3~ | P13a·A5★ P13b·A5★ P13c·A4★ P13d·B3★ | P14a·B3~ P14b·B3~ P14c·B3~ P14d·B3~ | P15a·?? P15b·B3~ P15c·?? P15d·B4~ | P16a·B4★ P16b·A4★ P16c·B3★ P16d·B3★ | P17a·C2~ P17b·B2~ P17c·C3~ P17d·B3~ | P18a·B2★ P18b·B2★ P18c·B2? P18d·B4★ | P19a·A4★ P19b·A5★ P19c·B3★ P19d·B4★ | P20a·B4★ P20b·B4★ P20c·B3★ P20d·A5★",
  "dimensions": {
    "P1a": {
      "id": "P1a",
      "pos": "Centre-left, non-ideological",
      "tier": "B",
      "int": 4,
      "con": "C2",
      "bsig": ["S001", "S002", "S003"],
      "trg": ["T002"],
      "exp": ["X001"],
      "conf": 3,
      "upd": "20260424",
      "oq": []
    },
    "P1b": {
      "id": "P1b",
      "pos": "Largely egalitarian",
      "tier": "B",
      "int": 3,
      "con": "C2",
      "bsig": ["S065"],
      "trg": [],
      "exp": ["X044"],
      "conf": 3,
      "upd": "20260424",
      "oq": []
    },
    "P1c": {
      "id": "P1c",
      "pos": "Evidence and ethics balanced",
      "tier": "B",
      "int": 4,
      "con": "C3",
      "bsig": ["S005", "S078"],
      "trg": ["T008"],
      "exp": ["X001"],
      "conf": 3,
      "upd": "20260424",
      "oq": []
    },
    "P1d": {
      "id": "P1d",
      "pos": "Aware and engaged but not activist",
      "tier": "C",
      "int": 3,
      "con": "C2",
      "bsig": ["S067"],
      "trg": ["T032"],
      "exp": ["X043"],
      "conf": 3,
      "upd": "20260424",
      "oq": []
    },
    "P5a": {
      "id": "P5a",
      "pos": "Exceptionally broad — data, film, music, astronomy, philosophy, photography",
      "tier": "A",
      "int": 5,
      "con": "C1",
      "bsig": ["S006", "S007", "S011", "S017", "S020"],
      "trg": ["T003"],
      "exp": ["X007", "X009"],
      "conf": 3,
      "upd": "20260424",
      "oq": []
    },
    "P9a": {
      "id": "P9a",
      "pos": "Unknown",
      "tier": null,
      "int": null,
      "con": null,
      "bsig": [],
      "trg": [],
      "exp": [],
      "conf": 1,
      "upd": "20260424",
      "oq": [
        "How does this person naturally express care toward people they are close to?",
        "Do they initiate acts of service or prefer verbal affirmation?"
      ]
    },
    "P13a": {
      "id": "P13a",
      "pos": "Dry, observational, witty — situational",
      "tier": "A",
      "int": 5,
      "con": "C1",
      "bsig": ["S068"],
      "trg": ["T033"],
      "exp": ["X011", "X033"],
      "conf": 3,
      "upd": "20260424",
      "oq": []
    },
    "P19b": {
      "id": "P19b",
      "pos": "Strongly prefers depth over small talk",
      "tier": "A",
      "int": 5,
      "con": "C1",
      "bsig": ["S036", "S037", "S038"],
      "trg": ["T013", "T015"],
      "exp": ["X031"],
      "conf": 3,
      "upd": "20260424",
      "oq": []
    },
    "P20d": {
      "id": "P20d",
      "pos": "Sees self as constantly evolving — very high growth mindset",
      "tier": "A",
      "int": 5,
      "con": "C1",
      "bsig": ["S005", "S081", "S096", "S097"],
      "trg": ["T041", "T050"],
      "exp": ["X051", "X060"],
      "conf": 3,
      "upd": "20260424",
      "oq": []
    }
  },
  "_note": "This is an anonymised example profile showing a subset of dimension records. A complete profile contains all 80 sub-dimension records."
}
```


==============================================================================
  PART 5 — STANDARD PROMPTS
==============================================================================

Three reference prompts. `build_profile` is what you send after the AI has the spec loaded. `update_profile` refreshes an existing profile with new conversation signal. `compare_profiles` produces a compatibility readout for two profiles.


------------------------------------------------------------------------------
FILE: prompts/build_profile.md
------------------------------------------------------------------------------

# Prompt — Build Once Profile

Use this prompt with any AI that has access to your conversation history.
Point the AI at this repository first, then paste this prompt.

---

## The prompt

```
You are building a Once compatibility profile using the Once Codebook v1.0.
Full specification: https://github.com/once-profile/codebook

Read the full codebook before proceeding — specifically:
- All 20 P parameters (parameters/ folder)
- S codes (codebook/S_signals.md)
- T codes (codebook/T_triggers.md)
- X codes (codebook/X_expressions.md)
- C consistency scale (codebook/C_consistency.md)
- Confidence markers (SPEC.md)

RULES:
1. Do NOT ask me any questions
2. Observe only from what I have naturally said in our conversation history
3. Assign confidence honestly:
   ★ = confirmed clearly across multiple signals
   ~ = reasonable inference from indirect signals
   ? = insufficient data — leave unknown
4. For each sub-dimension, identify which S, T, and X codes apply
5. Assign a consistency code (C1-C5) for all non-? dimensions
6. Build the full dimension record for each of the 80 sub-dimensions

OUTPUT FORMAT:
First — the encoding string:
P1a·[Tier][Level][Conf] P1b·[Tier][Level][Conf] ... through P20d

Then — for each sub-dimension, the structured record:
{
  "id": "P1a",
  "pos": "[position on spectrum]",
  "int": [1-5],
  "con": "[C code]",
  "bsig": ["S###", "S###"],
  "trg": ["T###"],
  "exp": ["X###"],
  "conf": [1=unknown, 2=inferred, 3=strong],
  "oq": ["open question if any"]
}

Finally — a brief note on:
- Which 5 dimensions have the strongest signal
- Which 5 dimensions need more conversation to resolve
- Any patterns worth flagging

Begin.
```

---

## Tips

- The longer your conversation history with the AI, the more accurate the profile
- Use the monthly update prompt (update_profile.md) to keep the profile current
- If a dimension comes back as ? run a natural conversation touching that area —
  do not answer direct questions about it
- Compare two profiles using compare_profiles.md


------------------------------------------------------------------------------
FILE: prompts/update_profile.md
------------------------------------------------------------------------------

# Prompt — Update Once Profile

Use this prompt monthly to keep your Once profile current. Paste your existing
encoding string and structured records, then run this prompt with any AI that
has access to your recent conversation history.

---

## The prompt

```
You are updating an existing Once compatibility profile using the Once Codebook v1.0.
Full specification: https://github.com/once-profile/codebook

My current profile encoding string is:
[PASTE YOUR ENCODING STRING HERE]

My current dimension records are:
[PASTE YOUR FULL JSON RECORDS HERE]

Read the codebook fully before proceeding.

RULES:
1. Do NOT ask me any questions
2. Review only our conversation history from the past 30 days
3. For each dimension:
   - If new strong signal confirms an existing ~ or ? — upgrade confidence
   - If new signal contradicts an existing ★ — flag it as conflicted, do not auto-change
   - If a dimension value has genuinely shifted — update with note
   - If nothing new — leave unchanged
4. Never downgrade confidence automatically — only upgrade or flag
5. Add any newly identified S, T, or X codes to existing records

OUTPUT FORMAT:
First — the updated encoding string (changed dimensions marked with *)
Then — only the dimension records that changed, with a note explaining what changed and why
Finally — list any dimensions flagged as conflicted for human review

Begin.
```

---

## When to run this

- Once a month minimum
- After any major life event — new job, relationship change, move, significant experience
- After a long conversation that covered new personal territory
- Whenever your encoding string feels outdated

---

## Notes

- Your profile should evolve. A profile that never changes isn't being updated — it's stale.
- Conflicted dimensions are valuable — they mean you are genuinely changing.
  Review them honestly rather than defaulting to the old value.
- Store your profile version history so you can see how you've changed over time.


------------------------------------------------------------------------------
FILE: prompts/compare_profiles.md
------------------------------------------------------------------------------

# Prompt — Compare Two Once Profiles

Use this prompt to assess compatibility between two Once profiles.
This is the core matching logic — used by the Once app internally
and available publicly for anyone to use.

---

## The prompt

```
You are comparing two Once compatibility profiles using the Once Codebook v1.0.
Full specification: https://github.com/once-profile/codebook

Profile A encoding string:
[PASTE PROFILE A ENCODING STRING]

Profile A dimension records:
[PASTE PROFILE A JSON RECORDS]

Profile B encoding string:
[PASTE PROFILE B ENCODING STRING]

Profile B dimension records:
[PASTE PROFILE B JSON RECORDS]

Read the codebook fully before proceeding.

MATCHING RULES:

1. CONFIDENCE WEIGHTING
   ★ dimensions = full weight in scoring
   ~ dimensions = 50% weight in scoring
   ? dimensions = excluded from scoring entirely

2. DIMENSION WEIGHTING (apply in this order)
   Tier 1 — Dealbreakers (check first, hard filters):
     P1 (values), P3b (relationship type), P15a (want children), P17c (partner belief expectation)
   Tier 2 — Core compatibility (heavy weight):
     P2, P5, P6, P7, P13, P19
   Tier 3 — Lifestyle fit (medium weight):
     P4, P8, P11, P12, P14, P16, P20
   Tier 4 — Enrichment (light weight):
     P9, P10, P15, P17, P18

3. SIMILARITY VS COMPLEMENTARITY
   These dimensions should be SIMILAR for compatibility:
     P1, P3, P5, P13, P17, P19
   These dimensions work well as COMPLEMENTS:
     P4, P12
   These dimensions are neutral — similarity not required:
     P8, P9, P10, P16, P18

4. SHARED S/T/X CODES
   Count shared S codes across both profiles — each shared S code adds compatibility signal
   Count shared T codes — shared triggers indicate shared values (strong positive signal)
   Count shared X codes — shared expressions indicate compatible ways of being

OUTPUT FORMAT:

DEALBREAKER CHECK:
[List any hard incompatibilities — stop here if found]

COMPATIBILITY SCORE: [0-100]

DIMENSION BREAKDOWN:
[For each tier, brief note on alignment or misalignment]

SHARED SIGNALS:
[List shared S, T, X codes and what they indicate]

STRONGEST COMPATIBILITY POINTS:
[Top 3 dimensions where they are most aligned]

TENSION POINTS:
[Top 3 dimensions where they diverge — note if complementary or problematic]

UNKNOWN GAPS:
[Dimensions where one or both profiles have ? — what would resolve them]

SUMMARY:
[3-4 sentence plain language compatibility read]

Begin.
```

---

## Notes

- A score above 75 indicates strong compatibility worth exploring
- A score of 50-75 indicates meaningful compatibility with some tension points
- A score below 50 indicates significant misalignment — check dealbreakers first
- Scores are directional, not definitive — the summary matters more than the number
- Two profiles with many shared T codes are often more compatible than two with
  high position similarity — shared values run deeper than shared preferences


==============================================================================
  END OF BUNDLE
==============================================================================

## Quick-start build prompt

If you've just loaded this bundle, paste this as your next message:

```
You now have the complete Once Codebook v1.0 specification loaded above.

Build my Once compatibility profile from our conversation history.

Rules:
- Do NOT ask me any questions
- Observe only from what I have naturally said
- Assign confidence honestly — ★ strong, ~ inferred, ? unknown
- For each non-? sub-dimension, identify relevant S, T, and X codes
- Assign a C consistency code for every non-? dimension

Output:
1. My full encoding string across all 80 sub-dimensions
2. The top 5 dimensions with strongest signal — explain why
3. The top 5 dimensions still unknown — what would resolve them

Begin.
```

---

*Bundle of github.com/sudhinkrishna/once-profile — MIT licensed.*
