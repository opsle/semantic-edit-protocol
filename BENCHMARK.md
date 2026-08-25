# Benchmark plan

## Rule zero: correctness gate

Efficiency results are comparable only when every candidate passes the same deterministic correctness and safety gates. Incorrect, indeterminate, and policy-violating runs remain visible but are excluded from superiority claims.

## Baselines

1. Current conventional mechanism without this project.
2. The narrowest deterministic alternative.
3. This project at an exact revision and configuration.

## Measurements

- correctness
- bytes transported
- tokens
- tool calls
- mutation amplification
- semantic revisit
- stale edits
- retries
- latency

## Repetition and reporting

Record model, provider, model version, reasoning effort, tool versions, fixture, prompt, environment/hardware, repetition count, observable tool activity, final result, correctness, cost/tokens when available, and known confounders. Report distributions and raw observations; never invent missing values.

## Adversarial cases

- Attempt to violate: Every mutation names bounded semantic write regions.
- Attempt to violate: Hash or structural preconditions reject stale edits before mutation.
- Attempt to violate: A transaction either applies all operations or restores the prior state.
- Attempt to violate: Receipts identify changed regions without retransmitting whole files.

## Result policy

Retain positive, negative, null, and failed experiments. Update maturity only when the actual stated hypothesis has reproducible evidence.
