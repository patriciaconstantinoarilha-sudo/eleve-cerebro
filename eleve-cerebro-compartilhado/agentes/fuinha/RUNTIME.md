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
- Telegram dedicado configurado por referencia de cofre: `telegram bot token - fuinha`, vault `Eleve Operacao`.

## Systemd

- Unit: `/etc/systemd/system/hermes-fuinha.service`
- Estado pos-smoke: `disabled` e `inactive`.
- `TimeoutStopSec=240`.
- `KillSignal=SIGINT` para parada limpa do Hermes gateway.
- `NoNewPrivileges=true`, `ProtectSystem=full`, `ProtectHome=true`, `ReadWritePaths=/opt/eleve-hermes-fuinha /tmp`, `UMask=0077`.

## Pendencias de handoff

- Patrick deve definir primeira fonte autorizada de pesquisa/scraping.
- Patrick deve definir politica de armazenamento e retencao para transcricao bruta real.
- Recorrencia automatica depende de frequencia, fontes, limites e revisor aprovados.
- Mensagem real no Telegram depende de aprovacao explicita de ativacao.
