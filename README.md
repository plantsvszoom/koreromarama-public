# Kōrero Mārama — public methodology & transparency kit

**Kōrero Mārama** (te reo Māori: *clear understanding* — to shed light on something) is a
public-interest project that makes New Zealand legislation readable, and holds every claim it
surfaces to a strict evidentiary standard.

This repository is the **open face** of the project. It contains the method, the guarantees the
project holds itself to, and the **exact verification prompts** the engine runs — published so
anyone can inspect and reproduce how a claim gets checked. The product's data pipeline and
application code are maintained separately; everything needed to understand and reproduce the
*method* is here.

## What the project is

Legislation is where power is actually exercised — but it is written to be read by lawyers, and
its substance is often dispersed across a bill, the Acts it amends, delegated regulations, and
official advice. Kōrero Mārama re-aggregates that into plain language, and refuses to state
anything it cannot back with the source text itself.

The goal is accountability by a **neutral method**: clear, sourced facts so the public can hold
power to account — never telling anyone what to think or how to vote.

## What's in this repo

- **[Mission](docs/mission.md)** — the north star and what "neutral method" means here.
- **[The guarantees we hold ourselves to](docs/invariants.md)** — six load-bearing commitments.
- **[How we verify](docs/methodology.md)** — the source-grounded, multi-model, human-gated method.
- **[Source provenance](docs/provenance.md)** — how published data is made tamper-evident with SHA-256 chains.
- **[The verification prompts](prompts/)** — the exact prompts the engine runs, so any check is reproducible.

## The one-line guarantee

> **No claim without a source.** Every surfaced claim — that a bill narrows, removes, or expands
> something; who a provision appears to benefit — is backed by verbatim source text and a
> clause/section citation. No grounded source, no claim.

## How it's built

Analysis is never published on a single model's say-so. Each factual claim is checked
**adversarially by three independent open-weight models** (DeepSeek V4 Pro, Qwen3, Llama 3.3 70B),
each of which must cite a verbatim quote from the stored source to call a claim supported. A
flagship adjudicator (**Claude Opus 4.8**) reconciles any disagreement into one recorded verdict
per claim. **Nothing is published until a human reviews the evidence and approves it.**

The method is versioned (currently `spb-v8`) and the prompts in this repo are the ones that run.

## Reproduce a check

For any published item you can take (1) the stored source snapshot, (2) the named models, and
(3) the [exact prompts](prompts/), re-run the check, and compare against the recorded reasoning.
The verification is the receipt.

## License

Documentation and prompts in this repository are released under
**[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE)** — reuse freely, just
attribute Kōrero Mārama. (The separate provenance-ledger *library* — see
[docs/provenance.md](docs/provenance.md) — is released under the MIT License in its own package.)
