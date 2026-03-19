# Prompt template: commit + push + PR

> Como usar: cole este arquivo em uma task do Codex após a feature estar implementada
> e os testes passando. Não requer substituição de placeholders — funciona como está.
> Adapte apenas o bloco "Configurações do projeto" na primeira vez que usar.

---

## Configurações do projeto

> ✏️ Preencha uma vez, na configuração inicial do template.

- Comando de testes: [PREENCHER: ex. mvn verify / pytest / npm test]
- Comando de lint/formatação: [PREENCHER: ex. mvn checkstyle:check / ruff check . / npm run lint]
- Labels padrão do PR: [PREENCHER: ex. feature, needs-review]
- Reviewers padrão: [PREENCHER: ex. @username ou deixar vazio]

---

## Instruções para o agente

Execute as etapas abaixo em sequência. Pare e me informe se qualquer etapa falhar.
Não avance para a próxima etapa sem confirmar que a atual foi concluída com sucesso.

### Etapa 1 — verificar estado do repositório
```
git status
git diff --stat
```
Liste os arquivos modificados. Confirme que não há arquivos não relacionados à feature incluídos.
Se houver arquivos inesperados, me informe antes de continuar.

### Etapa 2 — rodar os testes
```
[PREENCHER: comando de testes do projeto]
```
Se algum teste falhar, corrija o problema antes de continuar.
Não faça commit de código com testes falhando.

### Etapa 3 — verificar formatação e lint
```
[PREENCHER: comando de lint/formatação]
```
Corrija qualquer violação antes de continuar.

### Etapa 4 — preparar o commit
Adicione apenas os arquivos relacionados à feature atual:
```
git add <arquivos relevantes>
```
Nunca use `git add .` sem listar e confirmar cada arquivo incluído.

### Etapa 5 — escrever a mensagem de commit
Siga o padrão Conventional Commits:

```
<tipo>(<escopo>): <descrição curta em inglês, imperativo, sem ponto final>

<corpo opcional: explique o "por quê", não o "o quê" — quando a mudança não é óbvia>

Closes #<número da issue, se houver>
```

Tipos válidos:
- `feat` — nova funcionalidade
- `fix` — correção de bug
- `test` — adição ou correção de testes
- `refactor` — refatoração sem mudança de comportamento
- `docs` — documentação
- `chore` — tarefas de manutenção (deps, config, etc.)
- `security` — correção de vulnerabilidade

Exemplos:
```
feat(auth): add JWT login endpoint
fix(user): prevent password exposure in error logs
test(auth): add unhappy path tests for login service
security(auth): enforce bcrypt cost factor 12
```

### Etapa 6 — fazer o push
```
git push origin <branch-atual>
```

### Etapa 7 — abrir o Pull Request
Crie um PR com a seguinte estrutura:

**Título**: mesma mensagem do commit principal (sem o tipo/escopo se for redundante com o título do PR)

**Descrição**:
```markdown
## O que foi feito
[descrição objetiva do que foi implementado]

## Motivação
[por que essa mudança foi necessária]

## Como testar
1. [passo 1]
2. [passo 2]
3. [resultado esperado]

## Checklist
- [ ] Testes passando
- [ ] Sem secrets ou dados sensíveis no código
- [ ] Migration de banco incluída (se aplicável)
- [ ] Documentação atualizada (se aplicável)
- [ ] Breaking changes documentadas (se aplicável)
```

Retorne a URL do PR criado ao finalizar.
