# Record Templates

Records preserve continuity. Keep them concise, evidence-based, and usable by a future thread.

## Directory

```text
research/<project-name>/
  project-brief.md
  domain-core.md
  decisions.md
  worklog.md
  reviews.md
  handoff.md
```

Create records only when the user approves or the project already has a record directory. Do not invent project facts to fill templates.

## project-brief.md

```markdown
# Project Brief

## project_name

## research_goal

## scientific_claims_or_outputs

## scope

## success_criteria

## key_artifacts

## current_status
```

## domain-core.md

```markdown
# Domain Core

## scientific_problem
## core_assumptions

## observables_and_variables

## domain_constraints

## valid_algorithmic_mappings

## invalid_shortcuts

## open_domain_questions
```

## decisions.md

```markdown
# Decisions

## YYYY-MM-DD - <decision title>

- decision:
- level:
- reason:
- evidence:
- alternatives_rejected:
- scientific_impact:
- reproducibility_impact:
- revisit_condition:
```

## worklog.md

```markdown
# Worklog

## YYYY-MM-DD - <session title>

- level:
- goal:
- scientific_framing:
- actions:
- files_or_data_touched:
- commands_or_experiments:
- results:
- verification:
- risks:
- next_actions:
```
## reviews.md

```markdown
# Reviews

## YYYY-MM-DD - <review title>

- reviewed_artifact:
- review_type:
- gates_checked:
- alignment_check:
- confirmed_consistencies:
- risks:
- evidence_gaps:
- required_corrections:
- verdict:
```

## handoff.md

```markdown
# Handoff

- last_updated:
- current_goal:
- domain_core_summary:
- current_hypothesis_or_design:
- completed_work:
- open_tasks:
- known_risks:
- current_blockers:
- next_actions:
- must_read_files:
- record_files:
```

## Handoff Rules

- Keep handoff short enough to read at the start of a new thread.
- Include only information needed to continue work safely.
- List `must_read_files`; do not force the next thread to scan everything.
- Mark uncertain content as risk or pending verification.
- For critical work, include review verdict and missing evidence if any.
