# Gemini CLI Configuration

## Configuration File Locations

Gemini CLI uses a four-tier configuration system:

### System Defaults
- **File**: `/etc/gemini-cli/system-defaults.json` (Linux)
- **File**: `C:\ProgramData\gemini-cli\system-defaults.json` (Windows)
- **File**: `/Library/Application Support/GeminiCli/system-defaults.json` (macOS)
- **Scope**: System-wide default settings
- **Override**: Can be overridden via `GEMINI_CLI_SYSTEM_DEFAULTS_PATH` env var

### Global Settings
- **File**: `~/.gemini/settings.json`
- **Scope**: User-specific, applies to all projects
- **Use**: Personal preferences

### Project Settings
- **File**: `.gemini/settings.json`
- **Scope**: Project-specific
- **Use**: Team-wide project configuration

### System Overrides
- **File**: `/etc/gemini-cli/settings.json` (Linux)
- **File**: `C:\ProgramData\gemini-cli\settings.json` (Windows)
- **File**: `/Library/Application Support/GeminiCli/settings.json` (macOS)
- **Scope**: System-wide overrides (highest precedence)
- **Override**: Can be overridden via `GEMINI_CLI_SYSTEM_SETTINGS_PATH` env var

## Settings Hierarchy

Settings are applied in order of precedence (highest to lowest):
1. System overrides (`/etc/gemini-cli/settings.json`)
2. Project (`.gemini/settings.json`)
3. User (`~/.gemini/settings.json`)
4. System defaults (`/etc/gemini-cli/system-defaults.json`)

## Configuration Format

**Format**: JSON

### Example Settings Structure

```json
{
  "context": {
    "fileName": ["AGENTS.md", "GEMINI.md"]
  },
  "model": "gemini-2.0-flash-exp",
  "git": {
    "respectGitignore": true
  }
}
```

## Environment Variable Interpolation

String values in `settings.json` can reference environment variables:
- `$VAR_NAME` or `${VAR_NAME}` syntax
- Variables are resolved when settings are loaded

## Local Settings Support

**Note**: Gemini CLI does NOT natively support `.gemini/settings.local.json` files.

The documented hierarchy only includes the four tiers listed above. Unlike Claude Code, there is no auto-merging of `.local.json` variants.

## AGENTS.md Integration

The universal-agents install script configures Gemini CLI to load AGENTS.md files via the `context.fileName` setting, which tells Gemini to automatically include these files in the conversation context.

## Sources

- [Gemini CLI Configuration Documentation](https://geminicli.com/docs/get-started/configuration/)
- [GitHub Configuration Guide](https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/configuration.md)
- [Tutorial: Configuration Settings](https://medium.com/google-cloud/gemini-cli-tutorial-series-part-3-configuration-settings-via-settings-json-and-env-files-669c6ab6fd44)
