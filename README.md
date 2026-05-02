# AgentWorkflowPDLC AgentConfig

Central configuration repository for AgentWorkflowPDLC AI workers.

This repository stores reusable agent definitions, base prompts, skill notes, MCP templates, and worker policies. Product repositories can keep their workflow logic small and pull this configuration at runtime.

## Purpose

- Keep agent prompts versioned outside product repositories.
- Let local Claude Code workers discover available specialist agents.
- Keep MCP and tool policy templates in one audited place.
- Allow multiple repositories to reuse the same PDLC agent standards.

## Structure

```text
agents/
  manifest.json
  angular/agent.md
  java/agent.md
  dotnet/agent.md
  review/agent.md
  security/agent.md
skills/
  README.md
mcp/
  mcp.config.example.json
worker/
  worker-policy.md
docs/
  agent-config-repo.md
```

## Runtime Contract

Workers should clone this repository at startup, read `agents/manifest.json`, and attach matching agent prompts to the Claude Code task prompt.

Default usage:

```text
PDLC_AGENT_CONFIG_REPO=LordIllidan/AgentWorkflowPDLC-AgentConfig
PDLC_AGENT_CONFIG_REF=main
```

Business input and final business-facing output can be Polish. Agent instructions, technical metadata, and internal reasoning instructions should stay in English.
