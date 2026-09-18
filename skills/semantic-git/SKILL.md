---
name: semantic-git
description: Entity-level git analysis with sem CLI — structural diffs, impact analysis, blame. Use when asked for "blast radius", "impact analysis", "what functions changed", "semantic diff", or structural code change analysis beyond line-level diffs.
---

# Semantic Git (sem CLI)

Use the `sem` CLI for structural code change analysis:

- `sem diff` — entity-level diff (functions/classes changed, not line-level)
- `sem impact` — blast radius analysis (what depends on changed code)
- `sem context` — surrounding context for changes
- `sem blame` — entity-level blame (who last changed this function)
- `sem log` — entity-level git log
- `sem entities` — list all code entities in a file

Use `sem` when the question is structural. When complete patch review is required, supplement it with raw `git diff` and inspect any relevant untracked files separately; entity-level output does not replace that evidence. A standalone structural query does not require a raw diff automatically.

Check that `sem` is available before using it. If it is missing or fails, report structural analysis as unavailable. Continue with raw patch inspection when useful, but do not present it as completed entity-level analysis. Do not install `sem` or run `sem setup`/`sem unsetup` implicitly; they are not read-only analysis.
