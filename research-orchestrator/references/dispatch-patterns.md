# Dispatch Patterns

## Level: quick

Use for local, low-risk tasks.

Main thread pattern:

1. Restate the immediate goal.
2. Read or inspect the minimum necessary files/output.
3. Execute directly without sub-agent unless parallel search is useful.
4. Report result, risk, and any optional follow-up.

Required records: none, unless the result changes project memory.

## Level: standard

Use for ordinary implementation, analysis, experiment scripts, data processing, or module-level work.

Main thread pattern:

1. Define goal, scope, success criteria.
2. Optionally dispatch `Execution Planner` if the work spans multiple files or experiments.
3. Dispatch or perform implementation.
4. Run verification where feasible.
5. Do a basic review against the stated objective.
6. Update `worklog.md` and `handoff.md` when a project record directory exists.

Recommended context packet:

```text
Task level: standard
Objective:
Known constraints:
Relevant files:
Allowed write scope:
Expected output:
Verification required:
Relevant skills to use:
```

## Level: critical

Use for physics assumptions, core algorithms, thesis direction, paper conclusions, important experiments, or work where drifting from the physical meaning would be costly.

Main thread pattern:

1. Define research objective and success criteria.
2. Read `handoff.md`, `physics-core.md`, and relevant recent records if available.
3. Dispatch `Physics Translator` with minimal source material.
4. Convert translation into an implementation plan via `Execution Planner`.
5. Execute via one or more bounded `Implementation Agent` tasks, or locally when delegation is not useful.
6. Dispatch `Physics Reviewer` independently with the objective, physics core, plan/result, and evidence.
7. Resolve conflicts and decide corrections.
8. Use `Research Scribe` or update records directly.
9. Report conclusion, risks, corrections, and next actions.

Recommended context packet:

```text
Task level: critical
Research objective:
Physics core:
Current hypothesis:
Relevant evidence/files:
Out of scope:
Required output schema:
Relevant skills to use:
Decision owner: main thread
```

## Dispatch Hygiene

- 子 Agent 输入越短越好，但必须包含目标、边界、证据、输出格式，以及必要时应使用的相关 Skill。
- 不把完整历史倾倒给子 Agent；用 `handoff.md` 和必要文件代替。
- 执行 Agent 不负责物理最终判断；审核 Agent 不负责实现。
- 当 Agent 输出冲突时，主线程必须显式列出冲突点和采用理由。
- 重要任务结束前必须有可交接的下一步动作。