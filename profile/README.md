<div align="center">

# Engenharia Rockfeller

**O ponto de entrada para quem desenvolve nos projetos da organização**: padrões compartilhados, workflows e o fluxo de trabalho do dia a dia.

Feito para quem quer **começar rápido**, **abrir PRs no padrão** e **entregar com segurança**.

<img src="https://raw.githubusercontent.com/rockfellerfranchising/.github/main/assets/banner.png" alt="Rockfeller" width="100%">

[Site](https://rockfeller.com.br) · [Repositórios](https://github.com/rockfellerfranchising)

## Comece por aqui

</div>

1. Acesse os [repositórios da organização](https://github.com/rockfellerfranchising) e leia o `README.md` do projeto em que irá atuar.
2. Clone o repositório, instale as dependências com o gerenciador definido nele e execute os comandos de validação locais.
3. Crie uma branch a partir da branch de trabalho indicada pelo projeto.
4. Abra um *pull request* usando o [template padrão](https://github.com/rockfellerfranchising/.github/blob/main/PULL_REQUEST_TEMPLATE.md).

<div align="center">

## Ferramentas

</div>

Cada projeto define as próprias ferramentas: o `package.json` e o `README.md` do repositório são a fonte de verdade. A base compartilhada oferece suporte a:

- TypeScript e Node.js para aplicações e serviços;
- Bun, pnpm, npm ou Yarn para instalar dependências e rodar scripts;
- GitHub Actions para qualidade e entrega;
- Git e GitHub CLI (`gh`) para branches, *pull requests* e colaboração.

Tenha o Git e uma versão atual do Node.js instalados. Se o projeto usar a GitHub CLI, autentique-se uma vez:

```bash
gh auth login
```

<div align="center">

## Fluxo de desenvolvimento

</div>

```text
Issue ou tarefa → branch → desenvolvimento local → validações → pull request → revisão → integração
```

- Mantenha mudanças pequenas e focadas em uma tarefa.
- Rode os scripts do projeto, normalmente `lint`, `typecheck`, `test`, `build` e `format-check` quando existirem.
- Descreva no PR o contexto, a solução e como validou.
- Não envie segredos, arquivos `.env` ou dados pessoais.

<div align="center">

## Padrões compartilhados

</div>

O repositório [`.github`](https://github.com/rockfellerfranchising/.github) concentra o que é comum aos projetos:

| Recurso | Para que serve |
| --- | --- |
| [Template de pull request](https://github.com/rockfellerfranchising/.github/blob/main/PULL_REQUEST_TEMPLATE.md) | Estrutura a descrição e a validação das alterações. |
| [Governança de PR](https://github.com/rockfellerfranchising/.github/blob/main/.github/workflows/reusable-pr-governance.yml) | Valida a origem do PR e o preenchimento do template. |
| [Qualidade TypeScript](https://github.com/rockfellerfranchising/.github/blob/main/.github/workflows/reusable-typescript-quality.yml) | Lint, tipos, testes, build e formatação. |
| [Quality Gate](https://github.com/rockfellerfranchising/.github/blob/main/.github/workflows/required-typescript-quality-gate.yml) | Workflow para ser exigido nas regras do repositório. |
| [Deploy de produção](https://github.com/rockfellerfranchising/.github/blob/main/.github/workflows/reusable-production-release-deploy.yml) e [staging](https://github.com/rockfellerfranchising/.github/blob/main/.github/workflows/reusable-staging-release-deploy.yml) | Só release publicada faz deploy. |

<div align="center">

## Precisa de ajuda?

Abra uma *issue* no repositório da dúvida ou procure quem cuida do projeto.<br>
Para mudar os padrões globais, use o repositório [`.github`](https://github.com/rockfellerfranchising/.github).

</div>
