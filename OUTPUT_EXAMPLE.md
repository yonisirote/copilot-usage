# Copilot Usage Tool - Output Format

## Example Output

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Fetching Copilot Usage Data for: yonisirote
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Copilot Premium Requests

Total Requests: 450

ℹ Exceeded Pro plan limit by 150 requests

Requests by Model:
  GPT-4: 300 requests
  Claude-3: 150 requests

Total Cost: $0.85

Other Usage

  Actions: 1000 minutes ($8.00)

✓ Done!
```

## Output Breakdown

### 1. Copilot Premium Requests Section

**Total Requests**: Shows the combined requests across all models this month

**Pro Plan Comparison**: 
- If under 300: Shows "Within Pro plan limit (X requests remaining)"
- If over 300: Shows "Exceeded Pro plan limit by X requests"

**Requests by Model**: 
- Lists each AI model you used
- Shows number of requests per model
- Only includes models with > 0 requests
- Listed alphabetically

**Total Cost**: Shows the total amount charged for Copilot usage

### 2. Other Usage Section

Shows any additional GitHub usage (like Actions minutes) that isn't Copilot

Format: `Product: Quantity UnitType ($Cost)`

---

## What's New in This Format

✅ **Cleaner layout** - Section headers make it easy to scan  
✅ **Total requests first** - Immediately see your usage  
✅ **Pro plan comparison** - Know if you're over the 300 request limit  
✅ **Per-model breakdown** - See which models you're using most  
✅ **Simple cost display** - One line for total Copilot cost  
✅ **Omits zero values** - Only shows products/models you actually used  

---

## Pro Plan Information

The GitHub Copilot Pro plan includes:
- **300 premium requests per month** (included in subscription)
- If you exceed 300, additional requests are charged at approximately $0.002 per request
- Different models may have different pricing

This tool compares your usage to the 300 request limit to help you understand if you're using extra capacity.
