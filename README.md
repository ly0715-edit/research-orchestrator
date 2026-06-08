# Research Orchestrator

Research Orchestrator is a Codex skill for managing complex scientific work with stronger discipline around scope, evidence, review, and handoff. It is designed for research tasks where a small undocumented change can alter a result, weaken a claim, or make later work difficult to reproduce.

This skill is not a domain-specific answer generator. It is a workflow and governance layer that helps an AI agent coordinate scientific reasoning, implementation, verification, review, and project memory.

## Why This Skill Exists

Scientific work often fails in ways that ordinary coding workflows do not fully catch:

- A result is reported before the supporting evidence is clear.
- A script is changed without recording which assumption changed.
- An experiment is repeated, but the exact decision path is lost.
- A figure, metric, or conclusion becomes disconnected from the method that produced it.
- A long-running project spans multiple conversations, and important context disappears.
- Multiple agents or tools contribute useful work, but no one owns the final scientific judgment.

Research Orchestrator addresses these problems by making the agent slow down at the right moments: define the research objective, separate evidence from inference, choose an appropriate risk level, delegate bounded work when useful, require review before conclusions change, and record decisions for future continuation.

## Who It Is For

This skill is useful for researchers, engineers, analysts, and students who use AI agents in scientific or evidence-heavy work, especially when tasks involve:

- computational experiments;
- data processing pipelines;
- model evaluation and comparison;
- scientific code maintenance;
- paper, report, or thesis result interpretation;
- reproducibility-sensitive analysis;
- multi-session project continuation;
- review of claims supported by logs, figures, metrics, or datasets.

It can be adapted to many fields, including physical sciences, environmental science, remote sensing, engineering, biomedical analysis, geoscience, climate research, social science computation, and other data-intensive research workflows.

## What It Does

Research Orchestrator provides a structured operating mode for AI-assisted research work.

### 1. Level Selection

The skill classifies tasks into three levels:

| Level | Typical Use | Governance |
|---|---|---|
| `quick` | Local inspection, simple explanation, low-risk edits | Direct work with a concise risk note |
| `standard` | Ordinary experiment scripts, data processing, summaries, module edits | Scope, plan, execute, verify, basic review, record update when applicable |
| `critical` | Changes to assumptions, core algorithms, experiment validity, or paper-level conclusions | Scientific framing, bounded execution, independent review, evidence gates, decision record, handoff |

This prevents lightweight tasks from becoming overmanaged while still protecting high-risk scientific work.

### 2. Scientific Framing

For non-trivial tasks, the skill asks the agent to clarify:

- What is the scientific objective?
- What claim or output is at risk?
- What observations, variables, metrics, or artifacts matter?
- What assumptions are known, uncertain, or unverified?
- What evidence is available?
- What would count as a successful result?

The goal is to keep implementation choices aligned with the scientific meaning of the work.

### 3. Evidence Discipline

The skill separates:

- observations;
- assumptions;
- inferences;
- decisions;
- unresolved risks.

This is especially important when a result is based on code output, logs, generated figures, model scores, data filters, thresholds, or manual interpretation.

### 4. Bounded Delegation

When a task is large enough, Research Orchestrator can coordinate specialized sub-agent roles, such as:

- Physics or domain translator;
- Execution planner;
- Implementation agent;
- Scientific reviewer;
- Evidence auditor;
- Research scribe.

The main thread remains responsible for judgment. Sub-agents provide bounded analysis, implementation, or review, but they do not silently change conclusions or project direction.

### 5. Review Gates

For critical work, the skill uses explicit acceptance gates:

- physical or domain consistency;
- evidence sufficiency;
- reproducibility;
- implementation integrity;
- handoff completeness.

A conclusion should not be treated as established unless the relevant evidence and consistency checks pass.

### 6. Research Records and Handoff

The skill encourages lightweight project records for long-running work, such as:

```text
research/<project-name>/
  project-brief.md
  physics-core.md
  decisions.md
  worklog.md
  reviews.md
  handoff.md
```

These records help future sessions understand what was done, why it was done, what evidence supports it, and what remains uncertain.

## What Problems It Helps Solve

Research Orchestrator is intended to reduce common failure modes in AI-assisted research:

- losing the reasoning behind an experimental choice;
- mixing speculation with verified evidence;
- changing code without preserving scientific meaning;
- accepting results without checking the data path;
- treating generated text as a conclusion rather than a draft claim;
- forgetting previous decisions across sessions;
- allowing implementation convenience to override research validity;
- relying on one agent's output without independent review.

## What It Does Not Do

This skill does not:

- replace domain expertise;
- guarantee that a scientific conclusion is correct;
- automatically run experiments or validate data quality;
- remove the need for human review;
- impose heavy process on every small task;
- provide private project knowledge by default.

It provides structure. The user and the main agent still own the scientific judgment.

## How To Use

Install or place the skill folder in the appropriate Codex skills directory, then invoke it when a research task needs stronger governance.

Example prompts:

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

- `SKILL.md` defines when the skill is triggered and the core operating principles.
- `agents/openai.yaml` provides interface metadata for Codex.
- `references/agent-cards.md` describes optional sub-agent roles.
- `references/dispatch-patterns.md` defines workflows for quick, standard, and critical tasks.
- `references/record-templates.md` provides reusable project memory templates.
- `references/review-gates.md` defines scientific acceptance checks.

## Recommended Use Cases

Use this skill when the task involves one or more of the following:

- a result that may later appear in a paper, report, thesis, or technical decision;
- a code change that affects scientific meaning or reproducibility;
- an experiment that needs clear assumptions and acceptance criteria;
- a multi-session project where context loss is costly;
- a need to compare evidence from code, data, figures, metrics, and written claims;
- a need for independent review before changing a conclusion.

For simple factual questions, one-off command checks, or low-risk formatting edits, a normal agent workflow is usually enough.

## Design Principles

Research Orchestrator follows a few simple principles:

- Scientific meaning comes before implementation convenience.
- Evidence should be visible before claims are accepted.
- Assumptions and unknowns should be named explicitly.
- Execution and review should be separated when conclusions may change.
- Long-running work needs records, not just chat history.
- The main thread owns final judgment.

## Privacy and Project Safety

The skill is intentionally generic. It does not require users to disclose private project names, datasets, unpublished results, institutional details, or personal research directions. Records should only include information the user chooses to preserve.

When used in sensitive projects, keep examples, prompts, and handoff notes abstract unless the project context is already intended to be shared.

## Summary

Research Orchestrator helps AI agents behave more like disciplined research collaborators: careful about assumptions, explicit about evidence, cautious with conclusions, and reliable across long-running scientific work.

It is most valuable when the cost of being casually wrong is high.
