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
- Sem `OPENAI_API_KEY`, `OPENROUTER_API_KEY`, `ANTHROPIC_API_KEY` ou `NOUS_API_KEY` no env-file Fuinha.
- Telegram configurado por env-file root-only.
- Composio disponivel por env-file root-only.

## Pendencia critica

Codex OAuth ainda nao foi autenticado. O arquivo esperado e `/opt/eleve-hermes-fuinha/home/auth.json`. A autenticacao deve ser feita de modo interativo/controlado e nao pode ser substituida por fallback invisivel de chave de API.
