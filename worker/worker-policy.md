# Worker Policy

## Startup

At startup, a worker should:

1. Clone or update this configuration repository.
2. Read `agents/manifest.json`.
3. Select matching agents from issue text, PR comments, labels, changed files, and requested checks.
4. Attach selected agent prompts to the coding prompt.
5. Attach MCP policy metadata when tool access is relevant.
6. For issue-stage commands, use the matching stage agent and write a GitHub issue artifact before the next stage starts.

## Selection Rules

- Use no more than three specialist agents for one task unless the issue is explicitly cross-platform.
- Use `research-agent`, `analyst-agent`, `risk-agent`, `architect-agent`, and `planner-agent` in that order for the full PDLC flow.
- Always include `review-agent` for `/fix-review`.
- Include language agents only when the task touches that language or platform.
- Include `security-agent` for auth, secrets, permissions, MCP, dependency, or supply-chain changes.
- If `risk-agent` returns `human-dev-required`, coding workers should not autonomously implement code changes.

## Output Contract

The worker should ask Claude Code to include:

- selected agents,
- files changed,
- verification commands,
- risks or skipped checks.

Business-facing summaries should be Polish. Agent prompt instructions should remain English.
