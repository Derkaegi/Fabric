# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Fabric** is an open-source framework for augmenting humans using AI through organized prompts called "Patterns".

## Development Commands

```bash
# Build the project
go build -o fabric cmd/fabric/main.go

# Run tests
go test ./...

# Install locally
go install github.com/danielmiessler/fabric/cmd/fabric@latest

# Update patterns
fabric --updatepatterns

# Run setup
fabric --setup
```

## Architecture

- **Go-based CLI** with pattern management system
- **Patterns**: Located in `data/patterns/` - reusable AI prompts
- **Strategies**: Located in `data/strategies/` - prompt modification techniques
- **Completions**: Shell completion scripts in `completions/`
- **Web Interface**: SvelteKit app in `web/` directory

## Key Directories

- `cmd/fabric/` - Main CLI application
- `internal/` - Core Go packages
- `data/patterns/` - Community AI patterns
- `data/strategies/` - Prompt strategies
- `scripts/` - Installation and utility scripts
- `web/` - Web interface (requires npm/pnpm)

## Development Setup

1. Ensure Go 1.21+ is installed
2. Clone and build: `go build cmd/fabric/main.go`
3. Run setup: `./fabric --setup`
4. For web interface: `cd web && npm install && npm run dev`

## Testing

- Unit tests: `go test ./internal/...`
- Integration tests: Test CLI commands manually
- Pattern validation: `fabric --listpatterns`

## Related Configuration

- Uses global `~/.config/fabric/` for patterns and config
- Integrates with Claude Code via MCP servers
- Can be called from PAI hooks for pattern execution