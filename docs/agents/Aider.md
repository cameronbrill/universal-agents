# Aider Configuration

**Status**: Not yet supported by universal-agents install script

## Configuration File Locations

Aider looks for `.aider.conf.yml` files in multiple locations:

### Home Directory
- **File**: `~/.aider.conf.yml`
- **Scope**: User-wide, applies to all projects
- **Priority**: Lowest (loaded first)

### Git Repository Root
- **File**: `.aider.conf.yml`
- **Scope**: Project-wide, applies when running from within the git repo
- **Priority**: Medium (overrides home directory)

### Current Directory
- **File**: `.aider.conf.yml`
- **Scope**: Directory-specific
- **Priority**: Highest (overrides all others)

### Custom Config File
- **Flag**: `--config <filename>`
- **Behavior**: Only loads the specified file (bypasses default search)

## Settings Hierarchy

Files are loaded in order, with files loaded last taking priority:
1. Home directory (`~/.aider.conf.yml`)
2. Git repo root (`.aider.conf.yml`)
3. Current directory (`.aider.conf.yml`)

Later files override earlier ones.

## Configuration Format

**Format**: YAML

### Example Structure

```yaml
# Model configuration
model: gpt-4
edit-format: whole

# Files to include
read:
  - CONVENTIONS.md
  - AGENTS.md
  - README.md

# Editor settings
editor: vim

# Git settings
auto-commits: true
dirty-commits: false

# Linting
lint: true
```

### Alternative: .env Files

Aider also supports `.env` files for configuration via environment variables:
- `AIDER_MODEL=gpt-4`
- `AIDER_EDIT_FORMAT=whole`
- etc.

## Local Settings Support

**Note**: Aider does NOT support `.aider.local.conf.yml` files.

There is no mechanism for:
- Config file inclusion
- Wildcard config file loading
- `.local` variants

The hierarchy-based loading (home → git root → current dir) provides the override mechanism.

## Future Integration

When universal-agents adds Aider support, it will likely:
- Add AGENTS.md to the `read:` list in `.aider.conf.yml`
- Support project and global modes only (no local mode)
- Use YAML-specific merging utilities

## Sources

- [Aider Configuration Documentation](https://aider.chat/docs/config/aider_conf.html)
- [YAML Config File Guide](https://aider.chat/docs/config/aider_conf.html)
- [Sample Configuration](https://github.com/Aider-AI/aider/blob/main/aider/website/assets/sample.aider.conf.yml)
