# Entrega do desafio técnico — TaskFlow API

## 1. Visão geral da entrega

A entrega organiza a documentação da TaskFlow API para orientar quem está começando, descrever o contrato das operações e apoiar o diagnóstico de erros. O conteúdo está em português brasileiro e usa o OpenAPI como fonte de verdade para endpoints, parâmetros, schemas e respostas.

## 2. Processo de desenvolvimento e documentação

O processo começou pela leitura integral de `openapi.yaml` e pela revisão de `docs.json`, `index.mdx`, `quickstart.mdx`, `README.md` e `.mintignore`. Em seguida, organizei a navegação do Mintlify, substituí o conteúdo genérico do Starter Kit e alinhei os guias à especificação.

Os exemplos usam placeholders para chaves e IDs. A documentação informa que a autenticação é Bearer e que a primeira requisição pode levar até 60 segundos quando o servidor está inativo. A especificação OpenAPI foi validada com sucesso e a documentação foi visualizada localmente com Mintlify.

## 3. Decisões de estrutura e conteúdo

- **Visão geral:** apresenta a finalidade da API, o fluxo entre projetos e tarefas e os primeiros passos.
- **Guia de início rápido:** conduz pelo fluxo principal com exemplos cURL: criar projeto, criar tarefa, listar, atualizar e excluir.
- **Guia de autenticação:** explica o cabeçalho Bearer e orienta a proteger a chave de API nos exemplos e no uso cotidiano.
- **Referência OpenAPI:** centraliza os contratos dos cinco endpoints e mantém a referência ligada à especificação, evitando duplicar manualmente os detalhes técnicos.
- **Página sobre erros:** resume os códigos documentados, sugere verificações e registra dependências e limitações conhecidas.

## 4. Testes reais da API

Os testes manuais foram realizados em **22/10/2026 (UTC)**, usando cURL no CMD do Windows. Os cinco endpoints passaram pelo fluxo principal:

| Endpoint | HTTP | Resultado |
| --- | ---: | --- |
| `POST /projects` | `201` | Projeto criado com sucesso. |
| `POST /tasks` | `201` | Tarefa criada com status `pending`. |
| `GET /projects/{project_id}/tasks` | `200` | Retornou `total: 1` e a tarefa criada. |
| `PATCH /tasks/{task_id}` | `200` | Status atualizado para `in_progress`. |
| `DELETE /tasks/{task_id}` | `200` | Exclusão confirmada pela API. |

A API exigiu autenticação Bearer durante o uso. Os cenários de erro não foram testados integralmente; portanto, a tabela registra apenas os resultados do fluxo principal.

## 5. Desafios encontrados e possíveis melhorias

O OpenAPI fornece exemplos de respostas, mas não declara campos obrigatórios nos schemas de resposta. Por isso, a documentação não apresenta esses campos como obrigatórios além do que o contrato estabelece. A especificação também não define paginação, filtros ou limites de requisição, então esses recursos não foram presumidos.

Como próximos passos, recomenda-se testar sistematicamente os cenários de erro e revisar os exemplos de resposta com a equipe responsável pela API. O site público ainda precisa de revisão final após a publicação das alterações.

## 6. Links da documentação pública e do repositório

- **Repositório:** [github.com/NatanLuz/writechoice-taskflow-docs](https://github.com/NatanLuz/writechoice-taskflow-docs)
- **Documentação:** [write-choice-task-flow-docs.mintlify.site](https://write-choice-task-flow-docs.mintlify.site) — a versão final ainda precisa de revisão após a publicação das alterações.
