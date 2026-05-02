# Feature: Agent Configuration Repository

## Cel

Repozytorium `AgentWorkflowPDLC-AgentConfig` przechowuje konfigurację agentów używaną przez workerów PDLC. Dzięki temu prompty bazowe, reguły wyboru agentów, notatki skillowe oraz szablony MCP są wersjonowane niezależnie od repozytoriów aplikacyjnych.

## Zakres

- `agents/manifest.json` opisuje dostępnych agentów i reguły ich wyboru.
- `agents/*/agent.md` zawiera bazowe prompty specjalistów.
- `worker/worker-policy.md` definiuje kontrakt startowy workera.
- `mcp/mcp.config.example.json` pokazuje format bezpiecznej konfiguracji MCP bez sekretów.

## Kontrakt Dla Workera

Worker na starcie pobiera repo konfiguracji, czyta manifest i dołącza pasujące prompty do zadania przekazywanego do Claude Code. Wybór agentów może być wykonany heurystycznie przez worker albo przekazany Claude Code jako część instrukcji.

Domyślne zmienne:

```text
PDLC_AGENT_CONFIG_REPO=LordIllidan/AgentWorkflowPDLC-AgentConfig
PDLC_AGENT_CONFIG_REF=main
```

## Zasady Językowe

Instrukcje agentów są po angielsku, żeby ograniczyć koszt tokenów i zachować precyzję techniczną. Wejście i wyjście biznesowe może pozostać po polsku.
