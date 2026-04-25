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
