# Copilot Usage Tool - Changelog

## Latest Updates

### Fixed JSON Parsing & Output Formatting (v1.2)

**What changed:**
- ✅ Fixed parsing to use `grossQuantity` instead of `netQuantity` (shows all usage, not just paid overage)
- ✅ Removed jq dependency - now uses pure bash parsing with grep
- ✅ Proper number rounding for cleaner display (95 instead of 94.65)
- ✅ Now shows breakdown by model with actual request counts
- ✅ Displays whether usage is covered by Pro plan or incurs additional charges

**Why it matters:**
Previously, the script was filtering out all data because it looked for `netQuantity > 0`, but your Pro plan discount covers all requests (so netQuantity is 0). Now it shows:
- **Total Requests**: Sum of all requests across models
- **Per-Model Breakdown**: Exactly which models you used and how many requests
- **Cost Status**: Whether you're within the 300 request Pro plan limit
- **Discount Info**: Shows if you have credits/discount applied

**Technical improvements:**
- Works without jq (no external dependency needed)
- Uses grep patterns to extract JSON values
- Proper bash arithmetic for calculations
- Better number formatting and rounding

---

### Previous: Improved Token Handling (v1.1)

- Added **retry loop** for invalid tokens (up to 3 attempts)
- Better error messages explaining what went wrong
- Only saves tokens that pass validation

---

## Current Output

```
Copilot Premium Requests

Total Requests: 95

ℹ Within Pro plan limit (205 requests remaining)

Requests by Model:
  Claude Haiku 4.5: 1.65 requests
  Claude Sonnet 4.5: 92 requests
  Coding Agent model: 1 requests

✓ All requests covered by Pro plan ($3.79 value of usage)
```

You can now see exactly which models you're using and how much!
