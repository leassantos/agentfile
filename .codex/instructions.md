# Contexto estendido — [NOME DO PROJETO]

> Este arquivo complementa o AGENTS.md com contexto arquitetural mais profundo.
> O agente consulta isso para tomar decisões consistentes com o que já foi definido.
> Preencha conforme o projeto evolui — não precisa estar completo no dia 1.

---

## Decisões arquiteturais registradas

> Para cada decisão importante, documente o "por quê", não apenas o "o quê".
> Isso evita que o agente reverta decisões já tomadas.

### [PREENCHER: nome da decisão — ex. Por que REST e não GraphQL?]
[PREENCHER: contexto e justificativa da decisão]

### [PREENCHER: outra decisão]
[PREENCHER: justificativa]

---

## Módulos planejados

> Liste os módulos/features do projeto em ordem de prioridade.
> Marque o status de cada um para o agente saber o que já existe.

| Módulo | Status | Descrição |
|--------|--------|-----------|
| [PREENCHER] | Em desenvolvimento | [PREENCHER] |
| [PREENCHER] | Planejado | [PREENCHER] |
| [PREENCHER] | Planejado | [PREENCHER] |

---

## Variáveis de ambiente esperadas

> Liste todas as variáveis de ambiente que a aplicação usa.
> O agente nunca deve hardcodar valores que deveriam vir de variáveis de ambiente.

```
[PREENCHER: NOME_DA_VAR]=<descrição do valor esperado>
[PREENCHER: OUTRA_VAR]=<descrição>
```

---

## Convenções de API

> Se o projeto for uma API, documente o formato padrão de response aqui.
> O agente seguirá esse padrão em todos os endpoints que criar.

### Response de sucesso
```json
[PREENCHER: cole aqui um exemplo do formato de sucesso]
```

### Response de erro
```json
[PREENCHER: cole aqui um exemplo do formato de erro]
```

### Endpoints existentes

| Método | Path | Auth | Descrição |
|--------|------|------|-----------|
| [PREENCHER] | [PREENCHER] | [Sim/Não] | [PREENCHER] |

---

## Contexto de negócio

> Explique termos do domínio que o agente precisa conhecer para nomear coisas corretamente.

- **[PREENCHER: termo do domínio]**: [PREENCHER: definição]
- **[PREENCHER: outro termo]**: [PREENCHER: definição]
