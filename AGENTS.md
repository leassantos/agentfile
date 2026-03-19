# [NOME DO PROJETO] — Instruções para o agente

> Arquivo lido automaticamente pelo Codex em toda task.
> Preencha todas as seções marcadas com `[PREENCHER]` antes de começar o projeto.
> Remova os comentários em `>` após preencher.

## Contexto do projeto

> Descreva em 2-3 frases o que o projeto faz e para quem.

[PREENCHER: descrição do projeto]

Stack:
- Linguagem: [PREENCHER: ex. Java 21 / Python 3.12 / TypeScript 5]
- Framework: [PREENCHER: ex. Spring Boot 3 / FastAPI / NestJS]
- Banco de dados: [PREENCHER: ex. PostgreSQL / MySQL / MongoDB]
- Gerenciador de build/pacotes: [PREENCHER: ex. Maven / pip / npm]
- Testes: [PREENCHER: ex. JUnit 5 + Mockito / pytest / Jest]

---

## Regras obrigatórias de desenvolvimento

> Adapte cada seção à sua stack. Remova o que não se aplica. Adicione o que falta.

### Linguagem e nomenclatura
- Código em: [PREENCHER: inglês / português]
- Documentação externa em: [PREENCHER: português / inglês]
- Pacote/módulo raiz: [PREENCHER: ex. com.empresa.projeto / src/projeto]
- Convenção de nomes: [PREENCHER: ex. camelCase para métodos, PascalCase para classes]

### Arquitetura
- [PREENCHER: padrão arquitetural adotado — ex. Controller → Service → Repository]
- [PREENCHER: regra de dependência entre camadas]
- [PREENCHER: como separar lógica de negócio de infraestrutura]
- [PREENCHER: padrão para objetos de entrada/saída — ex. DTOs obrigatórios, nunca expor entidades]

### Testes
- [PREENCHER: estratégia — ex. TDD obrigatório / testes após implementação]
- Cobertura mínima: [PREENCHER: ex. 80% de linhas por classe]
- Framework de unidade: [PREENCHER]
- Framework de integração: [PREENCHER]
- Convenção de nomes de testes: [PREENCHER: ex. methodName_scenario_expectedResult]

### Segurança
- [PREENCHER: regras de autenticação/autorização se houver]
- [PREENCHER: o que nunca deve aparecer em logs]
- [PREENCHER: como tratar erros para o cliente — ex. nunca expor stack traces]
- [PREENCHER: validação de entrada — ex. sempre validar com Bean Validation / Pydantic]

### Banco de dados
- [PREENCHER: ferramenta de migration — ex. Flyway / Alembic / Prisma Migrate]
- [PREENCHER: convenção de IDs — ex. UUID / ULID / auto-increment]
- [PREENCHER: onde aplicar transações]

### Build e formatação
- Comando para rodar os testes: [PREENCHER: ex. mvn verify / pytest / npm test]
- Linter/formatter: [PREENCHER: ex. Checkstyle / Ruff / ESLint + Prettier]
- Comando de formatação: [PREENCHER]

---

## O que NÃO fazer

> Liste antipadrões específicos da sua stack que o agente deve evitar.

- [PREENCHER: ex. Não usar @Autowired por campo — usar injeção por construtor]
- [PREENCHER: ex. Não usar print/console.log — usar logger estruturado]
- [PREENCHER: ex. Não commitar arquivos .env ou secrets]
- [PREENCHER: ex. Não criar métodos com mais de X linhas]
- [PREENCHER: ex. Não desabilitar regras de lint sem comentário justificando]
