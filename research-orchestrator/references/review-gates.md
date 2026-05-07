# Review Gates

Use these gates before accepting critical scientific work, and selectively for standard work when risk rises.

## Gate 1: Physics Consistency

Pass only when:

- The physical objective is explicit.
- Variables, observables, thresholds, and diagnostics preserve their stated meaning.
- Algorithmic steps do not silently change the physical assumption.
- Known limitations are stated as limitations, not conclusions.

Fail or pause when:

- A physical concept is used without definition.
- A code shortcut, metric, or threshold changes the scientific interpretation.
- The result depends on an assumption the user has not accepted.

## Gate 2: Evidence Sufficiency

Pass only when each important claim has traceable support:

- Code claim: file path, function/module, line or behavior evidence.
- Experiment claim: command/config, data source, output artifact, metric or figure.
- Scientific claim: observation, diagnostic, comparison, literature, or explicit reasoning chain.
- Project-state claim: record entry, decision note, or handoff evidence.

If evidence is incomplete, label the conclusion provisional and record missing evidence.
## Gate 3: Reproducibility

Pass only when relevant reproducibility details are captured:

- Input data identity, time range, case list, or version.
- Script, command, config, model checkpoint, environment, or random seed when applicable.
- Output location and how to regenerate or inspect the result.
- Known nondeterminism or operational constraints.

Fail or pause when a reported result cannot be traced back to inputs and execution conditions.

## Gate 4: Implementation Integrity

Pass only when:

- Changes are inside the intended scope or deviations are justified.
- Existing experiment logic is preserved unless explicitly changed.
- Verification was run or the reason it could not be run is stated.
- Failure modes and residual risks are visible.

Fail when code correctness is asserted without inspection, tests, or defensible reasoning.

## Gate 5: Handoff Completeness

Pass only when the next thread can continue without reconstructing the project from chat history:

- Current goal and state are clear.
- Completed work, open tasks, risks, and blockers are listed.
- Must-read files are named.
- Decisions and their evidence are recorded or summarized.

For critical work, do not finish without either updating records or providing a compact handoff block in the final response.

## Verdict Language

Use one of these verdicts:

- `pass`: gates satisfied; normal continuation is safe.
- `pass_with_risks`: usable, but listed risks must remain visible.
- `fail`: do not accept conclusion or merge work until corrections are made.
- `insufficient_evidence`: cannot judge; gather specific missing evidence next.
