# Claude Code Configuration

## Configuration File Locations

Claude Code uses a hierarchical settings system:

### Global Settings
- **File**: `~/.claude/settings.json`
- **Scope**: Applies to all projects for the current user
- **Use**: Personal preferences and defaults

### Project Settings (Shared)
- **File**: `.claude/settings.json`
- **Scope**: Project-specific, checked into source control
- **Use**: Team-wide configuration

### Project Settings (Local)
- **File**: `.claude/settings.local.json`
- **Scope**: Project-specific, git-ignored
- **Use**: User-specific overrides within the project
- **Merge Behavior**: Native auto-merging with `.claude/settings.json`

## Settings Hierarchy

Settings are applied in order of precedence (highest to lowest):
1. Managed settings (organizational policies)
2. Project-shared (`.claude/settings.json`)
3. Project-local (`.claude/settings.local.json`)
4. Global (`~/.claude/settings.json`)

## Configuration Format

**Format**: JSON

### Example Settings Structure

```json
{
  "model": "claude-sonnet-4-20250514",
  "maxTokens": 4096,
  "permissions": {
    "allow": [
      "Bash(npm run lint)",
      "Bash(npm run test:*)",
      "Read(~/.zshrc)"
    ],
    "deny": [
      "Bash(curl:*)",
      "Read(./.env)",
      "Read(./.env.*)",
      "Read(./secrets/**)"
    ]
  },
  "hooks": {
    "SessionStart": [
      {
        "matcher": "startup",
        "hooks": [
          {
            "type": "command",
            "command": "$CLAUDE_PROJECT_DIR/.agents/polyfills/claude_agentsmd.sh"
          }
        ]
      }
    ],
    "PostToolUse": [
      {
        "matcher": "Write(*.py)",
        "hooks": [
          {
            "type": "command",
            "command": "python -m black $file"
          }
        ]
      }
    ]
  },
  "env": {
    "CLAUDE_CODE_ENABLE_TELEMETRY": "1"
  }
}
```

## AGENTS.md Integration

The universal-agents install script configures Claude Code to load AGENTS.md files via a SessionStart hook that:
1. Finds all AGENTS.md files in the project
2. Injects instructions for loading nested AGENTS.md files
3. Pre-loads root `./AGENTS.md` if it exists

## Sources

- [Claude Code Settings Documentation](https://code.claude.com/docs/en/settings)
- [Configuration Guide](https://claudelog.com/configuration/)
- [Developer's Guide to settings.json](https://www.eesel.ai/blog/settings-json-claude-code)
