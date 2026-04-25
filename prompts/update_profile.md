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
