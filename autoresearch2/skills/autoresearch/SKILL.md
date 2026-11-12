---
name: autoresearch
description: "Set up and run improvement experiments for any code project. Use for autoresearch or iterative optimization: gather goals and editable scope, prepare a plan for review, then test and summarize."
---

# Autoresearch

Work in the user's target project. Load only relevant code and the template needed for the current step. No model, language, hardware, or metric is assumed.

## 1. Establish requirements

Inspect project instructions, relevant code, evaluation tools, and local changes. Ask only what is missing:

- What should improve, and what behavior must remain intact?
- Which files may change? Clarify protected code, new files, and dependencies.
- Where should experiments run, with what overall budget and per-run timeout?

Derive hypotheses and evaluation commands yourself. Propose a metric or small evaluator if needed. For subjective goals, use an agreed rubric or human comparison.

## 2. Prepare files

Create `Mon_DD_expN`, such as `Nov_12_exp1`, in the project or chosen output parent. Use the user's local date, English month abbreviation, and two-digit day. N is one more than the highest matching sibling suffix, or 1 if none exist. Never overwrite; retry on collision. N identifies a study, not each trial. Resume in the same folder, even on another day.

Create two research documents:

- `program.md` from [the plan template](assets/program.template.md): objective, scope, evaluation, budget, and hypotheses.
- `summary.md` from [the report template](assets/summary.template.md): title `Autoresearch — <study name>`, full date/timezone, and status. Initially state that experiments have not run.

Use the summary for brief current-state notes and the final report. No separate event logs, trial ledger, or mandatory trial folders are needed. Keep command output only when useful for debugging or supporting results; read relevant excerpts.

## 3. Review before execution

Finish and link the files, mark them `awaiting review`, and ask the user to check them. Wait for explicit approval before any baseline or experiment. Setup-only requests stop here. Approval of the same plan persists; do not ask after every trial.

**Exception:** An explicit request to run directly without gathering requirements or waiting for review delegates missing choices. Record a defensible goal, narrow scope, finite budget, and the user's instruction, then proceed. A generic "use autoresearch" does not skip review. Material changes to approved requirements need renewed review unless already delegated.

## 4. Experiment

1. Preserve starting code and local changes for rollback. Measure the unchanged baseline before modifying the implementation.
2. Test one coherent hypothesis within scope. Run correctness checks and the fixed evaluation. Protect the evaluator, inputs, and acceptance criteria, including evaluation code inside editable files. Changed comparison conditions require a new baseline.
3. Compare valid results with the current best using the agreed metric, direction, threshold, and checks. Missing or non-finite scores are failures. Confirm noisy gains with comparable repetitions; keep holdout data separate where applicable.
4. Retain verified improvements; otherwise undo only the experiment's edits. Preserve user changes and identify the best candidate by revision, patch, or saved files.
5. Count preparation, baseline, retries, repetitions, and confirmation against their agreed limits. Stop on budget exhaustion, user interruption, the target/failure limit, or a blocker. Do not expand scope or resources silently.

## 5. Report or resume

Summarize baseline versus best, retained changes, important failed ideas, checks, budget used, limitations, stop reason, and reproduction command. Report observed results; label simulations clearly.

Keep a short current-state note: best candidate, remaining budget, pending work, and active process/job ID when needed. On resume, read the plan and summary, check authorization and running work, and continue within the remaining budget. Awaiting review still means no execution.

## Optional background

For questions about Karpathy's original workflow, consult [source notes](references/SOURCE.md) and only the relevant upstream document. These references are optional background; this skill's scope, review, budget, and reporting rules govern execution.
