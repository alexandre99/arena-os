# Napkin Runbook

## Curation Rules
- Re-prioritize on every read.
- Keep recurring, high-value notes only.
- Max 10 items per category.
- Each item includes date + "Do instead".

## Execution & Validation (Highest Priority)
1. **[2026-06-27] Prefix shell commands with `rtk`**
   Do instead: run repo shell commands as `rtk <cmd>` to follow `RTK.md` and keep output token-efficient.

2. **[2026-06-27] Prefer fast code search**
   Do instead: use `rg` for content search and `rg --files` for file discovery before slower scans.

3. **[2026-06-27] Create nested `.codex` dirs with escalation**
   Do instead: use an escalated `mkdir -p` for new subdirectories under `.codex` before patching files into them.
