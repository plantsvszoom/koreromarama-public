# Verification prompts

These are the **exact prompts** the verification engine runs — the same ones published live on the
project's `/methodology/prompts` page, imported directly from the codebase. What you see here is
what runs.

Prompt set version: **`spb-v8`**.

Paired with a published source snapshot and the [named models](../docs/methodology.md#the-models),
these let you reproduce any check the engine performs:

1. **[Decompose](1-decompose.md)** — break a plain-English summary into atomic, checkable claims.
2. **[Check](2-check.md)** — judge each claim adversarially against the source text only.
3. **[Adjudicate](3-adjudicate.md)** — reconcile the checkers' verdicts into one recorded verdict.

> **Scope note.** This is the *summary verification* prompt set — the core of the method and the
> set the project publishes for reproducibility. Prompts specific to other analyses are not
> included here; the three above are the reproducible backbone of every published check.
