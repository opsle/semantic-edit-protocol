# Theory

## Observation

Whole-file transport and repeated text patches can inflate payloads, overwrite concurrent work, and apply against stale structure.

## Hypothesis

Bounded semantic operations with structural and hash preconditions can reduce transport and stale edits without reducing correctness.

## Proposed mechanism

Represent a Change Intent Graph over semantic regions and apply AST-aware operations such as bounded replacement, symbol rename, and structural insertion in an atomic transaction with rollback and concise receipts.

## Falsifiable requirements

1. Every mutation names bounded semantic write regions.
2. Hash or structural preconditions reject stale edits before mutation.
3. A transaction either applies all operations or restores the prior state.
4. Receipts identify changed regions without retransmitting whole files.

## Disconfirming results

The hypothesis should be weakened or rejected if a comparable baseline passes the same correctness gate and this mechanism provides no repeatable benefit, or if the mechanism introduces safety/correctness failures that bounded revisions do not resolve. Negative results remain in `experiments/`.

## Uncertainty

Language adapters, conflict semantics, anchor durability measurements, and controlled comparisons with patch and whole-file editing.
