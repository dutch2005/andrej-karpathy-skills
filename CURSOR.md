# Using this repo with Cursor, Kilo, and Codex CLI

This project includes behavioral guidelines in formats for multiple AI coding tools.

## Cursor

This project includes a **Cursor project rule** so the guidelines apply automatically when you open this repo in Cursor.

1. Open the folder in Cursor.
2. The rule [`.cursor/rules/karpathy-guidelines.mdc`](.cursor/rules/karpathy-guidelines.mdc) is committed with `alwaysApply: true`, so you do not need extra installation steps.
3. In Cursor, you can confirm it under **Settings → Rules** (or the project rules UI), where `karpathy-guidelines` should appear.

### Use in another Cursor project

Copy `.cursor/rules/karpathy-guidelines.mdc` into that project's `.cursor/rules/` directory (create the folders if needed). Adjust or merge with existing rules as you like.

### Personal Agent Skills

If you want the same content as a reusable skill under `~/.cursor/skills`, use [`skills/karpathy-guidelines/SKILL.md`](skills/karpathy-guidelines/SKILL.md). Copy or symlink it into your personal skills directory.

## Kilo

Kilo reads `AGENTS.md` at project root and supports a rules directory at `.kilo/rules/*.md`.

### Use in this repo

- **[`AGENTS.md`](AGENTS.md)** is committed at the repo root — the cross-tool standard that Kilo auto-discovers.
- **[`.kilo/rules/karpathy-guidelines.md`](.kilo/rules/karpathy-guidelines.md)** is committed in the Kilo rules directory for projects that use `kilo.jsonc`'s `instructions` array.

Both are ready to use — open the folder in Kilo and the guidelines load automatically.

### Use in another Kilo project

**Option A: AGENTS.md (auto-discovered)**

```bash
curl -o AGENTS.md https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/AGENTS.md
```

**Option B: Rules directory (via kilo.jsonc)**

```bash
mkdir -p .kilo/rules
curl -o .kilo/rules/karpathy-guidelines.md https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/.kilo/rules/karpathy-guidelines.md
```

Then add to your `kilo.jsonc`:

```jsonc
{
  "instructions": [".kilo/rules/karpathy-guidelines.md"]
}
```

## OpenAI Codex CLI

Codex CLI reads `AGENTS.md` at project root as its primary instruction file.

### Use in this repo

**[`AGENTS.md`](AGENTS.md)** is committed — Codex CLI loads it automatically when you open the repo.

### Use in another Codex CLI project

```bash
curl -o AGENTS.md https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/AGENTS.md
```

Or install globally:

```bash
curl -o ~/.codex/AGENTS.md https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/AGENTS.md
```

## Tool compatibility matrix

| Tool | Auto-discovered file | Additional config |
|------|---------------------|-------------------|
| Claude Code | `CLAUDE.md` | Plugin: `/plugin marketplace add` + `/plugin install` |
| Cursor | `.cursor/rules/*.mdc` with `alwaysApply: true` | — |
| Kilo | `AGENTS.md` | `.kilo/rules/*.md` via `kilo.jsonc` |
| Codex CLI | `AGENTS.md` | `~/.codex/AGENTS.md` for global install |

## For contributors

When you change the four principles, keep all of these in sync:

- **[`CLAUDE.md`](CLAUDE.md)** — Claude Code per-project file
- **[`AGENTS.md`](AGENTS.md)** — Cross-tool standard (Kilo, Codex CLI)
- **[`.cursor/rules/karpathy-guidelines.mdc`](.cursor/rules/karpathy-guidelines.mdc)** — Cursor project rule
- **[`.kilo/rules/karpathy-guidelines.md`](.kilo/rules/karpathy-guidelines.md)** — Kilo rules file
- **[`skills/karpathy-guidelines/SKILL.md`](skills/karpathy-guidelines/SKILL.md)** — Reusable skill definition
