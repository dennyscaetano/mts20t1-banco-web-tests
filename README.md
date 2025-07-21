# mts20t1-banco-web-tests

## Objetivo

Este projeto tem como objetivo demonstrar, para os alunos da Mentoria 2.0, como automatizar testes de aplicações web utilizando o Cypress. Aqui você aprenderá a estruturar automações, criar comandos customizados (Custom Commands), organizar cenários de teste e gerar relatórios completos, tudo com foco em aplicações reais.

## Componentes do Projeto

- **Cypress**: Framework principal de automação de testes end-to-end.
- **Custom Commands**: Comandos personalizados para reutilização de lógicas comuns nos testes.
- **cypress-mochawesome-reporter**: Geração de relatórios detalhados e visualmente amigáveis.
- **Estrutura de pastas**:
  - `cypress/e2e/`: Scripts de teste automatizados.
  - `cypress/fixtures/`: Dados de apoio (ex: credenciais).
  - `cypress/support/commands/`: Implementação dos Custom Commands.
  - `cypress/support/`: Configurações e comandos globais do Cypress.

## Pré-requisitos

- Node.js (versão recomendada: 18.x ou superior)
- npm (gerenciador de pacotes)
- A API [mts20t1-banco-api](https://github.com/dennyscaetano/mts20t1-banco-api) em execução
- A aplicação Web [mts20t1-banco-web](https://github.com/dennyscaetano/mts20t1-banco-web) em execução

## Instalação

1. Clone este repositório:
   ```bash
   git clone https://github.com/seu-usuario/mts20t1-banco-web-tests.git
   cd mts20t1-banco-web-tests
   ```

2. Instale as dependências:
   ```bash
   npm install
   ```

3. Certifique-se de que a API e a aplicação web estejam rodando conforme instruções dos respectivos repositórios.

## Execução dos Testes

- Para rodar os testes em modo interativo (GUI):
  ```bash
  npx cypress open
  ```
- Para rodar os testes em modo headless (terminal) e gerar relatório:
  ```bash
  npx cypress run
  ```

- Para gerar o relatório Mochawesome após a execução:
  ```bash
  npx mochawesome-merge cypress/reports/*.json -o cypress/reports/report.json
  npx marge cypress/reports/report.json -f report -o cypress/reports/html
  ```
  O relatório em HTML estará disponível em `cypress/reports/html/report.html`.

## Estrutura dos Testes

- **login.cy.js**: Testes relacionados ao fluxo de login.
- **transferencia.cy.js**: Testes do fluxo de transferência bancária.

Os testes utilizam dados do arquivo `cypress/fixtures/credenciais.json` para simular diferentes cenários.

### Exemplo de Teste

```js
// login.cy.js
cy.login('usuario', 'senha');
// transferencia.cy.js
cy.realizarTransferencia({ origem: '0001', destino: '0002', valor: 100 });
```

## Custom Commands

Os comandos customizados estão localizados em `cypress/support/commands/` e são utilizados para:

- **login.js**: Automatizar o login na aplicação.
- **transferencia.js**: Automatizar o fluxo de transferência.
- **common.js**: Comandos utilitários reutilizáveis em diferentes cenários.

#### Exemplos de Uso

```js
// Realiza login
cy.login('usuario', 'senha');

// Realiza transferência
cy.realizarTransferencia({ origem: '0001', destino: '0002', valor: 100 });
```

## Relatórios

Após a execução dos testes, os relatórios são gerados automaticamente na pasta `cypress/reports/` utilizando o `cypress-mochawesome-reporter`. O relatório em HTML pode ser aberto no navegador para análise detalhada dos resultados.

## Contribuição

Sinta-se à vontade para abrir issues ou pull requests com sugestões de melhorias ou correções.

---

> **Dica:** Sempre mantenha a API e a aplicação web em execução antes de rodar os testes para garantir o funcionamento correto dos cenários automatizados. 