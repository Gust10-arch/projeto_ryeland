# Ryeland

Projeto acadêmico do IFCE Campus Aracati. Aplicação de gestão de ovinos e caprinos feita com Next.js (App Router) e banco de dados SQLite.

## Como executar

1. Instale o Node.js 20.9 ou superior.
2. Na pasta do projeto, rode `npm install`.
3. Rode `npm run dev`.
4. Abra http://localhost:3000 e entre em **Meu rebanho**.

## Banco de dados

Os dados ficam no arquivo `data/ryeland.db` (SQLite, via `better-sqlite3`). O arquivo e as tabelas são criados automaticamente na primeira execução, já com alguns animais e tarefas de exemplo. Para voltar ao estado inicial, pare o servidor e apague os arquivos `data/ryeland.db*`.

Tabelas: `animals`, `tasks` e `meta`.

## Rotas da API

| Método | Rota | Função |
| --- | --- | --- |
| GET | `/api/animals` | Lista os animais |
| POST | `/api/animals` | Cadastra um animal |
| DELETE | `/api/animals/:id` | Exclui um animal |
| GET | `/api/tasks` | Lista as tarefas da agenda |
| PATCH | `/api/tasks/:id` | Marca ou desmarca uma tarefa como concluída |

## Estrutura

- `app/` páginas e rotas da API
- `components/AnimalCard.tsx` cartão reutilizável, recebe `animal` e `onDetails` por props
- `lib/db.ts` conexão com o SQLite e consultas
- `src/App.tsx` interface principal; usa `.map()` para exibir um `AnimalCard` por animal

As páginas de logística, genética e clientes ainda usam dados de demonstração.
