# The guarantees we hold ourselves to

These six commitments are load-bearing. The whole system is designed so they *cannot* be
quietly violated, and they are enforced in code and in review — not left to good intentions.

### 1. No claim without a source

Every surfaced claim — a bill narrows / removes / expands something, a scrutiny finding, a
"who benefits" line — is backed by **verbatim source text plus a clause or section citation**.
If there is no grounded source, there is no claim.

### 2. Source text is never truncated

Text that feeds analysis is never silently capped, sliced, or truncated. (An early version once
capped a source snapshot and produced false "not found" conclusions — never again.) The full
captured text is what gets hashed, what feeds the analysis, and what a claim is checked against.

### 3. Provenance is cryptographic and site-wide

Published data and artifacts carry **SHA-256 provenance**, chained so any tampering is evident.
A hashed record is never mutated without re-chaining, and the chains are verified in continuous
integration. See **[Source provenance](provenance.md)**.

### 4. Published judgements clear a multi-model bar

A published *judgement* — a kept scrutiny finding, a harm reading — must clear
**multi-model verification**, not a single model's opinion. Deterministic evidence can stand on
its own; the subjective verdict is the part that needs the panel.

### 5. A human decides

Nothing reaches the public without passing a human-review gate. The AI produces a recommendation
with cited evidence; a person reviews it and approves or overrides. The model never publishes on
its own.

### 6. Never assert motive; never accuse an individual

We surface **sourced patterns, not intent.** We do not claim anyone intended a result, and we do
not accuse a named individual — user-facing copy and prompts are kept neutral by design. This is
an ethic and a deliberate defamation defence at once: boringly accurate over persuasive.
