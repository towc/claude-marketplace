# Claude Plugin Marketplace

A curated collection of plugins for [Claude Code](https://claude.com/claude-code).

## Installation

### Quick Start

First, add this marketplace to Claude Code:

```bash
claude plugin marketplace add towc/claude-marketplace
```

Then install plugins:

```bash
claude plugin install boops
claude plugin install hide-hooks
```

## Available Plugins

### 🔊 Claude Boops
Add delightful sound feedback to Claude Code interactions.

- **Repository:** [towc/claude-boops](https://github.com/towc/claude-boops)
- **Installation:** `claude plugin install boops`
- **Features:**
  - 5 different sounds for different events
  - Interactive visual sound editor
  - Smart detection (success vs error)
  - Customizable frequencies, durations, and volumes

[Learn more →](./plugins/claude-boops.md)

### 🙈 Hide Hooks
Conditionally hide successful hook execution messages.

- **Repository:** [towc/claude-hide-hooks](https://github.com/towc/claude-hide-hooks)
- **Installation:** `claude plugin install hide-hooks`
- **Features:**
  - Simple patch/revert commands
  - Only hides successful messages, errors remain visible
  - Easy to restore with `/hide-hooks:revert`

[Learn more →](./plugins/claude-hide-hooks.md)

## Direct Installation (Alternative)

You can also clone plugins directly without the marketplace:

```bash
cd ~/.claude/plugins/marketplaces/
git clone https://github.com/towc/claude-boops.git
git clone https://github.com/towc/claude-hide-hooks.git
```

## Plugin Registry

All plugins are registered in [`plugins.json`](./plugins.json) for automated discovery and installation.

## Contributing

Have a plugin to add? Open a PR with:
1. Your plugin repository
2. A plugin description in `plugins/your-plugin.md`
3. An entry in `plugins.json`

## Author

Created by [@towc](https://github.com/towc)

## License

Individual plugins have their own licenses. See each plugin's repository for details.
