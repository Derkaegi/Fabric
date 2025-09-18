# SERPAPI Integration Strategy for SEO Brief Pattern

## API Integration Design

### **Call Allocation Strategy (3-5 calls max)**

**Priority 1 - Essential (Calls 1-2)**
1. **Primary Keyword Research** - Core search data
2. **Related Keywords Batch** - Semantic terms + suggestions

**Priority 2 - High Value (Call 3)**
3. **People Also Ask Questions** - FAQ extraction

**Priority 3 - Optional (Calls 4-5)**
4. **Competitor Analysis** - Top 3 organic results
5. **Additional Context** - Location-specific or device-specific data

## SERPAPI Endpoints & Parameters

### **Call #1: Primary Keyword Research**
```
Endpoint: Google Search API
Parameters:
- q: "{primary_keyword}"
- num: 10 (top 10 results)
- device: desktop
- hl: en (English)
- gl: us (United States)
- api_key: {user_api_key}

Data Extracted:
- total_results (search volume indicator)
- organic_results[0-2] (top 3 competitors)
- search_metadata.processing_time
```

### **Call #2: Related Keywords & Suggestions**
```
Endpoint: Google Search API
Parameters:
- q: "{primary_keyword}"
- num: 10
- device: desktop
- related_searches: true

Data Extracted:
- related_searches[] (semantic keywords)
- searches_related_to_original_query[]
- people_also_search_for[]
```

### **Call #3: People Also Ask Questions**
```
Endpoint: Google Search API
Parameters:
- q: "{primary_keyword}"
- num: 10
- device: desktop

Data Extracted:
- related_questions[]
- people_also_ask[]
- answer_box.snippet (if available)
```

### **Call #4-5: Enhanced Competitor Analysis** (Optional)
```
Endpoint: Google Search API
Parameters:
- q: "{primary_keyword}"
- num: 20 (extended results)
- device: mobile (alternative perspective)
- location: "{target_location}" (if specified)

Data Extracted:
- Extended organic_results[3-9]
- about_this_result[] (source analysis)
- featured_snippet data
```

## Response Structure Mapping

### **Organic Results → Competitor Analysis**
```json
{
  "organic_results": [
    {
      "position": 1,
      "title": "Best CRM Software for Small Business 2024",
      "link": "https://example.com/crm-guide",
      "snippet": "Compare top CRM tools...",
      "about_this_result": {
        "source": {
          "description": "Software review site",
          "security": "secure"
        }
      }
    }
  ]
}
```
**Maps to:**
- Competitor position ranking
- Content approach (title analysis)
- Value proposition (snippet analysis)
- Domain authority indicators

### **Related Searches → Semantic Keywords**
```json
{
  "related_searches": [
    {"query": "best CRM for small business"},
    {"query": "affordable CRM software"},
    {"query": "CRM comparison 2024"}
  ]
}
```
**Maps to:**
- Primary semantic keyword variations
- Long-tail keyword opportunities
- Content angle insights

### **Related Questions → FAQ Section**
```json
{
  "related_questions": [
    {
      "question": "What is the best CRM for small business?",
      "snippet": "The best CRM depends on your specific needs...",
      "source": "https://authority-site.com"
    }
  ]
}
```
**Maps to:**
- FAQ question headlines
- Answer guidance/snippets
- Authoritative source references

## API Call Efficiency Optimizations

### **Batch Query Strategy**
Instead of multiple individual calls:
```
❌ Inefficient:
Call 1: "best CRM software"
Call 2: "CRM for small business"
Call 3: "affordable CRM tools"

✅ Efficient:
Call 1: "best CRM software" (primary + related_searches)
Call 2: "CRM small business questions" (PAA focus)
```

### **Smart Parameter Usage**
- **num=10**: Sufficient for top competitor analysis without over-consuming
- **device=desktop**: Standard for most SEO research
- **gl=us**: Default unless specific geo-targeting needed
- **related_searches=true**: Maximize data per call

### **Response Caching Strategy**
- Cache responses for 24 hours (search results change slowly)
- Reuse related_searches for similar keywords
- Build keyword family databases to reduce API calls

## Error Handling & Fallbacks

### **API Limit Reached**
```
If monthly_calls >= 240:
  Use manual semantic keyword templates
  Apply competitor analysis templates
  Reference curated FAQ question banks
```

### **API Response Errors**
```
If API call fails:
  Log error type and continue with available data
  Use cached responses if available (< 24hrs old)
  Apply relevant manual templates
  Maintain pattern output quality
```

### **Rate Limiting**
```
If rate_limited:
  Implement exponential backoff (1s, 2s, 4s delays)
  Queue remaining calls for retry
  Continue with available data
  Report API status to user
```

## Implementation Integration Points

### **Fabric Pattern Integration**
The SERPAPI calls will be embedded in the existing system.md pattern at these points:

1. **Step 1 (Keyword Research)** → API Calls #1-2
2. **Step 2 (Competitor Analysis)** → API Call #4 (optional)
3. **Step 4 (FAQ Integration)** → API Call #3
4. **Output Section** → API usage tracking

### **Environment Variables**
```bash
export SERPAPI_KEY="your_api_key_here"
export SERPAPI_MONTHLY_LIMIT=250
export SERPAPI_CACHE_DURATION=86400  # 24 hours
```

### **Response Processing Pipeline**
```
1. Make API call with error handling
2. Parse JSON response
3. Extract relevant SEO data points
4. Apply data to content brief template
5. Track API usage counter
6. Return structured brief + usage stats
```

## Cost & Performance Optimization

### **Cost Management**
- **Free Tier:** 100 searches/month (SERPAPI)
- **Paid Tier:** $50/month for 5,000 searches
- **Target Usage:** 3-4 calls per brief = 62-83 briefs/month on free tier

### **Performance Targets**
- **Response Time:** < 3 seconds per API call
- **Accuracy:** 90%+ keyword relevance
- **Coverage:** 100% fallback availability
- **Reliability:** 99%+ uptime with error handling

### **Monitoring & Alerting**
- Track daily/monthly API usage
- Alert at 80% monthly consumption
- Monitor response time and error rates
- Report efficiency metrics in pattern output

---
*Integration Design v1.0*
*Compatible with: create_seo_brief pattern*
*API Provider: SERPAPI Google Search API*
*Budget Target: 250 calls/month (free tier)*