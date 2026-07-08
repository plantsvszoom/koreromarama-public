# Source provenance

Transparency is only credible if the *inputs* are tamper-evident. Kōrero Mārama makes every piece
of published data cryptographically accountable with **SHA-256 hash chains** — the same idea that
underlies a git history or a blockchain, applied to civic data.

## Why this exists

If a tool claims "this is what the bill said," a reader has to be able to trust that the stored
source hasn't been quietly edited after the fact — including by us. Hashing each record and
chaining the hashes means any change to any past record is detectable, and the current state of a
chain can be pinned and checked by anyone.

## How the chains work

Each protected record stores the hash of its own content **and** the hash of the record before it:

```
record_n.ledger_hash = SHA-256( content_hash_n  +  ledger_hash_(n-1) )
```

- The first record links to a fixed **genesis** value.
- Because each link folds in the one before it, you cannot alter, insert, or remove a past record
  without breaking every link after it.
- The **head** (the latest link) is pinned to a committed **anchor** file. If the live head ever
  stops matching the anchor, verification fails loudly.

The project runs three such chains:

| Chain | Protects |
|---|---|
| **Sources** | The captured source snapshots that analysis is grounded on. |
| **Artifacts** | Original published artifacts (e.g. archived PDFs). |
| **Edit history** | The record of human edits to findings, so review decisions are auditable. |

Continuous integration verifies all three chains on every change; a broken chain is a build
failure. Repairs (rare, and only to restore a missing link — never to change content) are recorded
in a **self-hashed, transparent repair log** so the repair itself is tamper-evident.

## The provenance-ledger library

The chain mechanism is small, self-contained, and genuinely reusable by any project that wants
tamper-evident provenance over published data. It is being extracted into a standalone
**MIT-licensed** package so others can adopt it. *(Coming soon — this section will link to the
package when published.)*

## What this does **not** do

This mechanism proves that a stored record has not been altered since it was captured. It does not,
by itself, judge whether the *content* is accurate — that is the job of the
[verification method](methodology.md) and the human review gate. Provenance and verification are
two different guarantees, and Kōrero Mārama holds both.
