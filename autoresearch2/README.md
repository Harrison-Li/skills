# Generalized Autoresearch

The agent gathers requirements, prepares experiments, asks for review, and runs within the approved limits. Explicit requests for direct autonomous execution skip review after assumptions are recorded.

## Use

Ask your agent to read `skills/autoresearch/SKILL.md` while working in the target project.

For installation, copy `skills/autoresearch` to `~/.agents/skills/autoresearch` or `<project>/.agents/skills/autoresearch`, then invoke `$autoresearch`. Compare any existing installation before replacing it. See [Codex skill locations](https://learn.chatgpt.com/docs/build-skills).

## Output

```text
Nov_12_exp1/
    program.md   # plan for review
    summary.md   # brief progress note and final report
```

New studies use the next available number for the local date. Resumed studies keep their folder. Summaries are titled `Autoresearch — <study name>`. Detailed event logs and trial folders are optional.

Karpathy's original docs are in `skills/autoresearch/references/`, with source attribution. Load them only when needed; routine runs use the short skill and templates.

Updated from https://github.com/karpathy/autoresearch/tree/master
