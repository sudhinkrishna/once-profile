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
