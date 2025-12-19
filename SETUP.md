# Copilot Usage Tool - Setup Guide

## Installation

All files are now located in: `~/workspace/copilot-usage/`

### Option 1: Use the symlink (Recommended)

A symlink has been created at `~/bin/copilot-usage` pointing to the main script.

To use it:
```bash
~/bin/copilot-usage
```

To add it to your PATH for global access, add this line to your `~/.bashrc` or `~/.zshrc`:
```bash
export PATH="$HOME/bin:$PATH"
```

Then reload your shell:
```bash
source ~/.bashrc
# or
source ~/.zshrc
```

After that, you can use it from anywhere:
```bash
copilot-usage
```

### Option 2: Direct path

Run directly from the workspace:
```bash
~/workspace/copilot-usage/copilot-usage
```

### Option 3: Create an alias

Add this to your `~/.bashrc` or `~/.zshrc`:
```bash
alias copilot-usage='~/workspace/copilot-usage/copilot-usage'
```

Then reload your shell and use:
```bash
copilot-usage
```

---

## File Structure

```
~/workspace/copilot-usage/
├── copilot-usage          # Main script (executable)
├── README.md              # User guide and documentation
├── CHANGELOG.md           # Version history and updates
├── OUTPUT_EXAMPLE.md      # Example output format
└── SETUP.md              # This file
```

---

## Quick Start

1. First time setup (if needed):
```bash
~/bin/copilot-usage
```
When prompted, enter your GitHub token. It will be saved securely.

2. View your Copilot usage:
```bash
~/bin/copilot-usage
```

3. Check your usage for a different user:
```bash
~/bin/copilot-usage octocat
```

4. Reset your GitHub token:
```bash
~/bin/copilot-usage --reset-token
```

---

## Documentation

- **README.md** - Full user guide, features, authentication, troubleshooting
- **CHANGELOG.md** - What's new, version history, technical improvements
- **OUTPUT_EXAMPLE.md** - Visual examples of output formats

View any of these files:
```bash
cat ~/workspace/copilot-usage/README.md
cat ~/workspace/copilot-usage/CHANGELOG.md
```

---

## Token Storage

Your GitHub token is stored securely at:
```
~/.config/copilot-usage/github_token
```

The token file has restrictive permissions (`600`) and is never shared outside of GitHub's official API.

---

## Support

For detailed information, see:
- **README.md** - Full documentation
- **CHANGELOG.md** - Technical details and improvements

For issues with the GitHub API itself:
- [GitHub REST API Docs](https://docs.github.com/en/rest)
- [Creating PATs](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)
