# Dispatch Patterns

The main thread chooses the lightest workflow that protects the research objective. Escalate when evidence, physics, or reproducibility risk increases.

## Level: quick

Use for local, low-risk tasks with no durable scientific consequence.

Main thread flow:

1. State the immediate goal.
2. Inspect the minimum necessary files, command output, or context.
3. Execute directly unless parallel inspection is clearly useful.
4. Report result, uncertainty, and optional follow-up.

Records: none unless the result changes project memory.

Stop or upgrade when:

- The task reveals a physical assumption, experiment design issue, or result interpretation problem.
- The user asks for continuity, strict review, or project handoff.

## Level: standard

Use for ordinary research implementation, data processing, experiment scripts, module edits, stage summaries, or non-final analysis.

Main thread flow:

1. Define objective, scope, success criteria, and out-of-scope boundaries.
2. Build a compact scientific framing.
3. Use `Execution Planner` when work spans multiple files, scripts, data products, or verification stages.
4. Execute locally or dispatch bounded `Implementation Agent` tasks.
5. Run feasible verification and inspect outputs.
6. Perform a basic review against the objective and scientific framing.
7. Update `worklog.md` and `handoff.md` when a project record directory exists.
8. Final response includes conclusion, completed work, verification, risks, and next actions.

Standard context packet:

```text
Task level: standard
Objective:
Scientific framing:
Known constraints:
Relevant files/data:
Allowed write scope:
Forbidden changes:
Expected output:
Verification required:
Record directory, if any:
Relevant companion tools/skills:
```

Upgrade to critical when:

- A physical definition, threshold, label, metric, or assumption changes.
- Verification results affect a thesis/paper/report conclusion.
- The work determines whether an experiment is scientifically valid.
- The user asks for independent review.

## Level: critical

Use for physics assumptions, core algorithms, final or near-final conclusions, direction changes, high-impact experiments, reproducibility-critical workflows, or domain logic where mistakes are scientifically costly.

Main thread flow:

1. Define research objective, scientific claim at risk, success criteria, and stop conditions.
2. Read current `handoff.md`, `physics-core.md`, `decisions.md`, and recent `reviews.md` if they exist.
3. Dispatch `Physics Translator` unless the required framing is already current and explicit.
4. Convert approved framing into a plan via `Execution Planner` or main-thread planning.
5. Execute through bounded tasks; keep write scopes disjoint when using multiple agents.
6. Verify outputs with commands, data checks, figures, metrics, or artifact inspection as appropriate.
7. Dispatch `Physics Reviewer` independently with objective, physics core, plan/result, and evidence.
8. Use `Evidence Auditor` when claims depend on metrics, plots, logs, datasets, citations, or reproducibility details.
9. Resolve conflicts explicitly; decide corrections in the main thread.
10. Update records: `worklog.md`, `reviews.md`, `decisions.md` when applicable, and `handoff.md`.
11. Final response states conclusion, gate status, evidence, risks, decisions, and next actions.

Critical context packet:

```text
Task level: critical
Research objective:
Scientific claim at risk:
Physics core:
Current hypothesis:
Relevant evidence/files:
Allowed scope:
Forbidden changes:
Required review gates:
Expected output schema:
Decision owner: main thread
```

## Dispatch Hygiene

- Do not dump full history into a sub-agent. Send objective, boundary, evidence, and schema.
- Prefer records and must-read files over long chat summaries.
- Implementation agents do not make physical validity decisions.
- Review agents do not implement fixes unless separately assigned.
- If sub-agent outputs conflict, list the conflict, evidence on each side, and main-thread decision.
- If evidence is insufficient, stop at a provisional conclusion and record what is missing.
- Important tasks end with next actions that a future thread can execute.
