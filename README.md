# Once Profile Codebook

> A universal open standard for encoding human compatibility profiles.

---

## What is this?

The Once Codebook is an open specification for representing who someone is — across **20 psychological parameters**, **80 sub-dimensions**, and **270 behavioural signal codes** — in a structured format that any AI can read, build, and compare.

It was designed for [Once](https://github.com/sudhinkrishna/once-profile) — a weekly matchmaking app that connects one person to one other person every week, based on deep compatibility rather than surface-level preferences. But the codebook itself is open. Any AI, any platform, any developer can use it.

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

Each parameter has 4 sub-dimensions, full A–E spectrum definitions, and a dealbreaker rating to guide matching weight.

| Code | Parameter | Sub-dimensions | Dealbreaker |
|------|-----------|----------------|-------------|
| P1 | Values and worldview | Political orientation, gender role views, moral framework, social justice orientation | High |
| P2 | Emotional temperament | Expressiveness, emotional stability, empathy level, sensitivity to criticism | Medium |
| P3 | Life goals | Where they want to live, relationship type, personal growth priority, timeline urgency | High |
| P4 | Social style | Introvert vs extrovert, social circle size, need for alone time, social spontaneity | Medium |
| P5 | Intellect and curiosity | Curiosity breadth, love of learning, debate style, creative thinking | Medium |
| P6 | Conflict style | Confrontation comfort, resolution approach, forgiveness speed, stubbornness | Medium-High |
| P7 | Attachment style | Base type, closeness comfort, independence need, trust building speed | Medium-High |
| P8 | Practical lifestyle | Travel, financial habits, daily rhythm, living style | Medium |
| P9 | Love language | Primary give, primary receive, affection frequency, physical affection comfort | Low-Medium |
| P10 | Anger and mood management | Expression style, trigger sensitivity, cooldown time, mood contagion | Medium |
| P11 | Altruism and kindness | Generosity, stranger kindness, cause orientation, reciprocity expectation | Low-Medium |
| P12 | Dominance vs submissiveness | Decision-making, opinion assertiveness, compromise willingness, leadership | Medium |
| P13 | Sense of humour | Style, frequency, self-deprecation comfort, humour boundaries | Low-Medium |
| P14 | Emotional availability | Openness timing, vulnerability comfort, support style, emotional bandwidth | Medium-High |
| P15 | Family orientation | Want children, family centrality, parenting style, extended family involvement | High |
| P16 | Ambition and career | Career centrality, ambition level, work-life balance, financial ambition | Medium |
| P17 | Spirituality and religion | Religious identity, practice frequency, partner expectation, spiritual worldview | High |
| P18 | Physical lifestyle | Fitness orientation, health consciousness, substance use, outdoor vs indoor | Low-Medium |
| P19 | Communication style | Directness, conversation depth, digital communication, listening style | Medium |
| P20 | Openness to change | Adaptability, opinion flexibility, risk tolerance, growth mindset | Low |

> **Note on categorical sub-dimensions:** Most sub-dimensions are ordinal (A is one extreme, E is the other). A few are categorical — P9a and P9b (love language give/receive) and P13a (humour style). For these, compatibility is about category match, not tier similarity. See the individual parameter files for details.

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

There are two ways to load the codebook into an AI, depending on what your AI can do.

### Option A — AI with reliable web access (Claude, Gemini, Perplexity)

Point the AI at this repository and use the build prompt:

```
Read the Once Codebook at github.com/sudhinkrishna/once-profile.

Using the full specification — P parameters, S/T/X codes, C consistency 
scale, and confidence markers — build my Once profile from our 
conversation history.

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

### Option B — AI that can't browse (free ChatGPT, custom GPTs, local models)

Most AI surfaces can't reliably read a multi-file GitHub repo at runtime. For these, use the single-file bundle:

1. Open **[codebook-bundle.md](./codebook-bundle.md)** — the entire codebook in one file
2. Paste its full contents into the chat as your first message (or attach it as a file in tools that support uploads — Claude Projects, custom GPTs, Gemini Gems)
3. Send the build prompt above as your second message

The bundle contains the README, all 20 parameter definitions, all 270 lookup codes, the JSON schemas, and the standard prompts — everything needed to build a profile, in one paste.

---

## Repository structure

```
once-profile/
├── README.md                    — This file
├── codebook-bundle.md           — Full spec in one file (for AIs without web access)
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

*Built by [Once](https://github.com/sudhinkrishna/once-profile) — one person, one week, one real connection.*
