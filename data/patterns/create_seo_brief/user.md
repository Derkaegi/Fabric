# SEO Content Brief Generator

This pattern creates comprehensive, actionable SEO content briefs optimized for practical implementation while respecting strict API budget constraints.

## ⚡ Efficiency Focus

**Maximum API Calls:** 3-5 per execution
**Monthly Budget:** 250 SERPAPI calls (free tier)
**Expected Output:** 50-83 briefs per month

## Usage

```bash
fabric --pattern create_seo_brief
```

Then enter your keyword and context when prompted.

## Input Format

**Primary Keyword:** [Your main target keyword]
**Additional Context:** [Optional: Target audience, content type, business goals]

## Example Inputs

### Standard Brief (3-4 API calls)
```
Primary Keyword: best project management software
Additional Context: Small business owners, comparison guide, focus on affordability
```

### High-Value Brief (4-5 API calls)
```
Primary Keyword: enterprise CRM solutions
Additional Context: B2B decision makers, comprehensive analysis, competitor focus
```

### Budget-Conscious Brief (1-2 API calls)
```
Primary Keyword: social media marketing tips
Additional Context: Beginner marketers, practical advice, minimal research needed
```

## API Usage Strategy

**Call Priority Allocation:**
1. **Call 1:** Primary keyword data (volume, competition, intent)
2. **Call 2:** Batch semantic keywords (related terms + long-tail)
3. **Call 3:** "People Also Ask" questions (optional)
4. **Call 4-5:** Competitor insights (high-value keywords only)

## Monthly Planning Guide

### Conservative Usage (3 calls average)
- **83 briefs/month** - Ideal for regular content creation
- **Best for:** Blog content, informational articles, low-competition keywords

### Balanced Usage (4 calls average)
- **62 briefs/month** - Professional content strategy
- **Best for:** Commercial keywords, competitive analysis needed

### Premium Usage (5 calls average)
- **50 briefs/month** - High-stakes content
- **Best for:** Money keywords, enterprise content, detailed competitor analysis

## What You'll Get

✅ **Keyword Strategy:** Search intent + semantic keywords (always included)
✅ **Content Structure:** SEO-optimized H1/H2/H3 headings (always included)
✅ **Linking Strategy:** Internal + external recommendations (always included)
⚡ **Competitor Insights:** Top 3 analysis (API-dependent, fallback available)
⚡ **FAQ Integration:** PAA questions (API-dependent, fallback available)
📊 **API Usage Report:** Track monthly budget consumption

## Smart Fallbacks

When API limits are reached, the pattern provides:
- Manual semantic keyword suggestions
- Template-based competitor analysis
- Curated FAQ question banks by industry
- Expert knowledge alternatives

## API Requirements & Setup

**Quick Setup (2 minutes):**
1. Get free SERPAPI key at [serpapi.com](https://serpapi.com) (100 searches/month)
2. Set environment variable: `export SERPAPI_KEY="your_key_here"`
3. Test: `echo $SERPAPI_KEY` should show your key

**Detailed Setup:**
- See `setup_guide.md` for step-by-step instructions
- Available monthly calls tracked automatically in pattern output
- Budget monitoring included (pattern warns at 80% usage)

## Best Practices

### 🎯 Batch Similar Keywords
Group related research to maximize API efficiency:
```
Session 1: "CRM software" + "best CRM tools" + "CRM comparison"
Session 2: "project management" + "PM software" + "team collaboration"
```

### 📊 Monitor Usage
Check monthly consumption in pattern output:
- Track API calls used per brief
- Plan high-value keywords for early month
- Save low-competition keywords for end-of-month

### 🚀 Optimize Input
More context = better output without extra API calls:
```
Good: "SEO tools"
Better: "SEO tools for small business, focus on keyword research, under $100/month"
```

## Troubleshooting

**Pattern using too many calls?**
- Add more context to reduce competitor analysis needs
- Focus on informational keywords vs. commercial ones
- Use pattern early in month when API budget is fresh

**Need competitor analysis but low on API calls?**
- Manual Google search for top 3 results
- Pattern provides template-based analysis
- Save API calls for keyword research (higher ROI)

## Output

A structured, immediately actionable content brief that balances comprehensive SEO guidance with sustainable API usage.