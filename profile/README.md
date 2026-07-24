<div align="center">
  # Engenharia Rockfeller

  Este é o ponto de entrada para quem desenvolve nos projetos da organização.
</div>

## Comece por aqui

1. Acesse os [repositórios da organização](https://github.com/rockfellerfranchising) e leia o `README.md` do projeto em que irá atuar.
2. Clone o repositório, instale as dependências com o gerenciador definido nele e execute os comandos de validação locais.
3. Crie uma branch a partir da branch de trabalho indicada pelo projeto.
4. Abra um *pull request* usando o [template padrão](https://github.com/rockfellerfranchising/.github/blob/main/PULL_REQUEST_TEMPLATE.md).

## Ferramentas e skills

Os projetos podem utilizar ferramentas diferentes; o `package.json` e o `README.md` de cada repositório são a fonte de verdade. A base compartilhada já oferece suporte a:

- **TypeScript e Node.js** para aplicações e serviços;
- **Bun, pnpm, npm ou Yarn** para instalação e execução de scripts;
- **GitHub Actions** para automações de qualidade e entrega;
- **Git e GitHub CLI (`gh`)** para branches, *pull requests* e colaboração.

Antes de começar, confirme que você tem o Git e uma versão atual do Node.js instalados. Quando o projeto usar a GitHub CLI, autentique-se uma vez:

```bash
gh auth login
```

## Fluxo de desenvolvimento

```text
Issue ou tarefa → branch → desenvolvimento local → validações → pull request → revisão → integração
```

- Mantenha mudanças pequenas e focadas em uma tarefa.
- Rode os scripts definidos pelo projeto — normalmente `lint`, `typecheck`, `test`, `build` e `format-check` quando disponíveis.
- Descreva no PR o contexto, a solução e como a alteração foi validada.
- Não envie segredos, arquivos `.env` ou dados pessoais para o repositório.

## Padrões compartilhados

O repositório [`.github`](https://github.com/rockfellerfranchising/.github) concentra o que é comum aos projetos:

| Recurso | Para que serve |
| --- | --- |
| [Template de pull request](https://github.com/rockfellerfranchising/.github/blob/main/PULL_REQUEST_TEMPLATE.md) | Estrutura a descrição e a validação das alterações. |
| [Governança de PR](https://github.com/rockfellerfranchising/.github/blob/main/.github/workflows/reusable-pr-governance.yml) | Valida a origem do PR e o preenchimento do template. |
| [Qualidade TypeScript](https://github.com/rockfellerfranchising/.github/blob/main/.github/workflows/reusable-typescript-quality.yml) | Workflow reutilizável para lint, tipos, testes, build e formatação. |
| [Quality Gate](https://github.com/rockfellerfranchising/.github/blob/main/.github/workflows/required-typescript-quality-gate.yml) | Workflow pronto para ser exigido nas regras do repositório. |

## Precisa de ajuda?

Abra uma *issue* no repositório relacionado à dúvida ou procure a pessoa responsável pelo projeto. Para mudanças nos padrões globais, utilize o repositório [`.github`](https://github.com/rockfellerfranchising/.github).
