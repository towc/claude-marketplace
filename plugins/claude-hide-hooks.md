# 🙈 Hide Hooks

Conditionally hide successful hook execution messages in Claude Code.

## Overview

This plugin addresses the common complaint in [Issue #9603](https://github.com/anthropics/claude-code/issues/9603) where "hook succeeded" messages clutter the terminal, making it hard to track actual output.

## What It Does

**Hides:**
- ✅ Successful hook execution messages (e.g., "hook succeeded: Success")

**Keeps Visible:**
- ❌ Error messages and failures
- ❌ Important hook feedback
- ❌ Does NOT affect Claude's ability to receive hook data

## Features

- **Automatic Installation**
  - Patch applied automatically when plugin is installed
  - No manual commands needed
  - Auto-reverts on uninstallation

- **Environment Variable Control**
  - Hide by default
  - Show with `SHOW_CLAUDE_HOOKS=true`
  - Perfect for debugging

- **Safe Patching**
  - Creates backup before patching
  - Easy to revert
  - Only modifies UI rendering, not functionality

## Installation

First, add the marketplace:

```bash
claude plugin marketplace add towc/claude-marketplace
```

Then install the plugin:

```bash
claude plugin install hide-hooks
```

**That's it!** The patch is applied automatically.

## Usage

### Default Behavior (Hooks Hidden)

```bash
claude
```

Hook messages are hidden by default, giving you a cleaner terminal.

### Show Hooks When Debugging

```bash
SHOW_CLAUDE_HOOKS=true claude
```

### Permanent Visibility

Add to your shell profile (`.bashrc`, `.zshrc`, etc.):

```bash
export SHOW_CLAUDE_HOOKS=true
```

### Manual Patch (Optional)

If you need to re-apply the patch:

```bash
/hide-hooks
```

## How It Works

The plugin patches the Claude binary by wrapping the hook success message rendering in a conditional check:

```javascript
// Before:
return createElement(/* hook success message */);

// After:
return process.env.SHOW_CLAUDE_HOOKS === 'true'
  ? createElement(/* hook success message */)
  : null;
```

This allows toggling visibility with an environment variable without re-patching.

## Reverting

### Automatic (Recommended)

```bash
claude plugin uninstall hide-hooks
```

The patch is automatically reverted on uninstallation.

### Manual

```bash
# If sudo was required:
sudo cp ~/.local/bin/claude.bak.js ~/.local/bin/claude.js

# Otherwise:
cp ~/.local/bin/claude.bak.js ~/.local/bin/claude.js
```

## Important Notes

⚠️ **Warning:** This modifies the Claude binary and is **unsupported by Anthropic**.

- Future Claude updates will overwrite this patch
- You'll need to reinstall the plugin after updating Claude
- The patch only affects UI rendering, not functionality
- Hook errors and important messages remain visible

## Related Issues

- [#9603](https://github.com/anthropics/claude-code/issues/9603) - Turn off hook succeeded messages
- [#3060](https://github.com/anthropics/claude-code/issues/3060) - Fix unnecessary printing after successful hook execution
- [#8990](https://github.com/anthropics/claude-code/issues/8990) - Hook Messages Overwriting Command Output

## Companion Plugins

- **[Claude Boops](./claude-boops.md)** - Add sound feedback to Claude Code

## Links

- **Repository:** https://github.com/towc/claude-hide-hooks
- **Issues:** https://github.com/towc/claude-hide-hooks/issues
- **Author:** [@towc](https://github.com/towc)

## License

MIT License - See repository for details
