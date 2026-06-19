# Padrões de Branches, Commits, Pull Requests e Testes

Este documento define os padrões adotados pela equipe para organização do repositório, nomenclatura de branches, mensagens de commit, Pull Requests da Prova 2

## 1. Branch principal

A branch principal do repositório é:

```txt
main
```

A branch `main` deve representar a versão estável do projeto. Alterações não devem ser feitas diretamente na `main`. Toda mudança deve ser realizada em uma branch específica e integrada por meio de Pull Request.

## 2. Modelos de ramificação utilizados

Este repositório é usado para demonstrar três modelos de ramificação, um por cenário da atividade:

| Cenário | Modelo | Branches envolvidas |
|---|---|---|
| 3 | Trunk-Based Development | `main`, `feature-*` (vida curta) |

## 3. Fluxo de trabalho geral

O fluxo padrão do repositório é:

```txt
main -> branch de trabalho -> Pull Request -> revisão -> merge na main (ou develop, no Cenário 2)
```

Antes de iniciar uma nova alteração, a branch base local deve ser atualizada:

```bash
git checkout main
git pull origin main
```

Em seguida, deve ser criada a branch específica para a tarefa (veja o padrão de nomes na seção 4):

```bash
git checkout -b tipo/descricao-curta
```

Após finalizar a alteração, a branch deve ser enviada para o GitHub:

```bash
git push -u origin tipo/descricao-curta
```

A integração com a branch base deve ocorrer apenas após abertura, revisão e aprovação de um Pull Request.

## 4. Padrão de branches

Regras gerais, válidas para todos os cenários:

- usar letras minúsculas;
- não usar acentos;
- não usar espaços;
- separar palavras com hífen;
- usar nomes objetivos;
- indicar claramente o propósito da alteração.

### 4.1 Cenário 1 — GitHub Flow

| Branch | Finalidade |
|---|---|
| `nova-funcionalidade-homepage` | Branch única para as contribuições incrementais da homepage |

### 4.2 Cenário 2 — Git Flow

| Branch | Finalidade |
|---|---|
| `develop` | Integração das funcionalidades antes de uma release |
| `feature/nome-da-feature` | Uma funcionalidade nova (ex.: `feature/login`) |
| `release/vX.Y` | Preparação e ajustes finais de uma versão |
| `hotfix/vX.Y.Z` | Correção urgente, criada a partir da `main` |

### 4.3 Cenário 3 — Trunk-Based Development

| Branch | Finalidade |
|---|---|
| `feature-descricao-curta` | Branch de vida curta (no máximo 1 ciclo de commit antes do merge) |

Exemplos:

```txt
nova-funcionalidade-homepage
feature/login
release/v1.0
hotfix/v1.0.1
feature-cores-cardapio
feature-ajuste-rodape
```

## 5. Padrão de commits

As mensagens de commit devem seguir o formato:

```txt
tipo(escopo): descricao curta
```

Regras gerais:

- escrever em português;
- usar letras minúsculas;
- não finalizar com ponto;
- indicar a alteração de forma objetiva;
- evitar mensagens genéricas;
- evitar commits grandes com alterações não relacionadas.

Tipos permitidos:

| Tipo | Finalidade |
|---|---|
| `feat` | Nova funcionalidade |
| `fix` | Correção de bug (não urgente) |
| `hotfix` | Correção urgente em produção (usado apenas no Cenário 2) |
| `style` | Ajustes visuais/CSS sem alteração de lógica |
| `docs` | Documentação (README, login.md, etc.) |
| `chore` | Configuração ou organização do projeto |
| `refactor` | Reorganização de código sem alteração de comportamento |
| `test` | Verificação ou checklist de teste simulado |

Escopos recomendados:

```txt
homepage
header
sobre
cardapio
contato
login
css
build
tags
```

Exemplos válidos:

```bash
git commit -m "feat(header): adiciona header e menu de navegacao"
```

```bash
git commit -m "feat(cardapio): adiciona secao de cardapio"
```

```bash
git commit -m "style(css): adiciona estilizacao geral da homepage"
```

```bash
git commit -m "feat(login): adiciona estrutura da tela de login"
```

```bash
git commit -m "hotfix(cardapio): corrige link quebrado do cardapio"
```

```bash
git commit -m "docs(padroes): adiciona padrao de branches e commits"
```

Exemplos inválidos:

```txt
mudancas
arrumei
atualizacao
commit do grupo
ajustes finais
nova versao
```

## 6. Pull Requests

Todo Pull Request deve ser aberto para a branch correta conforme o cenário (`main` nos Cenários 1 e 3; `develop` ou `main` no Cenário 2, dependendo da etapa).

As Pull Requests devem ser revisadas e aprovadas por pelo menos um integrante diferente de quem abriu o PR. Sugestão: definam dois revisores principais e substituam abaixo pelos nomes de usuário reais no GitHub:

```txt
@usuario1
@usuario2
```

O título do Pull Request deve seguir o mesmo padrão das mensagens de commit:

```txt
tipo(escopo): descricao curta
```

Exemplos:

```txt
feat(homepage): adiciona contribuicoes da nova homepage
feat(login): adiciona feature de login no git flow
hotfix(cardapio): corrige link quebrado em producao
docs(padroes): adiciona padrao de uso do git
```

## 7. Modelo de descrição de Pull Request

Todo Pull Request deve seguir o modelo abaixo (também disponível em `.github/PULL_REQUEST_TEMPLATE.md`):

```md
## O que foi feito

Descreva objetivamente as alterações realizadas.

## Cenário relacionado

- [ ] Cenário 1 — GitHub Flow
- [ ] Cenário 2 — Git Flow
- [ ] Cenário 3 — Trunk-Based Development

## Arquivos alterados

-
-
-

## Como testar

1.
2.
3.

## Evidências

Print ou descrição do resultado observado ao abrir a página no navegador.

## Observações

Inclua pendências, limitações ou pontos que exigem atenção na revisão.
```

## 8. Critérios de revisão

Antes da aprovação de um Pull Request, devem ser verificados os seguintes pontos:

- a branch segue o padrão definido na seção 4;
- os commits seguem o padrão definido na seção 5;
- não há arquivos desnecessários (ex.: `preview.png`, arquivos temporários);
- a descrição do Pull Request informa como testar;
- não há conflitos com a branch de destino.

## 10. Checklist antes de abrir Pull Request

```txt
[ ] A branch segue o padrão definido
[ ] Os commits seguem o padrão definido
[ ] Os arquivos estão nas pastas corretas
[ ] Não há arquivos desnecessários
[ ] A descrição do Pull Request informa como testar
[ ] Não há conflitos com a branch de destino
```

## 11. Tags (Cenário 2 — Git Flow)

Tags marcam versões oficiais do projeto:

```bash
git tag -a v1.0 -m "Versao 1.0 - lancamento inicial"
git tag -a v1.0.1 -m "Hotfix - correcao do link do cardapio"
git push origin --tags
```

## 12. Comandos úteis

Atualizar a branch principal:

```bash
git checkout main
git pull origin main
```

Criar uma branch:

```bash
git checkout -b feature/login
```

Verificar alterações:

```bash
git status
```

Adicionar arquivos:

```bash
git add .
```

Criar commit:

```bash
git commit -m "feat(login): adiciona estrutura da tela de login"
```

Enviar branch:

```bash
git push -u origin feature/login
```

Voltar para a branch principal:

```bash
git checkout main
```

Atualizar a branch principal após o merge:

```bash
git pull origin main
```