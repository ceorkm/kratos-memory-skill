# Kratos Memory — Command Reference

## Table of Contents
- [Installation](#installation)
- [save](#save)
- [search](#search)
- [ask](#ask)
- [recent](#recent)
- [get](#get)
- [update](#update)
- [forget](#forget)
- [pin](#pin)
- [summary](#summary)
- [export](#export)
- [status](#status)
- [scan](#scan)
- [JSON Mode](#json-mode)
- [Project Isolation](#project-isolation)
- [Tags Convention](#tags-convention)

## Installation

```bash
# Global install (recommended — fastest, ~40ms per command)
npm install -g kratos-memory

# Or use npx (no install needed, slower first run)
npx kratos-memory@latest
```

After global install, use `kratos-memory` directly. With npx, prefix commands with `npx kratos-memory@latest`.

To check if installed: `kratos-memory --version`

## save

Store a memory with tags, file paths, and importance.

```bash
kratos-memory save "<text>" [options]
```

| Option | Description |
|--------|-------------|
| `-t, --tags <tags>` | Comma-separated tags |
| `-p, --paths <paths>` | Comma-separated file paths |
| `-i, --importance <1-5>` | Importance (default: 3) |
| `-c, --compress` | Compress before saving |
| `-j, --json` | JSON output |

**Importance:** 5=critical, 4=important, 3=normal, 2=minor, 1=low

**Examples:**
```bash
kratos-memory save "Auth uses JWT RS256, refresh in httpOnly cookies" --tags auth,security --importance 5 --paths src/auth.ts
kratos-memory save "Fixed crash in search — null check on empty results" --tags bug,fix --importance 4 --paths src/search.ts
```

## search

Find memories by keyword. Returns relevance percentage.

```bash
kratos-memory search "<query>" [-l limit] [-t tags] [-d] [--path-match] [-j]
```

## ask

Natural language question — synthesizes answer from matching memories.

```bash
kratos-memory ask "<question>" [-l limit] [-j]
```

## recent

Latest memories, newest first.

```bash
kratos-memory recent [-l limit] [--path-prefix <prefix>] [-j]
```

## get

Retrieve one memory by ID.

```bash
kratos-memory get <id> [-j]
```

## update

Edit a memory without delete + re-save.

```bash
kratos-memory update <id> "<new text>" [-t tags] [-i importance] [-p paths] [-j]
```

## forget

Delete a memory.

```bash
kratos-memory forget <id> [-j]
```

## pin

Pin = always surfaces first in search. For critical rules and context.

```bash
kratos-memory pin <id>
kratos-memory pin <id> --unpin
```

## summary

Project brief: pinned items, key decisions, topics, recent.

```bash
kratos-memory summary [-j]
```

## export

Dump all memories as JSON to stdout.

```bash
kratos-memory export > backup.json
```

## status

Dashboard: project, memory count, importance distribution, tags.

```bash
kratos-memory status [-j]
```

## scan

Detect secrets and PII before saving.

```bash
kratos-memory scan "<text>" [--redact] [-j]
```

Detects: SSN, credit cards, emails, API keys (sk-, ghp_, AKIA), JWTs, passwords.

## JSON Mode

All commands support `-j` / `--json` for machine-readable output.

## Project Isolation

Each project gets its own SQLite database. Detected from cwd by walking up for `.git`, `package.json`, `Cargo.toml`, `go.mod`, `pyproject.toml`.

## Tags Convention

| Tag | Use for |
|-----|---------|
| `bug`, `fix` | Bug found and fixed |
| `architecture` | System design |
| `decision` | Why X over Y |
| `security` | Auth, encryption |
| `database` | Schema, queries |
| `api` | Endpoints, patterns |
| `frontend` | UI, components |
| `backend` | Server, services |
| `infrastructure` | Hosting, deploy |
| `performance` | Optimizations |
| `rules` | Team standards |
