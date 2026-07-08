# How we verify

*This mirrors the project's canonical, version-stamped method document. Method version: `spb-v8`.*

Every bill summary and election promise is checked against a **primary source** before a human
approves it for publication — bill summaries against the bill's own text, promises against the
party's own policy page (fetched and snapshotted at the time of checking). We do this in the open,
with models whose results anyone can reproduce. **Nothing is published automatically.**

## The method

1. **Capture the source.** When analysis is generated, an immutable snapshot of the source text is
   stored with a SHA-256 hash, so it is tamper-evident. (See [provenance](provenance.md).)
2. **Break it into claims.** The summary is decomposed into individual factual claims, each tied to
   the part of the text it came from.
3. **Check each claim, adversarially.** Three independent open-weight models each judge every claim
   *against the stored source only*, and must cite a direct verbatim quote to call a claim supported.
4. **Adjudicate.** A final model reconciles any disagreement into one verdict per claim, recording
   its reasoning.
5. **A human decides.** The verdicts and evidence are shown to an editor, who approves or rejects.
   Only then is anything published.

## The models

Claims are checked by three open-weight models so the checks are independently reproducible:

| Role | Model | Notes |
|---|---|---|
| Checker | **DeepSeek V4 Pro** | open weights |
| Checker | **Qwen3** | open weights |
| Checker | **Llama 3.3 70B** | open weights |
| Adjudicator (premium) | **Claude Opus 4.8** | reconciles only; never originates a verdict |
| Adjudicator (economy) | **Claude Sonnet 4.6** | batched pass for the older back-catalogue |

The named models are current as of method version `spb-v8`; the live methodology page is canonical
if they change.

## Two tiers, one method

Bills are verified in two tiers that use **exactly the same method** (three independent checkers +
adjudicator + human gate). The difference is cost, not rigour:

- **Premium** — for bills before Parliament or recently enacted: the adjudicator runs per-claim with
  the source cached, grounding each claim individually against the full text.
- **Economy** — for the older back-catalogue: an adjudicator processes all claims in one batched
  pass against the source, keeping costs proportionate for bills unlikely to change.

Each published verification page shows a **Verified · premium** or **Verified · economy** badge.

## Who Benefits?

For each bill we ask which groups its provisions appear to advantage. The analysis is grounded
strictly in the bill's own text: every finding cites a specific clause, verified word-for-word by
three independent models before an editor approves it. We name **categories** of beneficiary (for
example "large-scale processors") rather than specific companies, unless the bill itself names them.
The language is deliberately hedged — it describes who a law *appears* to benefit, never an
assertion of intent — and the same method runs on every bill regardless of which party introduced it.

## Reproduce it yourself

For any published item, take (1) the stored source snapshot, (2) the named models above, and
(3) the [exact prompts](../prompts/), re-run the check, and compare against the reasoning we
recorded. **The verification is the receipt.**
