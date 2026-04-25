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
