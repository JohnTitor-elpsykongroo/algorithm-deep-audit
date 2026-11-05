# Algorithm Deep Audit

**English** | [简体中文](README.zh-CN.md)

A Codex Skill for research-grade analysis of existing algorithm projects. Trace what the code actually does, reconstruct its mathematical model, challenge the current interpretation, and compare competing approaches through falsifiable experiments.

## When to use it

- Understand an algorithm across configuration, preprocessing, solvers, postprocessing, and failure paths.
- Check whether an implementation matches its paper and documented assumptions.
- Investigate numerical behavior, stopping conditions, dynamic dispatch, and test coverage gaps.
- Assess alternative technical directions before investing in implementation or training.

This repository contains instructions and reference templates for Codex. It is not an executable analyzer or a training framework.

## Get started

Clone the repository into a directory of your choice:

```sh
git clone https://github.com/JohnTitor-elpsykongroo/algorithm-deep-audit.git
```

The skill entry point is [SKILL.md](SKILL.md). Keep `agents/` and `references/` alongside it. In Codex, provide the local path to `SKILL.md` and the repository you want to analyze. If the skill is available in your session's skill picker, invoke it with `$algorithm-deep-audit`.

For example, after cloning into `D:\WorkSpace\skills`:

```text
Use the skill at D:\WorkSpace\skills\algorithm-deep-audit\SKILL.md
to analyze D:\WorkSpace\my-algorithm.

Treat `python main.py --config configs/eval.yaml` as the representative
invocation, but do not execute it. Focus on the effective configuration,
objective function, solver updates, numerical handling, and fallback paths.
Compare competing approaches when network access is permitted.
Keep the audit read-only; do not run tests or start training.
```

Replace the example paths and command with your project's actual entry point. Providing the relevant paper, configuration, and research question helps define the scope. Cloning into an arbitrary directory alone does not guarantee automatic skill discovery.

## Audit workflow

Each stage has a coverage and evidence checkpoint. Finding the core entry point is only the beginning.

| Stage | Work | Checkpoint |
| --- | --- | --- |
| G1 — Scope | Inventory the repository, version, dependencies, configurations, tests, papers, and entry points. | Establish research boundaries, a representative invocation, and a coverage plan. |
| G2 — Execution paths | Follow preprocessing, data structures, algorithm dispatch, optimization, postprocessing, and exceptions. | Connect inputs to outputs and account for consequential branches and external boundaries. |
| G3 — Mathematics | Reconstruct objectives or rules, constraints, updates, parameters, stopping criteria, and numerical treatment. | Map the mathematical account to code evidence and expose paper–implementation differences. |
| G4 — Falsification | Seek evidence against important claims; inspect configuration overrides, hidden alternatives, and test assertions. | Revise disproved claims and record unresolved conflicts and coverage gaps. |
| G5 — Alternatives | Research competing papers and open-source algorithms, including different mechanisms and meaningful simple baselines. | Compare assumptions and applicability; propose a minimal experiment for each worthwhile candidate. |

Reading is selective and driven by research questions and consequential paths. Coverage is not measured by the number of files opened. Core unresolved paths or model conflicts require a partial report rather than an unsupported claim of completeness.

## Evidence standards

The skill separates:

- **Source facts:** file paths, functions or symbols, line numbers, and applicable configurations.
- **Paper claims:** original sources, versions, pages, sections, or equations.
- **Documentation claims:** README text and comments, kept distinct from implementation evidence.
- **Inferences and derivations:** explicit assumptions, supporting evidence, and falsification conditions.
- **Runtime observations:** commands, environments, data, and result provenance; static analysis is not presented as an executed test.

It maintains a coverage table, an evidence ledger, and an unknowns/falsification list throughout the audit.

## Deliverables

The final report includes scope and stage coverage, a source evidence table, execution flow, mathematical analysis, paper–implementation differences, falsification findings, test gaps, unresolved questions, candidate technical directions, and experiment recommendations.

Each worthwhile alternative receives a minimal experiment plan covering its hypothesis, intervention, baseline, data, metrics, fair resource budget, expected risks, and rejection criteria. An experiment proposal is not an experimental result.

## Execution boundaries

**Read-only by default.** The skill does not authorize code, configuration, data, or environment changes; dependency installation; repository entry-point or test execution; or training. Execution requires explicit authorization within the agreed scope.

External research proceeds when tools and network permissions allow it. When offline, the audit continues locally and labels unverified candidates and research limitations. Private source code, data, and sensitive configurations are not uploaded for research.

Reports are delivered in the conversation by default. If saving is requested, use the specified destination or an audit directory outside the source tree being reviewed.

## Repository contents

| File | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | Core workflow, evidence rules, permissions, and completion criteria. |
| [agents/openai.yaml](agents/openai.yaml) | Skill UI metadata. |
| [references/research-and-experiments.md](references/research-and-experiments.md) | Competitive research guidance and minimal experiment cards. |
| [references/report-template.md](references/report-template.md) | Report structure and final checks. |

The skill instructions and reference templates are currently written in Chinese. This English README describes their scope and usage.
