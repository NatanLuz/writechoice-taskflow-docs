# TaskFlow API Documentation

A documentation site built with Mintlify. The `openapi.yaml` specification is the source of truth for API contracts and powers the interactive reference configured in `docs.json`.

## Preview locally

Install Node.js. From the project root, where `docs.json` is located, run:

```bash
npx --yes mint dev
```

This command opened the local preview before the English translation. The translated files have not yet been previewed. On Windows with Node.js 24, the preview tool may fail intermittently with an error related to `p-cancelable`. When it starts successfully, open the address reported by the CLI, usually `http://localhost:3000`.

## Validate the documentation

To validate the Mintlify project structure and content, run:

```bash
npx mintlify validate
```

The Portuguese documentation previously passed validation with this command. The English translation has not yet been validated. Mintlify validation checks the local documentation; it does not send requests to the TaskFlow API or replace real endpoint tests. API tests require separate HTTP requests with valid credentials and are not part of the commands above.

## Project structure

- `index.mdx`: overview and workflow.
- `quickstart.mdx`: end-to-end workflow using cURL.
- `authentication.mdx`: secure use of Bearer authentication.
- `errors.mdx`: documented errors and limitations.
- `openapi.yaml`: contracts and examples for the five operations, referenced by Mintlify navigation.
- `docs.json`: site identity, navigation, and playground configuration.

`openapi.backup.yaml` is a backup copy and is listed in `.gitignore` to keep Git from tracking it. It is also listed in `.mintignore`, which controls what Mintlify ignores when processing or publishing documentation. These files apply to separate workflows; `.mintignore` does not replace `.gitignore`.

## Maintenance

- Update the contracts in `openapi.yaml` when the API changes, and keep the guides consistent with the specification.
- Use placeholders in public examples; never include real API keys or sensitive data.
- Review navigation and links when renaming or adding pages.
- Before publishing, run `npx mintlify validate` and check the preview with `npx --yes mint dev`.
- Publishing depends on the repository integration and Mintlify deployment workflow configured for this project. Review the published site after deployment.
