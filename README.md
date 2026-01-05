# AGENTS.md for Popular Coding Agents

Full-featured AGENTS.md support for Claude Code, Gemini CLI, and more.

## Installation

```bash
curl -fsSL https://raw.githubusercontent.com/agentsmd/universal-agents/main/install.sh | sh
```

## What This Does

Configures your installed AI coding agents with complete [AGENTS.md](https://agents.md) support:

- **AGENTS.md as context** - Agents automatically load AGENTS.md files instead of (or in addition to) their proprietary formats
- **Hierarchical inheritance** - Nested AGENTS.md files apply with proper precedence (closer = higher priority)
- **Smart loading** - Only loads relevant AGENTS.md files, not all of them (essential for large monorepos)

### How It Works

**Claude Code:** SessionStart hook that implements AGENTS.md with no CLAUDE.md files or symlinks needed

**Gemini CLI:** Native configuration pointing to AGENTS.md in addition to GEMINI.md

## Usage

Create AGENTS.md files anywhere in your project. They'll be loaded automatically with proper scoping:

```
project/
├── AGENTS.md              # Applies project-wide
└── src/
    └── api/
        └── AGENTS.md      # Applies to API work (overrides project-wide)
```

When working in `src/api/`, both AGENTS.md files apply - with the API-specific one taking precedence for conflicts.

Agents load context only for the directories you're working in, keeping token usage efficient even in large projects.
