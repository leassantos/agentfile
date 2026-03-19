# Codex Workflow Template

Template de workflow para projetos usando o OpenAI Codex como agente de desenvolvimento.
Baseado nas práticas do criador do Claude Code, adaptado para o Codex.

---

## O que é este template

Uma estrutura de arquivos de configuração que instrui o Codex sobre como trabalhar no seu projeto — quais regras seguir, como planejar antes de implementar, como revisar código e como fazer commits e PRs de forma padronizada.

Funciona como um "manual de instruções" que o agente lê automaticamente em cada task.

---

## Estrutura

```
.
├── AGENTS.md                        ← lido automaticamente pelo Codex em toda task
└── .codex/
    ├── instructions.md              ← contexto arquitetural e decisões do projeto
    ├── agents/
    │   ├── code-reviewer.md         ← subagente especializado em revisão de código
    │   └── security-auditor.md      ← subagente especializado em segurança
    └── prompts/
        ├── plan-mode.md             ← template para planejamento de features
        └── commit-push-pr.md        ← template para finalizar com commit e PR
```

---

## Como usar: passo a passo

### Passo 1 — clone o template

```bash
git clone https://github.com/seu-usuario/codex-workflow-template.git meu-projeto
cd meu-projeto
rm -rf .git
git init
```

### Passo 2 — preencha os arquivos de configuração

Esta é a etapa mais importante. Abra cada arquivo e substitua todos os blocos marcados com `[PREENCHER]`.

#### 2.1 — `AGENTS.md` (obrigatório, prioridade máxima)

Este é o arquivo que o Codex lê em toda task. Ele define as regras que o agente nunca pode violar.

Preencha:
- Nome e descrição do projeto
- Stack completa (linguagem, framework, banco, ferramentas)
- Regras de arquitetura específicas do seu projeto
- Convenções de teste
- Regras de segurança
- O que o agente nunca deve fazer

Exemplo de preenchimento:
```markdown
# Meu E-commerce — Instruções para o agente

## Contexto do projeto
API de e-commerce para venda de produtos digitais.
Stack: Python 3.12, FastAPI, PostgreSQL, SQLAlchemy, pytest.

## Regras obrigatórias
...
```

#### 2.2 — `.codex/instructions.md`

Contexto mais profundo que o agente consulta ao tomar decisões arquiteturais.

Preencha conforme o projeto evolui — não precisa estar completo no início. Adicione:
- Decisões arquiteturais com justificativa (o "por quê")
- Lista de módulos planejados e seus status
- Variáveis de ambiente necessárias
- Formato padrão de responses (se for uma API)
- Glossário de termos do domínio

#### 2.3 — `.codex/prompts/commit-push-pr.md`

Preencha apenas o bloco "Configurações do projeto" no topo com:
- Comando de testes do seu projeto
- Comando de lint/formatação
- Labels e reviewers padrão do PR

Exemplo:
```markdown
- Comando de testes: pytest --cov=src
- Comando de lint: ruff check . && mypy src
- Labels padrão do PR: feature, needs-review
- Reviewers padrão: @seu-tech-lead
```

#### 2.4 — `.codex/agents/code-reviewer.md` e `security-auditor.md`

Substitua `[NOME DO PROJETO]` nos dois arquivos.

Em `code-reviewer.md`, adicione nos blocos `[PREENCHER]`:
- Vulnerabilidades específicas da sua stack
- Antipadrões da sua linguagem/framework
- Convenções de teste do projeto

Em `security-auditor.md`, adicione no bloco "Específicos do projeto":
- Requisitos de segurança do seu domínio (LGPD, PCI-DSS, etc.)
- Validações específicas do negócio

---

### Passo 3 — use o workflow em cada feature

#### 3.1 — planejamento (sempre o primeiro passo)

Abra uma nova task no Codex. Cole o conteúdo de `.codex/prompts/plan-mode.md` e substitua apenas o bloco marcado com a descrição da feature:

```
[DESCREVA AQUI O QUE PRECISA SER IMPLEMENTADO]
```

Aguarde o plano. Revise. Ajuste se necessário. Só aprove quando o plano estiver correto — é muito mais barato corrigir um plano do que corrigir código.

#### 3.2 — execução

Após aprovar o plano, instrua o Codex a implementar. Para features maiores, divida em tasks paralelas por camada:

| Task | Exemplo de escopo |
|------|-------------------|
| Task A | Modelos de dados, migrations, repositórios |
| Task B | Lógica de negócio (services/use cases) |
| Task C | Controllers/rotas, DTOs, testes de integração |

Inclua ao final de cada task:
```
Após implementar, rode [comando de testes] e corrija qualquer falha antes de encerrar.
```

Isso ativa o feedback loop — o agente testa, vê os erros e corrige sozinho.

#### 3.3 — revisão de código

Após a implementação, invoque o agente de revisão:

```
Usando as instruções em .codex/agents/code-reviewer.md,
revise os seguintes arquivos: [lista dos arquivos modificados]
```

Para features com autenticação, dados sensíveis ou integrações externas, invoque também o auditor de segurança:

```
Usando as instruções em .codex/agents/security-auditor.md,
audite os seguintes arquivos: [lista dos arquivos relevantes]
```

#### 3.4 — commit e PR

Cole o conteúdo de `.codex/prompts/commit-push-pr.md` em uma task.
O agente vai verificar o estado do repo, rodar os testes, formatar o código, escrever o commit em Conventional Commits e abrir o PR com descrição estruturada.

---

## Fluxo resumido

```
Nova feature
    │
    ▼
[plan-mode.md] → plano gerado → revisão humana → aprovação
    │
    ▼
Execução (tasks paralelas se for grande)
    │
    ▼
Feedback loop automático (testa → corrige → testa)
    │
    ▼
[code-reviewer.md] → relatório de revisão → correções
    │
    ▼
[security-auditor.md] → auditoria → correções (se houver)
    │
    ▼
[commit-push-pr.md] → commit + push + PR aberto
```

---

## Dicas de uso

**Mantenha o `AGENTS.md` atualizado.** Quando o agente fizer algo errado repetidamente, adicione uma regra explícita. Ex: se ele insistir em usar um padrão que você não quer, escreva "Nunca use X, sempre use Y" no `AGENTS.md`.

**Registre decisões em `instructions.md`.** Sempre que você tomar uma decisão arquitetural importante, documente ali com a justificativa. Isso evita que o agente tome a decisão oposta na próxima task.

**Versione tudo no Git.** Esses arquivos são tão importantes quanto o código. O time inteiro se beneficia das mesmas regras e prompts quando estão no repositório.

**Comece simples.** Não tente preencher tudo no dia 1. Comece com o `AGENTS.md` básico e vá refinando conforme o projeto avança e você identifica padrões e antipadrões.

---

## Licença

MIT — use, adapte e distribua à vontade.
