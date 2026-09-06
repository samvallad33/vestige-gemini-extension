# Vestige

Local-first Rust MCP memory for this Gemini CLI session. Data stays on this machine. This extension is for local and synthetic use, not a hosted production service.

## Tools (only these)

- **recall** — retrieve prior decisions, preferences, and related memories.
- **smart_ingest** — store a memory with duplicate and contradiction handling.
- **backfill** — Causal Backfill: walk backward from a failure to the earlier memory that caused it.

Do not invent other Vestige tool names.

## Store

Default store is the OS per-user data directory. There is no `--project` flag. For a per-project store, override the MCP server in `settings.json` with `--data-dir` or set `VESTIGE_DATA_DIR`. `--data-dir` wins.

Never ingest secrets, API keys, passwords, or tokens.

This extension pins vestige-mcp-server@2.8.0.
