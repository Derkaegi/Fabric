# SERPAPI Setup Guide for SEO Brief Pattern

## Quick Setup (5 minutes)

### 1. Get Your SERPAPI Key
1. Visit [serpapi.com](https://serpapi.com)
2. Sign up for free account (100 searches/month)
3. Navigate to Dashboard → API Key
4. Copy your API key (format: `abc123def456...`)

### 2. Configure Environment Variable

**Windows (Command Prompt):**
```cmd
setx SERPAPI_KEY "your_api_key_here"
```

**Windows (PowerShell):**
```powershell
[Environment]::SetEnvironmentVariable("SERPAPI_KEY", "your_api_key_here", "User")
```

**Linux/Mac:**
```bash
export SERPAPI_KEY="your_api_key_here"
echo 'export SERPAPI_KEY="your_api_key_here"' >> ~/.bashrc
```

### 3. Verify Setup
Test your configuration:
```bash
echo $SERPAPI_KEY  # Should display your key
```

### 4. Test the Pattern
```bash
cd /path/to/fabric
echo "best CRM software" | ./fabric --pattern create_seo_brief
```

## Advanced Configuration

### API Key Storage Options

**Option 1: Environment Variable (Recommended)**
- Secure and persistent
- Works across all applications
- Easy to update

**Option 2: Fabric Configuration File**
Create `.env` file in Fabric directory:
```bash
# .env file
SERPAPI_KEY=your_api_key_here
SERPAPI_MONTHLY_LIMIT=250
SERPAPI_CACHE_DURATION=86400
```

**Option 3: System-wide Configuration**
Add to system environment variables for all users.

### API Key Security Best Practices

✅ **Do:**
- Store in environment variables
- Use different keys for dev/prod
- Rotate keys periodically
- Monitor usage in SERPAPI dashboard

❌ **Don't:**
- Hardcode in scripts
- Share keys in public repositories
- Use production keys for testing
- Store in plain text files

## Usage Monitoring

### Track Your Monthly Usage

**SERPAPI Dashboard:**
- Login to serpapi.com
- View real-time usage statistics
- Set up usage alerts
- Monitor remaining credits

**Pattern Output:**
Each SEO brief shows:
```
## API USAGE SUMMARY
- Total API calls used: 3/5
- Monthly budget remaining: 247 calls
- Efficiency rating: High
```

### Monthly Planning

**Free Tier (100 searches/month):**
- 20-33 SEO briefs per month (3-5 calls each)
- Best for: Personal projects, small websites

**Paid Tier ($50/month for 5,000 searches):**
- 1,000-1,667 SEO briefs per month
- Best for: Agencies, enterprise content teams

## Troubleshooting

### Common Issues

**"API key not found" Error:**
```bash
# Check if variable is set
echo $SERPAPI_KEY

# If empty, set it again
export SERPAPI_KEY="your_key_here"
```

**"Rate limit exceeded" Error:**
- You've used all monthly searches
- Wait for next billing cycle
- Upgrade to paid plan
- Pattern will use fallback templates

**"Invalid API key" Error:**
- Key was typed incorrectly
- Key was regenerated in dashboard
- Check for extra spaces/characters

**"No results returned" Error:**
- Search query might be too specific
- Try broader keyword variations
- Check SERPAPI status page

### Pattern Behavior

**With Valid API Key:**
- Full keyword research data
- Real competitor analysis
- Actual "People Also Ask" questions
- Complete API usage tracking

**Without API Key (Fallback Mode):**
- Manual semantic keyword suggestions
- Template-based competitor analysis
- Curated FAQ question banks
- Static content recommendations

## API Limits & Optimization

### Free Tier Optimization

**Smart Usage Tips:**
- Use 3-4 calls per brief (not 5)
- Focus on high-value keywords
- Batch related keyword research
- Save competitor analysis for important content

**Monthly Planning:**
- Week 1: High-priority keywords (use full 5 calls)
- Week 2-3: Standard keywords (3-4 calls each)
- Week 4: Low-priority keywords (2-3 calls each)

### Upgrade Considerations

**Upgrade to Paid When:**
- Creating 30+ briefs per month
- Running agency/client work
- Need real-time competitive data
- Building content at scale

**Cost-Benefit Analysis:**
- Free: $0 for 20-33 briefs ($0 per brief)
- Paid: $50 for 1,000+ briefs ($0.05 per brief)

## Support Resources

### SERPAPI Documentation
- [API Documentation](https://serpapi.com/search-api)
- [Response Structure](https://serpapi.com/google-organic-results)
- [Status Page](https://status.serpapi.com)

### Pattern Support
- Check `tech_report.md` for detailed implementation
- Review `fallback_templates.md` for manual alternatives
- Monitor `serpapi_integration.md` for API strategy

### Community Resources
- [SERPAPI Python SDK](https://github.com/serpapi/google-search-results-python)
- [Fabric Patterns GitHub](https://github.com/danielmiessler/fabric)
- [SEO Community Forums](https://www.reddit.com/r/SEO)

---
*Setup Guide v1.0*
*Compatible with: create_seo_brief pattern*
*Last Updated: 2025-09-18*