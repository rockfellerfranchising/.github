# Rockfellerfranchising `.github`

Arquivos comunitarios e automacoes globais da organizacao.

## O que existe aqui

- `PULL_REQUEST_TEMPLATE.md`: template padrao de PR da organizacao
- `.github/pr-template-spec.json`: contrato validado pelo workflow de governanca
- `.github/workflows/reusable-pr-governance.yml`: valida origem do PR e estrutura do body
- `.github/workflows/reusable-typescript-quality.yml`: roda lint, typecheck, test, build e format-check quando configurados, com suporte a `bun`, `pnpm`, `npm` e `yarn`
- `.github/workflows/required-typescript-quality-gate.yml`: workflow pronto para ser exigido por ruleset da organizacao
- `.github/workflow-templates/typescript-quality-gate.yml`: workflow template para repositorios TypeScript

## Estrategia recomendada

1. Repositorios TypeScript usam o template `TypeScript Quality Gate` ou chamam os reusable workflows diretamente.
2. `main`, `develop` e `staging` ficam protegidas por rulesets da organizacao.
3. O ruleset da `main` exige PR e usa o workflow de governanca para aceitar `develop`, `staging` ou branches `hotfix/*`.
4. O body do PR precisa seguir o `PULL_REQUEST_TEMPLATE.md`.

Observacao:

Quando `.github/workflows/required-typescript-quality-gate.yml` for usado como workflow exigido por ruleset, ele deve referenciar os reusable workflows com `owner/repo/path@ref`, nao com caminho relativo.

## Exemplo de uso direto em um repositorio

```yaml
name: Quality Gate

on:
  pull_request:
    branches: [main, develop, staging]
  push:
    branches: [develop, staging]

permissions:
  contents: read
  pull-requests: read

jobs:
  governance:
    if: ${{ github.event_name == 'pull_request' }}
    uses: rockfellerfranchising/.github/.github/workflows/reusable-pr-governance.yml@main

  quality:
    uses: rockfellerfranchising/.github/.github/workflows/reusable-typescript-quality.yml@main
    with:
        node-version: "22"
        bun-version: "1.1.26"
        require-build: true
```
