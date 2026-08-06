---
name: write-commit-messages
description: Use when the user asks for a commit message
---

# Write commit messages

Draft git commit messages based on staged changes, adhering to Conventional Commits prefixes and the 50/72 character limits for subjects and bodies. The following are detailed guidelines.

## Format (50/72)

```
<type>(<optional scope>): <subject>   # ≤ 50 characters

<optional body>                       #wrap lines at 72 characters

<optional footer(s)>
```

| Part           | Rule                                                                                                                       |
| -------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Subject**    | One line, **≤ 50 characters** (type + scope + summary combined). Imperative mood ("add", not "added"). No trailing period. |
| **Blank line** | Required between subject and body.                                                                                         |
| **Body**       | Optional. Explain **why**, not what the diff already shows. **Wrap at 72 characters** per line.                            |

Count the full subject line toward the 50-character limit, e.g. `feat(ui): add recent searches row` (34 chars).

### Allowed types

Use [Conventional Commits](https://www.conventionalcommits.org/) prefixes:

| Type       | When to use                                                                            |
| ---------- | -------------------------------------------------------------------------------------- |
| `feat`     | New user-facing behavior or capability                                                 |
| `fix`      | Bug fix                                                                                |
| `docs`     | README, comments, or other human-facing documentation only                             |
| `style`    | Formatting, whitespace, semicolons — no logic change                                   |
| `refactor` | Code change that is neither a fix nor a feature                                        |
| `perf`     | Performance improvement                                                                |
| `test`     | Adding or updating tests                                                               |
| `build`    | Build system or dependencies (Vite, npm, bundler config)                               |
| `ci`       | CI/CD workflows (`.github/workflows/`)                                                 |
| `ai-infra` | **Changes to AI-agent-facing files** (see [below](#ai-infra--agent-facing-files-only)) |
| `chore`    | Maintenance that doesn't fit above (tooling config, `.gitignore`)                      |

Optional scope in parentheses narrows the area: `feat(ui): …`, `fix(download): …`.

### `ai-infra` — agent-facing files only

Use **`ai-infra`**, not `docs` or `chore`, when the commit mainly changes files intended to guide AI agents:

- `AGENTS.md`
- `.agents/skills/**`
- `.agents/rules/**` (if present)

Human-facing docs (`README.md`, code comments) still use `docs`.

## When no changes are staged

Do not make assumptions—stop and ask the user to stage the files, or propose which changes should be staged.

## Combined feature and documentation updates

When a commit includes a feature change along with its corresponding documentation update, use **`feat`** as the commit type and mention the document update in the `<optional body>`.

## When unsure about the type

**Never guess**. If your changes are mixed or unclear:

- If there is a feature change accompanied by a documentation update, use `feat` and mention the doc update in the `<optional body>`.
- Stop and evaluate the categories involved.
- Suggest staging a representative selection of files from the overall set if the prefix remains uncertain.
- Suggest partial staging for complex files.
