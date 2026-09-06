# Vestige Gemini CLI extension

Gemini CLI extension for [Vestige](https://github.com/samvallad33/vestige) — local-first Rust MCP memory with Causal Backfill.

This repo is a **public GitHub extension**, not a hosted production service. It declares an `mcpServers` entry that launches `vestige-mcp-server@2.8.0` on your machine and exposes three tools: `recall`, `smart_ingest`, `backfill`.

## Install

```bash
npm install -g vestige-mcp-server@2.8.0
gemini extensions install https://github.com/samvallad33/vestige-gemini-extension
```

Requires [Gemini CLI](https://github.com/google-gemini/gemini-cli), `git`, and Node.js. Restart the CLI session after install.

Direct MCP equivalent:

```bash
gemini mcp add vestige -- npx -y vestige-mcp-server@2.8.0
```

If `vestige-mcp` is already on `PATH`, GUI / config-file clients should use its **absolute** path from `which vestige-mcp` (macOS / Linux) or `where vestige-mcp` (Windows), not a bare command name.

Update later with:

```bash
gemini extensions update vestige
```

Uninstall:

```bash
gemini extensions uninstall vestige
```

## What you get

| Tool | Role |
|---|---|
| `recall` | Retrieve prior decisions, preferences, and related memories. |
| `smart_ingest` | Write memories with duplicate / contradiction handling. |
| `backfill` | Causal Backfill: reach backward from a failure to the older memory that caused it. |

Memories stay in a local SQLite store. Default location is the OS per-user data directory. There is **no** `--project` flag. Isolate a repo with `--data-dir` by overriding the server in `settings.json`, or set `VESTIGE_DATA_DIR`. `--data-dir` wins over the env var.

## Requirements

- Node.js (for `npm install -g vestige-mcp-server@2.8.0`)
- Gemini CLI with extensions support
- Prebuilt server binaries in `2.8.0` for macOS (Apple Silicon and Intel), Linux x86_64 (Ubuntu 22.04, Debian 12, and newer), and Windows x86_64

First launch may download an embedding model (~130MB). Later runs do not need the network.

This wrapper is for **local and synthetic** use. It is not a production hosted memory service.

## Layout

```
gemini-extension.json   MCP launch: npx -y vestige-mcp-server@2.8.0
GEMINI.md               tool guidance loaded as extension context
```

Schema: [Gemini CLI extension reference](https://geminicli.com/docs/extensions/reference/).

## License

MIT for this wrapper. The launched server (`vestige-mcp-server`) is AGPL-3.0; see [samvallad33/vestige](https://github.com/samvallad33/vestige).
