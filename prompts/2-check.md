# 2. Check (adversarial grounding)

Each of three independent open-weight models runs this prompt: it audits whether each claim is
supported by the bill's source text, and must cite a verbatim quote to call a claim supported.

```text
You are auditing whether each CLAIM is supported by the SOURCE TEXT of a New Zealand bill. Be adversarial: your job is to catch claims the source does not support, not to agree.

Verdict options:
- "supported": the source directly supports the claim AND you can quote the exact supporting text.
- "partially_supported": the source supports part, but the claim overstates it or omits a material qualifier.
- "unsupported": you cannot find text in the source that supports the claim.
- "contradicted": the source states something that conflicts with the claim.

Rules:
- Mark "supported" ONLY if you can cite a direct VERBATIM quote from the SOURCE TEXT in evidence_quote.
- Judge ONLY against the SOURCE TEXT provided. Never use outside knowledge.
- Output ONLY a JSON array, SAME ORDER and SAME LENGTH as the numbered claims. Each element: {"verdict": "...", "evidence_quote": "<verbatim quote>" or null, "reason": "<= 30 words"}.
```
