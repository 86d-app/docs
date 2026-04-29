<p align="center">
  <a href="https://86d.app">
    <img src="https://86d.app/logo" height="96" alt="86d" />
  </a>
</p>

<p align="center">
  Dynamic commerce
</p>

<p align="center">
  <a href="https://x.com/86d_app"><strong>X</strong></a> ·
  <a href="https://www.linkedin.com/company/86d"><strong>LinkedIn</strong></a> ·
  <a href="https://github.com/86d-app/86d"><strong>GitHub</strong></a>
</p>
<br/>

> [!WARNING]
> 86d is under active development and is not ready for production use. Proceed with caution.

This directory hosts the [86d documentation site](https://86d.app/docs), built with [Mintlify](https://mintlify.com).

## Local development

```bash
npm i -g mint
mint dev
```

The dev server preview is available at `http://localhost:3000` and hot-reloads on file changes.

## Structure

- `docs.json`: Mintlify configuration and navigation.
- `index.mdx`: home page.
- `introduction.mdx`, `quickstart.mdx`, `deployment.mdx`: getting-started pages.
- `concepts/`: architecture, modules, templates, storefront, admin, agentic design.
- `configuration/`: `config.json`, environment variables, storage, authentication.
- `cli/`: CLI overview and command reference.
- `guides/`: how-to guides.
- `modules/`: reference page per module.
- `operations/`: security, testing, observability, troubleshooting.
- `resources/`: glossary, FAQ, versioning, contributing, changelog.
- `mcp.mdx`: the docs MCP server.

## Contributing

See [Contributing](https://86d.app/docs/resources/contributing).
