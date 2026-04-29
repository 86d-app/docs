# Documentation site instructions for AI agents

This file briefs AI agents on how to work in `docs/`. It is short by design.

## Project shape

- Mintlify documentation site for [86d](https://86d.app).
- Pages are MDX files with YAML frontmatter.
- Configuration lives in `docs.json`.
- Run `mint dev` to preview locally.
- Run `mint broken-links` to check links.

## Editing rules

- **Always run from the docs/ directory** for Mintlify commands.
- **Every page must have `title` and `description`** in frontmatter. Both are required.
- **Sentence case for headings.** "Module configuration", not "Module Configuration".
- **Use "you", not "the user".**
- **Active voice. Short sentences. One idea per sentence.**
- **No em dashes and no en dashes misused as em dashes.** This is a hard rule. Use a comma, a colon, a semicolon, parentheses, or a sentence break. We grep for them in CI.
- **Bold for UI elements** (`Click **Settings**`).
- **Code formatting** for file paths, command names, environment variables, and identifiers. Not for prose emphasis.
- **Internal links** are root-relative paths without the `.mdx` extension (`/concepts/modules`).

## Source of truth

The 86d framework lives in `../` (sibling to `docs/`). The docs must agree with that source code. Specifically:

- CLI commands, flags, and behavior: `../packages/cli/src/`.
- Module names, options, and contracts: `../modules/<name>/src/` and `../registry.json`.
- Environment variables: `../.env.example`.
- Template structure: `../templates/<name>/`.

Before claiming a feature exists or works a particular way, verify in the framework source.

## Common tasks

### Add a new module page

1. Confirm the module exists in `../modules/<name>/` and `../registry.json`.
2. Create `modules/<name>.mdx` with frontmatter (`title`, `description`).
3. Add the page to the appropriate group in `docs.json` -> `tabs[Modules].groups[...].pages`.
4. Cross-link from related pages.

### Update a CLI command reference

1. Read the actual command in `../packages/cli/src/commands/<name>.ts`.
2. Update `cli/commands.mdx` to match flags, sub-commands, and behavior.
3. If the change adds or removes a top-level command, also update `cli/overview.mdx`.

### Run health checks

```bash
mint broken-links                                                                        # internal links
python3 -c "import re,sys,glob;[sys.exit(1) for f in glob.glob('**/*.mdx',recursive=True) if re.search('[\\u2013\\u2014]',open(f).read())]"  # must return 0
```

## What not to touch

- `LICENSE`.
- `.git/`.
- Files in `..` (the framework). Treat the parent repo as read-only when working in `docs/`.

## Reporting back

Surface a brief change summary at the end of any PR-shaped task: changed files (one line each), new pages created, gaps left for a maintainer, and any open questions.
