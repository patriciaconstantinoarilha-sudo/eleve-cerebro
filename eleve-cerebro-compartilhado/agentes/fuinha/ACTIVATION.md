# Ativacao Fuinha

Status: ativa para interacao real do Patrick no Telegram.

## Decisao

Iygge autorizou liberar a Fuinha para Patrick interagir diretamente pelo Telegram em 2026-06-23.

## Estado vivo validado

- Service: `hermes-fuinha.service`
- Estado: `active (running)`
- Habilitacao: `enabled`
- Inicio observado: 2026-06-23 17:52 UTC
- Canal: Telegram dedicado da Fuinha
- Runtime: Hermes isolado em `/opt/eleve-hermes-fuinha`
- Provider: OpenAI Codex
- Modelo: `gpt-5.5`

## Evidencias

- Bot dedicado validado com `getMe` antes da ativacao.
- Hash do token da Fuinha diferente do bot OpenClaw Eleve.
- Gateway ativo sem conflito de polling observado apos ativacao.
- Stop lifecycle corrigido previamente com `KillSignal=SIGINT`.
- OpenClaw Eleve permaneceu saudavel com `healthz=200` e `readyz=200`.

## Limites que continuam ativos

- Scraping real depende de fonte autorizada por Patrick/Instituto Eleve.
- Transcricao bruta depende de politica de retencao/storage.
- Recorrencia automatica depende de frequencia, fontes, limites e revisor aprovados.
- Contato com terceiros ou publicacao externa continua exigindo aprovacao explicita.
- Segredos permanecem fora do Git, em cofre/env-file root-only.

## Primeiro Oi

Patrick pode iniciar a conversa com a Fuinha. O primeiro ciclo deve coletar apenas calibracao inicial e salvar resumo confirmado no cerebro, sem pedir segredo.
