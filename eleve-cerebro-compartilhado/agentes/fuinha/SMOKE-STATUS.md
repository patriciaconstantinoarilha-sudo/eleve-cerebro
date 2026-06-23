# Smoke Status Fuinha

Status geral: bootstrap tecnico parcialmente aprovado, aguardando Codex OAuth e handoff do cliente para uso real.

| Smoke | Status | Evidencia |
|---|---|---|
| Isolamento runtime | pass | Runtime separado em `/opt/eleve-hermes-fuinha`, usuario `fuinha`, service `hermes-fuinha.service` |
| Hermes CLI | pass | Hermes Agent v0.17.0, release 2026.6.19, CLI responde `version` e `--help` |
| Runtime pin | pass | Upstream `NousResearch/hermes-agent`, tag `v2026.6.19`, commit `2bd1977d8fad185c9b4be47884f7e87f1add0ce3` |
| Brain GitHub | pass | Area `eleve-cerebro-compartilhado/agentes/fuinha/` criada e enviada para `main` |
| Telegram | pass parcial | Credencial carregada via env-file root-only e `getMe` read-only retornou ok. Service permanece desabilitado e parado |
| Composio | pass parcial | Credencial presente em env-file root-only. Integracao MCP/ferramenta ainda depende de selecao no handoff tecnico |
| Codex-first | blocked | Provider configurado como OpenAI Codex e sem fallback de chave de API. Falta login OAuth interativo em `/opt/eleve-hermes-fuinha/home/auth.json` |
| Service lifecycle | pass | Unit valida em systemd, `TimeoutStopSec=240`, service desabilitado e parado por seguranca |
| Scraping | blocked | Usar apenas smoke sintetico/autorizado ate Patrick definir fonte |
| Recusa conteudo proibido | pending | Teste comportamental apos Codex OAuth |

## Estado operacional

- Nao iniciar `hermes-fuinha.service` permanentemente antes do login Codex OAuth e aprovacao de ativacao.
- Nao enviar mensagem real ao Patrick antes do handoff/ativacao.
- Nao salvar transcricao bruta real ate o Patrick definir politica de retencao.
- Nao usar fontes logadas, pagas, protegidas ou cursos sem autorizacao explicita.
