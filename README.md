# AGENTS.md for Popular Coding Agents

Configure Claude Code, Gemini CLI, and other agents to use AGENTS.md.

## Installation

```bash
curl -fsSL https://raw.githubusercontent.com/agentsmd/universal-agents/main/install.sh | sh
```

## What This Does

Configures your installed AI coding agents to recognize [AGENTS.md](https://agents.md).

### Claude Code

Adds a SessionStart hook that implements AGENTS.md support:
- **Hierarchical inheritance** - Nested AGENTS.md files automatically apply with proper precedence
- **On-demand loading** - Loads context only as you work in relevant directories (minimizes token usage)
- **No extra files** - No CLAUDE.md files or symlinks needed

### Gemini CLI

Configures Gemini to look for AGENTS.md in addition to GEMINI.md files.

## Usage

After installation, create `AGENTS.md` in your project:

```markdown
# AGENTS.md

## Standards
- TypeScript strict mode
- Run `npm test` before committing

## Architecture
- API routes in `/src/api`
- Components in `/src/components`
```

Your agents will load it automatically.

### Nested AGENTS.md

Create scoped instructions for specific directories:

```
project/
├── AGENTS.md              # Project-wide
└── src/
    └── api/
        └── AGENTS.md      # API-specific (overrides project-wide)
```

## CLI

```bash
./install.sh              # Configure all installed agents
./install.sh claude       # Claude only
./install.sh gemini       # Gemini only
./install.sh -n          # Dry run (preview changes)
```
