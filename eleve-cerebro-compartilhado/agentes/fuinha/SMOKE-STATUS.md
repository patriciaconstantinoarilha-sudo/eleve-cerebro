# Smoke Status Fuinha

Status geral: runtime aprovado em CLI/modelo, ativacao Telegram bloqueada por credencial compartilhada.

| Smoke | Status | Evidencia |
|---|---|---|
| Isolamento runtime | pass | Runtime separado em `/opt/eleve-hermes-fuinha`, usuario `fuinha`, service `hermes-fuinha.service` |
| Hermes CLI | pass | Hermes Agent v0.17.0, release 2026.6.19, CLI responde `version` e `--help` |
| Runtime pin | pass | Upstream `NousResearch/hermes-agent`, tag `v2026.6.19`, commit `2bd1977d8fad185c9b4be47884f7e87f1add0ce3` |
| Brain GitHub | pass | Area `eleve-cerebro-compartilhado/agentes/fuinha/` criada e enviada para `main` |
| Codex-first | pass | OpenAI Codex logado em `/opt/eleve-hermes-fuinha/home/auth.json`, dono `fuinha`, modo `600`, sem fallback de chave de API |
| Modelo | pass | One-shot sintetico respondeu como Fuinha em smoke tecnico |
| Recusa conteudo proibido | pass | One-shot recusou acesso a curso pago/area logada sem autorizacao |
| Composio | pass parcial | Credencial presente em env-file root-only; integracao MCP/ferramenta ainda depende de selecao tecnica |
| Telegram getMe | pass parcial | Credencial anterior retornou `getMe` ok, sem envio real |
| Telegram gateway | blocked | Hash do token era identico ao token do OpenClaw Eleve; polling conflitou. Token removido do env-file ativo da Fuinha ate existir bot proprio |
| Service lifecycle | pass com bloqueio Telegram | Unit valida, desabilitada e parada; nao deve iniciar com token compartilhado |
| OpenClaw Eleve | pass | `healthz=200`, `readyz=200` apos testes |
| Scraping | blocked | Usar apenas smoke sintetico/autorizado ate Patrick definir fonte |

## Blocker P0

O item de Telegram usado para Fuinha apontava para o mesmo bot/token ja usado pelo OpenClaw Eleve. Isso viola a decisao de canal proprio e causa conflito de polling. A Fuinha precisa de um bot/token Telegram proprio antes da ativacao do gateway.

## Estado operacional

- `hermes-fuinha.service` esta desabilitado e parado.
- O env-file ativo nao contem mais `TELEGRAM_BOT_TOKEN` nem `TELEGRAM_ALLOWED_USERS` para evitar uso acidental do bot compartilhado.
- Nao houve envio real de mensagem ao Patrick.
- Nao salvar transcricao bruta real ate o Patrick definir politica de retencao.
- Nao usar fontes logadas, pagas, protegidas ou cursos sem autorizacao explicita.
