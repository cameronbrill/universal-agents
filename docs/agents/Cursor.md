# Cursor CLI Configuration

**Status**: Not yet supported by universal-agents install script

## Configuration File Location

- **File**: `~/.cursor/cli-config.json`
- **Scope**: Global only (user-wide)

## Project-Level Configuration

Only **permissions** can be configured at the project level.
All other CLI settings must be set globally.

## Configuration Format

**Format**: JSON

### Example Structure

```json
{
  "version": 1,
  "editor": {
    "vimMode": false
  },
  "permissions": {
    "allow": ["Shell(ls)"],
    "deny": []
  }
}
```

## Rules Configuration (Separate System)

Cursor IDE has a separate rules system:
- **Project**: `.cursor/rules/*.mdc` files (new system)
- **Legacy**: `.cursorrules` in project root (deprecated)
- **Global**: User Rules via Cursor Settings

## Local Settings Support

**Note**: Cursor CLI does NOT support `.local.json` variants.
Project-level configuration is limited to permissions only.

## Future Integration

When universal-agents adds Cursor support, it will likely:
- Configure permissions via project-level settings
- Use rules system for AGENTS.md integration

## Sources

- [Cursor CLI Configuration Documentation](https://cursor.com/docs/cli/reference/configuration)
- [January 2026 Update](https://forum.cursor.com/t/cursor-cli-jan-8-2026-new-commands-and-performance-improvement/148372)
