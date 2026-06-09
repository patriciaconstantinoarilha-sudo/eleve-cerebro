# Eleve Cérebro

Estrutura inicial dos cérebros do Instituto Eleve criada pela Júpiter Tech durante o bootstrap da Agente Eleve.

## Estrutura

- `eleve-cerebro-compartilhado/` — memória operacional compartilhável do Instituto Eleve.
- `eleve-cerebro-diretoria/` — camada de diretoria/governança com acesso controlado.

## Segurança

- Segredos não devem ser versionados neste repositório.
- Tokens, senhas, chaves privadas, IDs sensíveis e arquivos `.env` devem permanecer no cofre/secret manager do tenant.
- Dados reais de alunos, saúde, financeiro, menores ou identificáveis só entram após allowed-context e política de retenção aprovados.
