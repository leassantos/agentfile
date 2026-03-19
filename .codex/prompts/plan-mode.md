# Prompt template: plan mode (nova feature)

> Como usar: cole este arquivo inteiro em uma nova task do Codex.
> Substitua apenas o bloco "Feature solicitada" antes de enviar.
> NÃO modifique o restante — ele instrui o agente a trabalhar corretamente.

---

## Instruções para o agente

Antes de escrever qualquer código, gere um plano detalhado para a feature descrita abaixo.
**NÃO implemente nada ainda.** Apresente o plano completo e aguarde minha aprovação explícita.

### Feature solicitada

<!-- ✏️  SUBSTITUA ESTE BLOCO ANTES DE ENVIAR -->
[DESCREVA AQUI O QUE PRECISA SER IMPLEMENTADO]
<!-- Seja específico: o que deve fazer, o que não deve fazer, restrições conhecidas -->

---

### Contexto do projeto
- Leia o arquivo `AGENTS.md` na raiz do projeto para as regras obrigatórias.
- Leia o arquivo `.codex/instructions.md` para o contexto arquitetural e decisões já tomadas.
- Analise o código existente antes de propor qualquer estrutura nova — siga os padrões já estabelecidos.

### O plano deve conter obrigatoriamente

**1. Entendimento da feature**
- O que exatamente precisa ser implementado?
- Quais são os casos de uso principais (happy paths)?
- Quais são os casos de borda e erros esperados?
- Há ambiguidades que precisam ser esclarecidas antes de começar?

**2. Impacto no sistema existente**
- Quais arquivos existentes serão modificados?
- Quais arquivos novos serão criados?
- Há necessidade de migration de banco de dados?
- Alguma breaking change em interfaces existentes?

**3. Estrutura proposta**
- Liste cada arquivo a ser criado ou modificado com uma breve descrição de sua responsabilidade.
- Mostre a assinatura dos métodos/funções principais (sem implementação).
- Mostre o schema de banco de dados se houver migration.

**4. Plano de testes**
- Quais cenários serão cobertos por testes de unidade?
- Quais cenários precisam de testes de integração?
- Como os testes validarão os casos de erro (unhappy paths)?

**5. Considerações de segurança**
- Há dados sensíveis envolvidos?
- Quais rotas/endpoints serão públicos vs autenticados?
- Há validações de entrada necessárias?
- Algum risco de segurança específico nessa feature?

**6. Estimativa de complexidade**
- Baixa / Média / Alta — com justificativa.

---

Após apresentar o plano completo, aguarde minha aprovação antes de qualquer implementação.
Se houver dúvidas ou ambiguidades, liste-as antes do plano.
