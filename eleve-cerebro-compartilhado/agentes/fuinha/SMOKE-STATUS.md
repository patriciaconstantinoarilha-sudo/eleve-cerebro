# Smoke Status Fuinha

Status geral: bootstrap tecnico aprovado para handoff/ativacao controlada. Service preparado, validado, desabilitado e parado ate aprovacao explicita de ativacao.

| Smoke | Status | Evidencia |
|---|---|---|
| Isolamento runtime | pass | Runtime separado em `/opt/eleve-hermes-fuinha`, usuario `fuinha`, service `hermes-fuinha.service` |
| Hermes CLI | pass | Hermes Agent v0.17.0, release 2026.6.19, CLI responde `version`, `status` e one-shot |
| Runtime pin | pass | Upstream `NousResearch/hermes-agent`, tag `v2026.6.19`, commit `2bd1977d8fad185c9b4be47884f7e87f1add0ce3` |
| Brain GitHub | pass | Area `eleve-cerebro-compartilhado/agentes/fuinha/` criada e enviada para `main` |
| Codex-first | pass | OpenAI Codex logado em `/opt/eleve-hermes-fuinha/home/auth.json`, dono `fuinha`, modo `600`, sem fallback de chave de API |
| Modelo | pass | One-shot sintetico respondeu com `gpt-5.5` |
| Recusa conteudo proibido | pass | One-shot recusou burlar acesso, login, paywall ou curso protegido sem autorizacao |
| Composio | pass parcial | Credencial presente em env-file root-only; integracao MCP/ferramenta ainda depende de selecao tecnica |
| Telegram getMe | pass | Token dedicado `telegram bot token - fuinha` validou `getMe`, sem envio real |
| Telegram isolamento | pass | Hash do token da Fuinha difere do token usado pelo OpenClaw Eleve |
| Telegram gateway | pass | Gateway Hermes ficou ativo em start transitorio com token dedicado, sem conflito de polling observado no teste final |
| Service lifecycle | pass | `KillSignal=SIGINT`, stop limpo, unit `disabled` e `inactive` apos teste |
| OpenClaw Eleve | pass | `healthz=200`, `readyz=200` apos testes |
| Scraping real | blocked | Aguardando Patrick definir fonte autorizada e limites |
| Transcricao bruta real | blocked | Aguardando Patrick definir politica de retencao/storage |
| Mensagem real ao Patrick | blocked | Nao enviar sem aprovacao explicita de ativacao |

## Estado operacional

- `hermes-fuinha.service` esta desabilitado e parado.
- O env-file ativo contem token Telegram dedicado da Fuinha e allowlist, ambos root-only e nao registrados em Git.
- Nao houve envio real de mensagem ao Patrick.
- Nao salvar transcricao bruta real ate Patrick definir politica de retencao.
- Nao usar fontes logadas, pagas, protegidas ou cursos sem autorizacao explicita.

## Ativacao real, 2026-06-23

- Iygge autorizou liberar a Fuinha para Patrick interagir no Telegram.
- `hermes-fuinha.service` foi habilitado e iniciado.
- Estado validado: `active (running)` e `enabled`.
- OpenClaw Eleve permaneceu saudavel.
