# OpenAI Codex CLI Configuration

**Status**: Not yet supported by universal-agents install script

## Configuration File Location

- **File**: `~/.codex/config.toml`
- **Scope**: Global only (user-wide)
- **Shared**: CLI and IDE extension use the same config file

## Configuration Format

**Format**: TOML

### Example Structure

```toml
[features]
shell_snapshot = true
web_search_request = true

[analytics]
enabled = true

[tui]
scroll_speed = 1.0

[profiles.default]
model = "gpt-4"
provider = "openai"

[approval]
policy = "prompt"

[sandbox]
mode = "container"
```

### Key Configuration Sections

1. **Features**: Enable/disable CLI features
2. **Analytics**: Control analytics behavior
3. **TUI**: Terminal UI settings (scroll behavior, etc.)
4. **Profiles**: Model and provider configuration
5. **Approval**: Approval policies for commands
6. **Sandbox**: Shell environment policies

## Command-Line Overrides

Any `-c key=value` overrides passed at the command line take precedence for that invocation:
```sh
codex -c features.shell_snapshot=false
```

## Project-Level Configuration

**Note**: Codex natively only supports global configuration in `~/.codex/config.toml`.

There is no documented project-level config file support.

## Future Integration

When universal-agents adds Codex support, it will likely:
- Create TOML-specific utilities for config merging
- Support global mode primarily
- Potentially extend with project-level config (`.codex/config.toml`)

## Sources

- [Codex CLI Documentation](https://developers.openai.com/codex/cli/)
- [GitHub Repository](https://github.com/openai/codex)
- [Comprehensive Setup Guide](https://smartscope.blog/en/generative-ai/chatgpt/openai-codex-cli-comprehensive-guide/)
