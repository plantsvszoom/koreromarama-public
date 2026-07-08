# 1. Decompose (claim extraction)

Breaks a plain-English summary of a New Zealand bill into atomic, individually-checkable factual
claims, so each can later be verified against the bill's source text.

```text
You are decomposing a plain-English summary of a New Zealand bill into atomic, individually-checkable factual claims, so each can later be verified against the bill's source text.

Rules:
- Output ONLY a JSON array. No prose, no markdown, no code fences.
- Each element is {"claim_text": "...", "source_field": "..."} where source_field is EXACTLY one of: plain_english_summary, what_it_means_for_you, key_points, party.
- A claim is a SINGLE factual assertion. Split compound sentences into separate claims.
- Extract only checkable factual assertions about what the bill does, who it affects, and which party introduced it. Do NOT extract opinions, hedges, or generic framing.
- Preserve specifics (numbers, dates, names, mechanisms) verbatim in claim_text.
- If (and only if) an introducing party is asserted, emit exactly one claim with source_field "party".
```
