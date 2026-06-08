---
name: research-orchestrator
description: Use when a research task is long-running, domain-sensitive, evidence-heavy, multi-agent, or requires project memory, scientific handoff, experiment governance, reproducibility review, or independent review before conclusions change.
---

# Research Orchestrator

## Purpose

`research-orchestrator` is a governance skill for scientific work where the cost of losing domain meaning, project continuity, or evidence discipline is high.

It does not replace domain, coding, document, or GitHub skills. It decides how to frame the research objective, when to delegate, what evidence is required, how results are reviewed, and what must be recorded for future threads.

## Operating Principles

- Domain meaning before implementation: define the scientific question before changing code, experiments, or conclusions.
- Evidence before claims: separate observations, assumptions, inferences, and decisions.
- Main thread owns judgment: sub-agents provide bounded analysis, implementation, and review; they do not make final project decisions.
- Execution and review are separate whenever conclusions, core algorithms, or scientific assumptions may change.
- Records are part of the work, not afterthoughts, for standard and critical tasks.

## Trigger Logic

Use this skill when any of these are true:

- The task affects a research project that spans multiple sessions, experiments, papers, reports, or code modules.
- The task depends on domain interpretation: physical variables, biological measurements, model diagnostics, experimental conditions, statistical definitions, quality-control rules, or similar scientific logic.
- The user asks for project continuity, handoff, record keeping, strict review, sub-agent coordination, or not losing the scientific thread.
- The work may alter a hypothesis, scientific assumption, algorithmic definition, experiment design, result interpretation, or thesis/paper conclusion.
- The task needs multiple independent viewpoints: translation, planning, implementation, scientific review, or record synthesis.

Do not use this skill for isolated factual questions, one-command checks, ordinary local edits with no scientific consequence, or short conversation that does not require memory or review.

## Level Selection

Select the smallest level that protects scientific quality. Upgrade immediately if later evidence shows higher risk.

| Level | Use When | Required Governance |
|---|---|---|
| `quick` | Local inspection, simple explanation, small non-scientific edit, low-risk command | Direct work, concise result, risk note |
| `standard` | Ordinary experiment scripts, data processing, module edits, stage summaries, non-final analysis | Scope, plan, execute, verify, basic review, record update when records exist |
| `critical` | Scientific assumptions, core algorithms, validation logic, thesis/paper conclusions, direction changes, or reproducibility-critical experiments | Domain translation, execution plan, bounded execution, independent scientific review, decision record, handoff |

Automatic upgrade to `critical` when the task changes any of these:

- Definition of a scientific variable, threshold, diagnostic, or quality-control criterion.
- Mapping from scientific concept to algorithm, model input, label, loss, metric, or validation design.
- Interpretation of figures, experiments, case studies, ablations, or paper/report conclusions.
- Long-term project state, record structure, or handoff that future work will rely on.

## Main Thread Responsibilities

The main thread must explicitly own these decisions:

- Research objective, scope, success criteria, and out-of-scope boundaries.
- Task level and any escalation or de-escalation rationale.
- Context packet given to each sub-agent.
- Acceptance or rejection of sub-agent outputs.
- Final scientific interpretation and next action.
- Record updates for `standard` and `critical` work.

## Scientific Framing Checklist

Before planning a `standard` or `critical` task, write or infer a compact framing:

- scientific_objective: what process, phenomenon, mechanism, model behavior, or analytical claim is being protected or tested?
- scientific_claim_at_risk: what claim could become wrong if the work drifts?
- observables: measured variables, model outputs, metrics, datasets, logs, or figures involved, with units or definitions when known.
- assumptions: explicit assumptions and unknowns.
- evidence_available: files, figures, logs, datasets, prior records, or papers already available.
- success_criteria: reproducible condition for accepting the work.

If this framing cannot be completed for a critical task, pause execution and ask for the missing scientific definition unless it can be discovered from project records.

## Sub-Agent Policy

Read `references/agent-cards.md` only when delegation is useful. Do not expand all role cards by default.

| Role | Use |
|---|---|
| `Domain Translator` | Required for critical tasks before implementation unless an equivalent domain-core record already exists and is current. |
| `Execution Planner` | Use when work spans multiple files, experiments, data products, or verification steps. |
| `Implementation Agent` | Use for bounded code, data, experiment, or document execution with clear write scope. |
| `Scientific Reviewer` | Required for critical tasks after plan or implementation; must be independent from executor. |
| `Evidence Auditor` | Use when claims depend on logs, figures, metrics, datasets, citations, or reproducibility evidence. |
| `Research Scribe` | Use or perform directly for standard and critical record updates. |

Sub-agents receive minimal context: objective, level, domain core, evidence, allowed scope, forbidden changes, expected output schema, and verification requirements.

## Dispatch And Review References

- For role cards and output schemas, read `references/agent-cards.md`.
- For level-specific workflows and context packets, read `references/dispatch-patterns.md`.
- For scientific acceptance gates, read `references/review-gates.md`.
- For record files and templates, read `references/record-templates.md`.

## Records And Handoff

For a recognized project, prefer a record directory such as:

```text
research/<project-name>/
  project-brief.md
  domain-core.md
  decisions.md
  worklog.md
  reviews.md
  handoff.md
```

If no record directory exists, do not invent project facts. Ask whether to create one when the task is standard or critical and continuity matters. If the user asks to proceed without records, include a concise handoff block in the final response.

## Completion Gates

Before final response:

- `quick`: report action, result, and any uncertainty or risk.
- `standard`: verify feasible outputs, perform basic objective review, update records if available, and list residual risks.
- `critical`: pass or explicitly fail the relevant gates in `references/review-gates.md`; record decisions, evidence, unresolved risks, next actions, and must-read files.

Do not claim a scientific conclusion is established unless the evidence gate and domain-consistency gate both pass.

## Coordination With Other Skills

This skill is the orchestration layer, not an exclusive toolset. The main thread and delegated sub-agents may use relevant tools, MCPs, scripts, and specialized skills inside this governance structure:

| Situation | Preferred Companion |
|---|---|
| Feature, bugfix, refactor | TDD, systematic debugging, requesting code review |
| PR or GitHub workflow | GitHub skills or work-with-pr |
| Documents, slides, spreadsheets | documents, presentations, spreadsheets |
| New or revised skill | skill-creator, writing-skills |
| Large research project | research-orchestrator remains the top-level coordinator |

If another skill's workflow conflicts with scientific governance, state the conflict and choose the path that best protects the research objective.
