# Worker Policy

## Startup

At startup, a worker should:

1. Clone or update this configuration repository.
2. Read `agents/manifest.json`.
3. Select matching agents from issue text, PR comments, labels, changed files, and requested checks.
4. Attach selected agent prompts to the coding prompt.
5. Attach MCP policy metadata when tool access is relevant.

## Selection Rules

- Use no more than three specialist agents for one task unless the issue is explicitly cross-platform.
- Always include `review-agent` for `/fix-review`.
- Include language agents only when the task touches that language or platform.
- Include `security-agent` for auth, secrets, permissions, MCP, dependency, or supply-chain changes.

## Output Contract

The worker should ask Claude Code to include:

- selected agents,
- files changed,
- verification commands,
- risks or skipped checks.

Business-facing summaries should be Polish. Agent prompt instructions should remain English.
