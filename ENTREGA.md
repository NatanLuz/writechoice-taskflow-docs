# Technical Writing Test Submission — TaskFlow API

## 1. Delivery overview

This submission organizes the TaskFlow API documentation to help new users get started, understand the operation contracts, and troubleshoot errors. The documentation is written in English and uses the OpenAPI specification as the source of truth for endpoints, parameters, schemas, and responses.

## 2. Documentation process

I began by reading `openapi.yaml` in full and reviewing `docs.json`, `index.mdx`, `quickstart.mdx`, `README.md`, and `.mintignore`. I then organized the Mintlify navigation, replaced the generic Starter Kit content, and aligned the guides with the specification.

Examples use placeholders for API keys and IDs. The documentation explains Bearer authentication and notes that the first request may take up to 60 seconds when the server is idle. Before this English translation, the Portuguese documentation passed `npx mintlify validate` and was previewed locally with Mintlify. The English changes have not yet been validated or previewed.

## 3. Structure and content decisions

- **Overview:** introduces the API, explains the project and task workflow, and points readers to the next steps.
- **Quickstart:** walks through the main workflow with cURL examples: create a project, create a task, list tasks, update a task, and delete it.
- **Authentication guide:** explains the Bearer header and how to protect API keys in examples and everyday use.
- **OpenAPI reference:** centralizes the five endpoint contracts and keeps the reference connected to the specification to avoid manually duplicating technical details.
- **Errors page:** summarizes documented status codes, suggests checks, and records known dependencies and limitations.

## 4. Real API tests

Manual tests were performed on **October 22, 2026 (UTC)** using cURL in Windows CMD. All five endpoints passed the main workflow:

| Endpoint | HTTP | Result |
| --- | ---: | --- |
| `POST /projects` | `201` | Project created successfully. |
| `POST /tasks` | `201` | Task created with status `pending`. |
| `GET /projects/{project_id}/tasks` | `200` | Returned `total: 1` and the created task. |
| `PATCH /tasks/{task_id}` | `200` | Status updated to `in_progress`. |
| `DELETE /tasks/{task_id}` | `200` | API confirmed the deletion. |

The API required Bearer authentication. Error scenarios were not tested comprehensively, so this table reports only the main workflow results.

### Published playground verification

On **October 22, 2026**, the five endpoints were also run through the interactive playground on the public site:

| Endpoint | Observed HTTP status | Result |
| --- | ---: | --- |
| `POST /projects` | `201 Created` | Project created; `project_id` returned. |
| `POST /tasks` | `201 Created` | Task created in the project with status `pending`; `task_id` returned. |
| `GET /projects/{project_id}/tasks` | `200 OK` | Returned `total: 1` and the created task. |
| `PATCH /tasks/{task_id}` | `200 OK` | Status changed from `pending` to `in_progress`; task identity was preserved. |
| `DELETE /tasks/{task_id}` | `200 OK` | API confirmed deletion of the test task. |

## 5. Challenges and possible improvements

The OpenAPI specification provides response examples but does not mark response schema fields as required. The documentation therefore does not present these fields as required beyond what the contract states. The specification also does not define pagination, filters, or rate limits, so these features were not assumed.

The first `POST /projects` attempt through the playground resulted in an HTTP `524` timeout from the request intermediary. The operation was retried later and completed with `201 Created`; no cause was determined.

As next steps, I recommend systematically testing error scenarios and reviewing response examples with the API team. The site was published and accessed in a Brave private window, confirming public access without authentication. The **Create a project** page (`POST /projects`) was visually inspected, and the API reference navigation displayed all five endpoints in Portuguese at the time of that inspection. This English translation has not yet been published.

## 6. Public documentation and repository links

- **Repository:** [github.com/NatanLuz/writechoice-taskflow-docs](https://github.com/NatanLuz/writechoice-taskflow-docs)

- **Documentation:** [write-choice-task-flow-docs.mintlify.site](https://write-choice-task-flow-docs.mintlify.site)
