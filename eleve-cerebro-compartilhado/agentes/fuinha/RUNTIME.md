# Runtime Fuinha

## Decisao de fonte

- Runtime: Hermes Agent upstream.
- Repo: `https://github.com/NousResearch/hermes-agent.git`
- Tag pinada: `v2026.6.19`
- Commit pinado: `2bd1977d8fad185c9b4be47884f7e87f1add0ce3`
- Instalacao: `uv sync --extra all --locked`, sem rodar installer interativo upstream.

## Isolamento

- Base: `/opt/eleve-hermes-fuinha`
- Usuario runtime: `fuinha`
- Home Hermes: `/opt/eleve-hermes-fuinha/home`
- Codigo fonte: `/opt/eleve-hermes-fuinha/src`
- Venv: `/opt/eleve-hermes-fuinha/venv`
- Env-file sensivel: `/etc/fuinha-hermes/fuinha.env`, root-only
- Service: `hermes-fuinha.service`, desabilitado ate ativacao

## Configuracao atual

- Provider: OpenAI Codex
- Modelo default: `gpt-5.5`
- Codex OAuth: autenticado em `/opt/eleve-hermes-fuinha/home/auth.json`, dono `fuinha`, modo `600`.
- Sem `OPENAI_API_KEY`, `OPENROUTER_API_KEY`, `ANTHROPIC_API_KEY` ou `NOUS_API_KEY` no env-file Fuinha.
- Composio disponivel por env-file root-only.
- Telegram removido do env-file ativo por blocker de token compartilhado.

## Pendencia critica

Criar ou registrar no cofre um bot/token Telegram dedicado da Fuinha. O token testado tinha hash identico ao token usado pelo OpenClaw Eleve, gerando conflito de polling e violando isolamento de canal.
