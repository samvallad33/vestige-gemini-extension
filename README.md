# Vestige Gemini CLI extension

Gemini CLI extension for [Vestige](https://github.com/samvallad33/vestige) — local-first Rust MCP memory with Causal Backfill.

This repo is a **public GitHub extension**, not a hosted production service. It declares an `mcpServers` entry that launches `vestige-mcp-server@2.3.0` on your machine and exposes three tools: `recall`, `smart_ingest`, `backfill`.

## Install

```bash
gemini extensions install https://github.com/samvallad33/vestige-gemini-extension
```

Requires [Gemini CLI](https://github.com/google-gemini/gemini-cli), `git`, and Node.js (`npx`). Restart the CLI session after install.

Direct MCP equivalent:

```bash
gemini mcp add vestige -- npx -y vestige-mcp-server
```

If `vestige-mcp` is already on `PATH`, GUI / config-file clients should use its **absolute** path, not a bare command name.

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

- Node.js (for `npx -y vestige-mcp-server@2.3.0`)
- Gemini CLI with extensions support
- Prebuilt server binaries in `2.3.0` for macOS (Apple Silicon and Intel), Linux x86_64, and Windows x86_64
- **Ubuntu 22.04 and Debian 12:** wait for `vestige-mcp-server` **v2.4.0**

First launch may download an embedding model (~130MB). Later runs do not need the network.

This wrapper is for **local and synthetic** use. It is not a production hosted memory service.

## Layout

```
gemini-extension.json   MCP launch: npx -y vestige-mcp-server@2.3.0
GEMINI.md               tool guidance loaded as extension context
```

Schema: [Gemini CLI extension reference](https://geminicli.com/docs/extensions/reference/).

## License

MIT for this wrapper. The launched server (`vestige-mcp-server`) is AGPL-3.0; see [samvallad33/vestige](https://github.com/samvallad33/vestige).
