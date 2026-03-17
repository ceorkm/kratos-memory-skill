# Kratos Memory Skill

Persistent memory for AI coding agents. Install this skill and your agent automatically saves bug fixes, architecture decisions, and project context across sessions.

## Install

```bash
npx skills add ceorkm/kratos-memory-skill
```

## What it does

Once installed, your AI agent will:

- **Check project memory at session start** — no more re-explaining your codebase
- **Save bug fixes** — what was wrong, why, and how it was fixed
- **Save architecture decisions** — what was chosen and why
- **Save rules** — "never push to main without PR" gets pinned and always surfaces
- **Save infrastructure details** — hosting, deployment, API endpoints
- **Recall context** — search and ask questions about prior sessions

## Requirements

The skill uses [kratos-memory](https://github.com/ceorkm/kratos-cli) CLI. If not installed, the agent will install it automatically:

```bash
npm install -g kratos-memory
```

## Compatible Agents

Works with any agent that supports skills:

Claude Code, Codex, Cursor, Cline, Windsurf, GitHub Copilot, Gemini CLI, Warp, Roo Code, Continue, and [28+ more](https://skills.sh).

## How it works

All data stays local — SQLite databases at `~/.kratos/`, zero network calls, 40ms per command. Each project is fully isolated with its own database.

## Links

- [kratos-memory CLI](https://github.com/ceorkm/kratos-cli) — the CLI tool
- [kratos-mcp](https://github.com/ceorkm/kratos-mcp) — MCP server (legacy)
- [skills.sh](https://skills.sh) — skill platform
