# Record Templates

长期记录用于项目记忆；`handoff.md` 用于线程切换。记录要短、准、可追溯，不写未经证据支持的结论。

## Directory

```text
research/
  <project-name>/
    project-brief.md
    physics-core.md
    decisions.md
    worklog.md
    reviews.md
    handoff.md
```

## project-brief.md

```markdown
# Project Brief

## project_name

## research_goal

## physics_core

## scope

## success_criteria

## key_artifacts

## current_status
```

## physics-core.md

```markdown
# Physics Core

## physical_problem

## core_assumptions

## physical_constraints

## observables_and_variables

## invalid_shortcuts

## open_physics_questions
```

## decisions.md

```markdown
# Decisions

## YYYY-MM-DD - <decision title>

- decision:
- reason:
- evidence:
- alternatives_rejected:
- impact:
- revisit_condition:
```

## worklog.md

```markdown
# Worklog

## YYYY-MM-DD - <session title>

- level:
- goal:
- context:
- actions:
- results:
- risks:
- next_actions:
- files_touched:
```

## reviews.md

```markdown
# Reviews

## YYYY-MM-DD - <review title>

- reviewed_artifact:
- review_type:
- alignment_check:
- confirmed_consistencies:
- risks:
- required_corrections:
- verdict:
```

## handoff.md

```markdown
# Handoff

- last_updated:
- current_goal:
- physics_core:
- completed_work:
- open_tasks:
- known_risks:
- next_actions:
- must_read_files:
- current_blockers:
```

## Handoff Rules

- 控制在下一线程可快速读取的长度。
- 只写当前推进所必需的信息。
- 必须列出 `must_read_files`，避免新线程盲读全部历史。
- 对不确定内容标注为风险或待验证，不写成结论。