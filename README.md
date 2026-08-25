# Semantic Edit Protocol

> Experimental Opsle research. Claims are hypotheses until evidence supports them.

## Problem

Whole-file transport and repeated text patches can inflate payloads, overwrite concurrent work, and apply against stale structure.

## Hypothesis

Bounded semantic operations with structural and hash preconditions can reduce transport and stale edits without reducing correctness.

## Mechanism

Represent a Change Intent Graph over semantic regions and apply AST-aware operations such as bounded replacement, symbol rename, and structural insertion in an atomic transaction with rollback and concise receipts.

## Why it matters

The Opsle thesis asks: **What if we stopped using intelligence for work that doesn’t require intelligence?** This project isolates one candidate boundary so it can be falsified and measured independently.

## Non-goals

A universal AST, unconstrained natural-language editing, or replacing ordinary patches when they are already the best mechanism.

## Current maturity

**THEORY** under the [Opsle maturity model](https://github.com/opsle/research/blob/main/MATURITY.md).

## Existing evidence

The hypothesis is motivated by observed edit churn; no general superiority benchmark exists yet.

## Evidence still missing

Language adapters, conflict semantics, anchor durability measurements, and controlled comparisons with patch and whole-file editing.

## Benchmark strategy

Correctness gates every comparison. Planned measures:

- correctness
- bytes transported
- tokens
- tool calls
- mutation amplification
- semantic revisit
- stale edits
- retries
- latency

See [BENCHMARK.md](BENCHMARK.md) for experiment rules. No benchmark numbers are claimed.

## Relationship to other Opsle research

This project is part of [Opsle Research](https://github.com/opsle/research). Opsle Tasks is the future public name of the integrated reference system from which several ideas emerged. Its active development migration to the Opsle organization is intentionally deferred.

## Relationship to future Opsle Tasks

Future Opsle Tasks may consume this project through an adapter only after evidence supports integration. The active predecessor, Taslos Tasks, remains unchanged and has no dependency on this repository.

## Installation status

No installable production package is justified yet. The repository is theory/specification-first.

## Known limitations

Language adapters, conflict semantics, anchor durability measurements, and controlled comparisons with patch and whole-file editing.

## License

Apache-2.0. See [LICENSE](LICENSE).
