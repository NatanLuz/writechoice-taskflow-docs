# Documentação da TaskFlow API

Site de documentação em português brasileiro, construído com Mintlify. A especificação `openapi.yaml` é a fonte de verdade para os contratos e alimenta a referência interativa configurada em `docs.json`.

## Prévia local

Tenha o Node.js instalado. Na raiz do projeto, onde está `docs.json`, execute:

```bash
npx --yes mint dev
```

Este comando abriu a prévia local neste ambiente. No Windows com Node.js 24, a ferramenta de prévia pode apresentar falhas intermitentes relacionadas a `p-cancelable`. Quando funcionar, abra o endereço informado pelo CLI, normalmente `http://localhost:3000`.

## Validar a documentação

Para validar a estrutura e o conteúdo do projeto Mintlify, execute:

```bash
npx mintlify validate
```

A validação foi concluída com sucesso neste projeto. Ela verifica a documentação local, mas não envia requisições à TaskFlow API nem substitui testes reais dos endpoints. Testes da API exigem chamadas HTTP separadas com credenciais válidas; não fazem parte dos comandos acima.

## Estrutura

- `index.mdx`: visão geral e fluxo de uso.
- `quickstart.mdx`: fluxo de ponta a ponta com cURL.
- `authentication.mdx`: uso seguro da autenticação Bearer.
- `errors.mdx`: erros e limitações documentados.
- `openapi.yaml`: contratos e exemplos das cinco operações, referenciados pela navegação Mintlify.
- `docs.json`: identidade, navegação e configuração do playground.

`openapi.backup.yaml` é uma cópia de segurança e está listado em `.gitignore`, que impede que o Git passe a rastreá-lo. O mesmo arquivo também está em `.mintignore`, que controla o que o Mintlify ignora ao processar ou publicar a documentação. Cada arquivo atua em seu próprio fluxo; `.mintignore` não substitui `.gitignore`.

## Manutenção

- Atualize os contratos em `openapi.yaml` quando a API mudar e mantenha os guias coerentes com a especificação.
- Use placeholders em exemplos públicos; nunca inclua chaves reais ou dados sensíveis.
- Revise a navegação e os links ao renomear ou adicionar páginas.
- Antes da publicação, rode `npx mintlify validate` e confira a prévia com `npx --yes mint dev`.
- A publicação depende da integração do repositório com o fluxo de deploy Mintlify configurado para o projeto. Revise o site publicado após o deploy.
