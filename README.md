# GitHub Copilot Usage Tool

A terminal-based tool to fetch and display your GitHub Copilot usage data and billing information.

## Features

- **Copilot Premium Requests**: View API requests made to Copilot models
- **Billing Summary**: See overall usage across all products (Actions, Copilot, etc.)
- **Token Caching**: Securely stores your GitHub token locally for convenience
- **Zero-Value Filtering**: Omits models/products with no usage
- **Easy Setup**: Interactive token setup on first run
- **Pretty Output**: Color-coded, human-readable terminal output

## Requirements

- `bash` (4.0+)
- `curl`
- `jq` (for JSON parsing, optional but recommended)
- `git` (optional, for auto-detecting username)

## Installation

1. Download the script:
```bash
curl -o ~/bin/copilot-usage https://your-repo/copilot-usage
chmod +x ~/bin/copilot-usage
```

Or copy the script to your preferred location:
```bash
cp copilot-usage ~/bin/
chmod +x ~/bin/copilot-usage
```

2. Add to PATH (if not already in a PATH directory):
```bash
export PATH="$HOME/bin:$PATH"  # Add to ~/.bashrc or ~/.zshrc
```

## Authentication

### Getting Your GitHub Token

1. Visit: https://github.com/settings/tokens
2. Click "Generate new token (classic)" or create a fine-grained token
3. For fine-grained tokens, grant these permissions:
   - **Account permissions**: `Plan` (read-only)
4. Copy the generated token

On first run, the script will prompt you to enter your token. It will be securely stored in:
```
~/.config/copilot-usage/github_token
```

The token is stored with restrictive permissions (`600`) and is never transmitted anywhere except to the official GitHub API.

### Token Validation

The script **validates your token before saving it**. If you enter an invalid or expired token:
- The script will reject it and ask you to try again
- You get **up to 3 attempts** to enter a valid token
- Invalid tokens are **never saved** to disk

This prevents you from being locked out with an expired token stored locally.

### Resetting Your Token

To clear the stored token and use a new one:
```bash
copilot-usage --reset-token
```

## Usage

### Basic Usage

```bash
# Fetch usage for your GitHub username
copilot-usage

# Or specify a username
copilot-usage octocat
```

### Help

```bash
copilot-usage --help
copilot-usage -h
```

### Reset Token

```bash
copilot-usage --reset-token
```

## Output Example

```
Fetching Copilot Usage Data for: yonisirote

Copilot Premium Requests

Total Requests: 95

[✓] Within Pro plan limit (205 requests remaining)

Requests by Model:
  Claude Haiku 4.5: 1.65 requests
  Claude Sonnet 4.5: 92 requests
  Coding Agent model: 1 requests

✓ All requests covered by Pro plan ($3.79 value of usage)

Other Usage

  No other usage this period

✓ Done!
```

## Output Sections

### Copilot Premium Requests

- **Total Requests**: Combined requests across all AI models for this month
- **Pro Plan Status**: Shows if you're within the 300 request limit (included in Pro plan)
  - Within limit: `[✓] Within Pro plan limit (X requests remaining)` (in green)
  - Over limit: `[!] Exceeded Pro plan limit by X requests` (in yellow/warning)
- **Requests by Model**: Breakdown of requests by each AI model (alphabetically sorted)
- **Cost Status**: Shows if charges apply
  - Covered by plan: `✓ All requests covered by Pro plan ($X value of usage)`
  - With charges: `Total Cost: $X` plus discount info if applicable

### Other Usage

Additional GitHub services billed separately (e.g., Actions compute minutes).

**Note**: Only products/models with usage > 0 are displayed

## How It Works

1. **Authentication**: Uses your GitHub Personal Access Token to authenticate with the GitHub API
2. **Data Fetching**: Calls the GitHub REST API endpoints:
   - `/users/{username}/settings/billing/premium_request/usage` - Copilot usage
   - `/users/{username}/settings/billing/usage/summary` - Overall billing summary
3. **Filtering**: Removes any items with zero quantity to reduce clutter
4. **Formatting**: Presents data in an easy-to-read terminal format

## Data Privacy

- Your GitHub token is stored locally in `~/.config/copilot-usage/github_token`
- The token is **never** shared with anyone or anything except GitHub's official API
- The script uses HTTPS for all API communication
- Token file permissions are set to `600` (readable/writable only by you)

## Troubleshooting

### "API Error (401): Bad credentials"
Your GitHub token is invalid or expired. Reset it:
```bash
copilot-usage --reset-token
```

### "API Error (403): Forbidden"
Your token doesn't have the required permissions. Create a new token with `Plan` (read-only) permissions.

### "API Error (404): Resource not found"
The username doesn't exist or the endpoint isn't available. Verify the GitHub username is correct.

### "Command not found: jq"
The `jq` tool isn't installed. Install it:
- **macOS**: `brew install jq`
- **Ubuntu/Debian**: `apt-get install jq`
- **Fedora/CentOS**: `yum install jq`

The script can still work without jq, but output formatting may be less reliable.

## API Rate Limits

GitHub allows 5,000 authenticated API requests per hour. This tool makes 2 requests per run, so you can safely run it multiple times per hour.

## Supported Data

The tool fetches data from the **current month**. To view historical data:
1. Visit: https://github.com/settings/billing/cost-analysis
2. Use the date picker to select a different month

Future versions may add date range support.

## License

This tool is provided as-is for personal use.

## Support

For issues or feature requests, refer to the GitHub documentation:
- [Billing API Docs](https://docs.github.com/en/rest/billing/usage)
- [Creating PATs](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)
