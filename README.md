# codex-statusline

Go command for Codex usage stats with two output modes:

- `pretty`: terminal dashboard rendered with Bubble Tea v2 + Lip Gloss v2
- `compact`: single-line output for Codex status line integration

## Build

```bash
cd /Users/pcong/Project/codex-statusline
go build -o ./bin/codex-statusline ./cmd/codex-statusline
```

## Run

Pretty mode is the default when stdout is a terminal:

```bash
./bin/codex-statusline
```

Force compact mode:

```bash
./bin/codex-statusline --mode compact
```

## Config

For Codex builds that support command-based status items:

```toml
[tui]
status_line = [
  { type = "command", command = "/Users/pcong/Project/codex-statusline/bin/codex-statusline --mode compact", ansi = false, timeout_ms = 1200 },
  "model-with-reasoning",
  "context-remaining",
  "current-dir"
]
```

## Environment

- `CODEX_USAGE_KEY`: optional explicit API key
- `CODEX_USAGE_URL`: optional endpoint override
- `CODEX_USAGE_MODE`: optional default mode (`auto`, `pretty`, `compact`)

If `CODEX_USAGE_KEY` is unset, the binary reads `OPENAI_API_KEY` from `~/.codex/auth.json`.
