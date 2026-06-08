# Research Orchestrator

**Research Orchestrator** is a Codex skill for evidence-first scientific workflows. It helps AI agents coordinate complex research tasks with explicit scientific framing, bounded execution, independent review, and reproducible handoff records.

It is designed for work where a casual answer is not enough: experiments, data pipelines, model evaluation, scientific code changes, result interpretation, and long-running projects where assumptions and evidence must remain traceable.

## Why It Matters

AI agents are useful in research, but scientific work has failure modes that ordinary coding workflows do not fully protect against:

- results are summarized before the supporting evidence is checked;
- code changes alter a scientific definition without anyone noticing;
- experiments are repeated without a record of assumptions, filters, or acceptance criteria;
- figures, metrics, logs, and written claims drift apart;
- long-running projects lose context across sessions;
- multiple agents contribute analysis, but no one owns the final scientific judgment.

Research Orchestrator provides a lightweight governance layer for these situations. It does not replace domain expertise; it makes the agent more disciplined about scope, evidence, review, and continuity.

## What The Skill Does

Research Orchestrator guides an AI agent through six core behaviors:

1. **Select the right governance level**
   - `quick`: low-risk checks and small local tasks.
   - `standard`: ordinary experiments, data processing, summaries, or module edits.
   - `critical`: assumptions, core algorithms, validation logic, paper-level conclusions, or reproducibility-critical changes.

2. **Frame the scientific objective**
   - Define the research question, claim at risk, observables, assumptions, available evidence, and acceptance criteria before execution.

3. **Separate evidence from inference**
   - Keep observations, assumptions, inferences, decisions, and unresolved risks distinct.

4. **Coordinate bounded sub-agent work**
   - Delegate planning, implementation, review, evidence auditing, or record synthesis without giving away final judgment.

5. **Apply review gates before conclusions change**
   - Check domain consistency, evidence sufficiency, reproducibility, implementation integrity, and handoff completeness.

6. **Preserve project memory**
   - Encourage concise records for decisions, worklogs, reviews, and future handoff.

## Who Should Use It

Use this skill if you use AI agents for scientific or evidence-heavy work, including:

- computational experiments;
- data analysis pipelines;
- model evaluation and comparison;
- scientific or analytical code maintenance;
- reproducibility-sensitive result interpretation;
- paper, report, thesis, or technical decision support;
- multi-session projects where context loss is costly;
- workflows where logs, figures, metrics, datasets, and written claims must agree.

It is intentionally domain-general. It can support physical science, life science, environmental analysis, engineering, social science computation, machine learning research, and other research workflows that depend on evidence discipline.

## Installation

Copy the skill directory into your Codex skills directory:

```text
research-orchestrator/
  SKILL.md
  agents/
  references/
```

Typical destinations include:

```text
~/.codex/skills/research-orchestrator
```

or another skills directory supported by your Codex environment.

If you use a skill installer that accepts GitHub paths, install from:

```text
https://github.com/ly0715-edit/research-orchestrator/tree/main/research-orchestrator
```

## Quick Start

Invoke the skill when a research task needs stronger governance:

```text
Use research-orchestrator to plan this experiment and define what evidence is needed before changing the conclusion.
```

```text
Use research-orchestrator to review whether this result is supported by the logs, figures, and method description.
```

```text
Use research-orchestrator to coordinate a multi-step analysis and produce a handoff record for the next session.
```

```text
Use research-orchestrator before modifying this scientific code, because the change may affect reproducibility.
```

## Workflow Levels

| Level | Use When | Expected Discipline |
|---|---|---|
| `quick` | Local inspection, simple explanation, low-risk command, small non-scientific edit | Direct work, concise result, uncertainty or risk note |
| `standard` | Ordinary experiment scripts, data processing, module edits, stage summaries, non-final analysis | Scope, plan, execute, verify, basic review, record update when records exist |
| `critical` | Scientific assumptions, core algorithms, validation logic, paper conclusions, direction changes, reproducibility-critical experiments | Domain translation, bounded execution, independent review, decision record, handoff |

The skill intentionally chooses the smallest level that protects research quality. It can escalate when new evidence shows higher risk.

## Repository Structure

```text
research-orchestrator/
  SKILL.md
  agents/
    openai.yaml
  references/
    agent-cards.md
    dispatch-patterns.md
    record-templates.md
    review-gates.md
```

- `SKILL.md` defines the trigger logic and core workflow.
- `agents/openai.yaml` provides Codex interface metadata.
- `references/agent-cards.md` describes optional sub-agent roles.
- `references/dispatch-patterns.md` defines level-specific workflows.
- `references/record-templates.md` provides lightweight research memory templates.
- `references/review-gates.md` defines acceptance gates for scientific claims.

## Research Records

For long-running projects, the skill recommends a concise record directory such as:

```text
research/<project-name>/
  project-brief.md
  domain-core.md
  decisions.md
  worklog.md
  reviews.md
  handoff.md
```

These records help future sessions recover what was done, why it was done, what evidence supports it, and what remains uncertain.

## What It Is Not

Research Orchestrator does not:

- replace domain expertise;
- guarantee that a scientific conclusion is correct;
- automatically validate data quality;
- run experiments by itself;
- remove the need for human review;
- impose heavy process on every small task;
- require users to disclose private project information.

It provides structure so that AI-assisted research work is easier to inspect, reproduce, and continue.

## Privacy And Safety

The skill is intentionally generic. It is not tied to any private project, institution, dataset, unpublished result, or specific research direction.

When using it in sensitive work, keep records as abstract as possible and include only the information needed for reproducibility and handoff.

## License

MIT License. See [LICENSE](LICENSE).
