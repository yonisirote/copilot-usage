# copilot-usage

CLI tool to fetch and display your GitHub Copilot usage statistics.

## Quick Start

### Install

```bash
git clone https://github.com/yonisirote/copilot-usage.git
cp copilot-usage/copilot-usage ~/bin/
chmod +x ~/bin/copilot-usage
```

Or add `~/bin` to PATH in `~/.bashrc`:
```bash
export PATH="$HOME/bin:$PATH"
```

### Get Your GitHub Token

1. Visit: https://github.com/settings/tokens
2. Generate a new token (classic or fine-grained)
3. Grant `Plan` (read-only) permissions
4. Run: `copilot-usage`
5. Paste your token when prompted

Token is saved securely to `~/.config/copilot-usage/github_token`

## Usage

```bash
copilot-usage              # Show your usage
copilot-usage octocat      # Show another user's usage
copilot-usage --help       # Show help
copilot-usage --reset-token # Update token
```

## Output

Shows:
- **Total Requests**: Your total Copilot requests this month
- **Pro Plan Status**: If you're within the 300 request limit
- **Requests by Model**: Breakdown by AI model (Claude, GPT-4, etc.)
- **Cost**: Total charges (if any)

Example:
```
Total Requests: 95
[✓] Within Pro plan limit (205 requests remaining)

Requests by Model:
  Claude Haiku 4.5: 1.65 requests
  Claude Sonnet 4.5: 92 requests

✓ All requests covered by Pro plan ($3.79 value of usage)
```

## Requirements

- bash 4.0+
- curl
- git (optional, for auto-detecting username)

## Privacy

- Your token is stored locally and never shared
- Only communicated with GitHub's official API
- Uses HTTPS for all requests

## License

MIT
