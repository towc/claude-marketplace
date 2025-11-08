# 🔊 Claude Boops

Add delightful sound feedback to Claude Code interactions.

## Overview

Claude Boops enhances your Claude Code experience by adding customizable sound feedback for different events. Each interaction gets its own distinct sound, making it easier to track what's happening even when you're not looking at the screen.

## Features

- **5 Different Sounds** for different event types:
  - User Submit (when you press enter)
  - Permission Prompts (when Claude needs approval)
  - Questions (multiple choice prompts)
  - Success (normal completions)
  - Error (failures)

- **Interactive Visual Editor**
  - Drag-to-edit interface
  - Real-time preview
  - Logarithmic frequency control
  - Auto-save functionality

- **Smart Detection**
  - Different sounds for success vs error completions
  - Skips redundant sounds (e.g., won't play success after a question)
  - Intelligent event detection

- **Customization**
  - Adjust frequency, duration, and volume for each tone
  - Support for multi-tone sequences
  - Share configurations via JSON

## Installation

First, add the marketplace:

```bash
claude plugin marketplace add towc/claude-marketplace
```

Then install the plugin:

```bash
claude plugin install boops
```

The plugin works immediately after installation - sounds are generated dynamically from config.json.

## Usage

### Customizing Sounds

Open the visual editor:

```bash
/boops:settings
```

This will:
1. Start a sound server on port 8765
2. Open the visual editor in your browser
3. Allow you to customize frequency, duration, and volume
4. Auto-save changes to config.json

### Using Custom Sound Files

Instead of generated tones, you can use your own `.wav` files by placing them in the plugin directory with these names:
- `user-submit.wav`
- `permission-needed.wav`
- `question.wav`
- `completion-success.wav`
- `completion-error.wav`

## Technical Details

**How it works:**
- Uses Claude Code hooks to detect events
- Generates WAV files on-the-fly using pure JavaScript
- Plays sounds using `paplay` (Linux) or system default player
- Exclusive playback prevents sound overlap

**Requirements:**
- Linux with `paplay` (PulseAudio) or macOS
- Node.js for the visual editor
- Port 8765 available for the editor server

## Troubleshooting

**No sounds playing?**
- Check hooks are installed: `cat ~/.claude/settings.json | jq .hooks`
- Verify scripts are executable
- Check logs: `/tmp/claude-sound.log`

**Sound server won't start?**
- Make sure port 8765 is available: `lsof -i :8765`
- Check Node.js is installed: `node --version`

## Companion Plugins

- **[Hide Hooks](./claude-hide-hooks.md)** - Hide successful hook execution messages

```bash
claude plugin install hide-hooks
```

## Links

- **Repository:** https://github.com/towc/claude-boops
- **Issues:** https://github.com/towc/claude-boops/issues
- **Author:** [@towc](https://github.com/towc)

## License

MIT License - See repository for details
