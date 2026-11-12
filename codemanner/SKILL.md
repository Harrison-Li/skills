---
name: code-guidelines
description: Apply the user's concise Python style when writing, reviewing, or refactoring code.
---

# Code Guidelines

- Write concise, readable Python with standard terms and familiar abbreviations (`emb`, `cond`, `batch_idx`, `z_t`, `pred_z_1`). Preserve parameter and return type annotations.
- Use one canonical name per function, class, or variable; remove compatibility aliases and update callers.
- Keep structure simple: functions for linear, stateless work; cohesive classes for shared state. Avoid fragmented helpers and speculative abstractions.
- Remove unnecessary casts (`int`, `float`, `bool`); keep conversions needed for tensor precision, scalar extraction, parsing, or serialization.
- Remove redundant guards and shape/type/device checks when callers or frameworks guarantee the contract. Keep checks against silent data corruption, incorrect atom correspondence, incompatible checkpoint loading, nonfinite training, and accidental file overwrites.
- Trace dependencies before deleting stale code, obsolete model pipelines, and their unused configuration and entry points. Ask when usage or removal scope is uncertain.
- Integrate proven experiments into the main implementation; remove duplicate implementations, experiment-specific imports, and hard-coded environment paths.
- Keep comments and docstrings short: explain purpose, tensor conventions, and non-obvious assumptions.
- Preserve valid-input behavior during cleanup. Use focused tests and numerical parity checks for model changes.
- Keep documentation and tests local and Git-ignored; never commit or push `docs/` or `tests/`.
- Make authorized changes directly within scope. Ask only when ambiguity materially affects correctness or scope.
