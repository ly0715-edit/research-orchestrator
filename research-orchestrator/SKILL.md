---
name: research-orchestrator
description: Use when coordinating long-running research projects, physics-to-algorithm work, radar meteorology tasks, multi-agent research execution, context handoff, project memory, or rigorous review of scientific implementation.
---

# Research Orchestrator

## Overview

`research-orchestrator` 是面向长期科研项目的主线程调度 Skill。主线程负责目标、分级、派发、整合和记录；子 Agent 只处理明确边界内的专长任务。

核心原则：节约上下文、保护物理主旨、执行与审核分离、长期记录可交接。

## When to Use

在这些场景使用：

- 长期科研项目、博士课题、横向项目、多轮实验或多线程协作。
- 雷达气象学、物理主导、算法实现、实验验证、论文结论相关任务。
- 需要把物理目标转译为算法、代码、实验、文档执行计划。
- 用户要求“不要跑偏”“严格审核”“长期记录”“交接”“按科研工作流推进”。
- 当前会话上下文较长，需要压缩任务输入并让子 Agent 接收最小必要材料。

不用于普通闲聊、一次性简短问答、无需项目记忆的小问题。

## Level Selection

主线程先判断任务等级；用户显式指定时，以用户指定为准。

| Level | Default Trigger | Required Flow |
|---|---|---|
| `quick` | 文件查找、局部解释、小修、单条命令、非关键问题 | Understand -> Execute -> Brief Report |
| `standard` | 普通算法实现、实验脚本、数据处理、模块修改、阶段分析 | Understand -> Plan -> Execute -> Basic Review -> Update Records |
| `critical` | 物理假设、核心算法、论文结论、博士主线、重要实验、方向调整 | Understand -> Physics Translation -> Execution Planning -> Execute -> Independent Review -> Record -> Synthesis |

升级规则：涉及物理主旨、关键假设、核心算法、论文/项目结论、长期记录或跨线程交接时，默认升级到 `critical`。

## Main Thread Duties

| Duty | Requirement |
|---|---|
| `Scope Control` | 明确目标、任务等级、成功标准和边界。 |
| `Context Packing` | 只向子 Agent 提供必要目标、文件、约束和输出格式。 |
| `Task Dispatch` | 明确每个子 Agent 的角色、输入、禁止事项和产物。 |
| `Synthesis` | 整合子 Agent 输出，解决冲突，决定下一步。 |
| `Memory Update` | 对 `standard` 和 `critical` 任务维护长期日志与交接包。 |

主线程不得把最终项目决策交给子 Agent。子 Agent 提供证据、风险和建议，主线程负责判断。

## Skill Coordination

`research-orchestrator` 是调度层，不替代专门 Skill。主线程和子 Agent 在坚持本 Skill 的等级、记录和物理审核原则下，应按任务需要调用更合适的 Skill。

| Situation | Preferred Skill Type |
|---|---|
| 实现功能、修复 bug、重构 | TDD、debugging、code review、implementation planning |
| 代码审查、发布前检查 | requesting-code-review、pre-publish-review、review workflow |
| 文档、表格、演示文稿 | documents、spreadsheets、presentations |
| GitHub issue/PR 分析 | github triage 或 PR workflow |
| 新 Skill 创建或修改 | skill-creator、writing-skills |

规则：先满足用户显式指令和当前 Skill 的科研调度原则；再调用任务专用 Skill。若两者冲突，主线程必须说明冲突并选择更符合用户目标的路径。

## Sub-Agent Use

完整角色卡见 `references/agent-cards.md`。按需读取，不要在每次任务中全部展开。

| Agent | Use When |
|---|---|
| `Physics Translator` | `critical` 必用；把物理目的转成算法、变量、约束和风险。 |
| `Execution Planner` | `standard`/`critical` 常用；把目标拆成文件级、实验级、验证级任务。 |
| `Implementation Agent` | 有明确执行范围时；负责代码、实验、文档或数据处理。 |
| `Physics Reviewer` | `critical` 必用；独立审查物理一致性和假设漂移。 |
| `Research Scribe` | `standard`/`critical` 必用；维护长期记录与交接摘要。 |

## Records

长期项目建议使用：

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

模板见 `references/record-templates.md`。

## Dispatch Patterns

三档任务的派发模式见 `references/dispatch-patterns.md`。原则：先最小化上下文，再派发；先审查物理转译，再执行关键实现；执行与审核尽量分离。

## Completion Rules

结束一轮工作前检查：

- `quick`: 已说明做了什么、结果是什么、是否有风险。
- `standard`: 已更新 `worklog.md` 和 `handoff.md`，或说明为什么当前没有项目记录目录。
- `critical`: 已完成物理一致性审核，记录风险、决策、下一步和必读文件。

最终汇报必须包含：当前结论、已完成事项、主要风险、下一步建议。