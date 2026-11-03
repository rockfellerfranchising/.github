<p align="center">
  <img src="assets/banner.png" alt="Rockfeller" width="100%">
</p>

# Rockfellerfranchising `.github`

Arquivos comunitários e automações globais da organização.

## O que existe aqui

- `PULL_REQUEST_TEMPLATE.md` e `.github/pr-template-spec.json`: template de PR e o contrato usado para validá-lo.
- `reusable-pr-governance.yml`: valida a branch de origem e o body do PR.
- `reusable-typescript-quality.yml`: roda lint, typecheck, test, build e format-check (quando configurados) com `bun`, `pnpm`, `npm` ou `yarn`.
- `reusable-production-release-deploy.yml` e `reusable-staging-release-deploy.yml`: validam a release publicada e devolvem a tag e o SHA verificados.
- `required-typescript-quality-gate.yml`: workflow para ser exigido por ruleset da organização.
- `workflow-templates/typescript-quality-gate.yml`: template para repositórios TypeScript.

Os workflows ficam em `.github/workflows/`.

## Como usar

1. Repositórios TypeScript usam o template `TypeScript Quality Gate` ou chamam os reusable workflows direto.
2. `main`, `develop` e `staging` ficam protegidas por rulesets. A `main` exige PR vindo de `develop`, `staging` ou `hotfix/*`.
3. O body do PR segue o `PULL_REQUEST_TEMPLATE.md`.

Se `required-typescript-quality-gate.yml` for exigido por ruleset, ele deve referenciar os reusable workflows com `owner/repo/path@ref`. Caminho relativo não funciona nesse caso.

## Deploy só por release

Só release publicada faz deploy: pre-release de `develop` vai para `staging` e release estável de `main` vai para `production`. Cada repositório chama o gate do ambiente e roda o próprio deploy com os secrets do GitHub Environment. Desative o auto-deploy do provedor para que um push não passe por fora da regra.

```yaml
jobs:
  production-gate:
    if: ${{ !github.event.release.prerelease }}
    uses: rockfellerfranchising/.github/.github/workflows/reusable-production-release-deploy.yml@main

  deploy-production:
    needs: production-gate
    if: ${{ !github.event.release.prerelease }}
    runs-on: ubuntu-latest
    environment: production
    concurrency:
      group: deploy-production
      cancel-in-progress: false
    steps:
      - uses: actions/checkout@v4
        with:
          ref: ${{ needs.production-gate.outputs.release-tag }}
      - run: ./scripts/deploy-production.sh
```

Para staging, use `reusable-staging-release-deploy.yml` em uma pre-release.

## Exemplo em um repositório

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
      bun-version: "1.3.8"
      require-build: true
```
