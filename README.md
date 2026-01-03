# AI-Powered SEO Automation Workflow

An end-to-end automated SEO analysis system that collects real SEO data, analyzes it, and generates AI-powered actionable insights using Google Gemini.

## 🎯 Features

✅ **Real SEO Data Collection**
- Google PageSpeed Insights API integration (no auth required)
- On-page SEO analysis (meta tags, headings, content)
- Technical SEO checks (HTTPS, response time, mobile-friendly)
- Image optimization analysis
- Link structure evaluation

✅ **Comprehensive Analysis**
- Performance scoring (0-100)
- Technical SEO evaluation
- On-page SEO assessment
- Automated issue detection with severity levels
- Strengths and opportunities identification

✅ **AI-Powered Insights**
- Google Gemini integration for intelligent recommendations
- Executive summaries
- Priority action plans
- Strategic recommendations
- 30-day implementation roadmap

✅ **Multiple Report Formats**
- Markdown (.md)
- HTML (styled, ready to share)
- JSON (for integrations)

## 📋 Requirements

- Python 3.8+
- Internet connection
- Google Gemini API key (free tier available)

## 🚀 Quick Start

### 1. Installation

```bash
# Clone or download the project
cd Task

# Install dependencies
pip install -r requirements.txt
```

### 2. Configuration

Create a `.env` file in the project root:

```bash
GEMINI_API_KEY=your_actual_gemini_api_key_here
```

**To get your Gemini API key:**
1. Visit [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Click "Get API Key"
3. Create a new API key
4. Copy and paste it into your `.env` file

### 3. Configure Target URLs

Edit `config.json` to specify which websites to analyze:

```json
{
  "target_urls": [
    "https://example.com",
    "https://your-website.com"
  ]
}
```

### 4. Run the Analysis

```bash
# Analyze URLs from config.json
python main.py

# Or analyze specific URLs directly
python main.py --urls https://example.com https://wikipedia.org

# Skip AI insights (if API key not available)
python main.py --skip-ai
```

## 📊 Usage Examples

### Basic Usage

```bash
python main.py
```

This will:
1. Read URLs from `config.json`
2. Collect SEO data using Google PageSpeed Insights
3. Analyze the data and identify issues
4. Generate AI-powered insights with Gemini
5. Create reports in `reports/` directory

### Analyze Specific URLs

```bash
python main.py --urls https://example.com https://another-site.com
```

### Without AI (Skip Gemini)

```bash
python main.py --skip-ai
```

Useful for testing or when you don't have a Gemini API key yet.

## 📁 Project Structure

```
Task/
├── main.py                 # Main orchestration script
├── seo_collector.py        # Data collection module
├── seo_analyzer.py         # Analysis engine
├── ai_insights.py          # Gemini AI integration
├── report_generator.py     # Report generation
├── config.json             # Configuration file
├── requirements.txt        # Python dependencies
├── .env                    # API keys (create this)
├── .env.example            # Example environment file
├── data/                   # Collected data (auto-created)
└── reports/                # Generated reports (auto-created)
```

## 🔧 Configuration Options

### config.json

```json
{
  "target_urls": [
    "https://example.com"
  ],
  "output_directory": "reports",
  "data_directory": "data",
  "analysis_metrics": [
    "page_speed",
    "meta_tags",
    "heading_structure",
    "image_optimization",
    "mobile_friendly"
  ]
}
```

**⚠️ SECURITY NOTE:** API keys should NEVER be stored in config.json. Always use the `.env` file for API keys, which is excluded from version control by `.gitignore`.

## 📈 What Gets Analyzed?

### Performance Metrics
- Performance Score (0-100)
- First Contentful Paint (FCP)
- Largest Contentful Paint (LCP)
- Speed Index
- Time to Interactive (TTI)
- Total Blocking Time (TBT)
- Cumulative Layout Shift (CLS)

### On-Page SEO
- Title tag (length, presence)
- Meta description (length, presence)
- Heading structure (H1, H2, H3)
- Image optimization (alt text)
- Word count
- Internal/external links

### Technical SEO
- HTTPS implementation
- Response time
- Status codes
- Mobile-friendliness
- robots.txt presence
- XML sitemap presence
- Compression enabled

## 📄 Generated Reports

After running the workflow, you'll find these reports in the `reports/` directory:

### 1. Markdown Report (.md)
- Clean, readable format
- Easy to share via GitHub, Notion, etc.
- Contains all analysis details

### 2. HTML Report (.html)
- Beautifully styled
- Ready to open in browser
- Visual score cards and metrics
- Color-coded issues

### 3. JSON Report (.json)
- Structured data
- Perfect for integrations
- Can be imported into other tools

## 🤖 AI Insights

The AI-powered insights include:

1. **Executive Summary**
   - High-level assessment
   - Critical areas needing attention

2. **Top 3 Priority Actions**
   - Most impactful quick wins
   - Specific, actionable steps

3. **Strategic Recommendations**
   - Long-term improvements
   - Content strategy
   - Technical optimizations

4. **Competitive Advantage Opportunities**
   - Differentiation strategies
   - Emerging trends

5. **30-Day Action Plan**
   - Week-by-week implementation guide
   - Clear milestones

## 🎓 Understanding Your SEO Score

| Score | Status | Meaning |
|-------|--------|---------|
| 90-100 | 🟢 Excellent | Outstanding SEO, minor optimizations |
| 75-89 | 🟢 Good | Solid foundation, room for improvement |
| 60-74 | 🟡 Fair | Needs attention, several issues |
| 40-59 | 🟠 Poor | Major improvements required |
| 0-39 | 🔴 Critical | Urgent action needed |

## 🔍 Example Workflow

```bash
# Step 1: Install
pip install -r requirements.txt

# Step 2: Set up API key
echo "GEMINI_API_KEY=your_key_here" > .env

# Step 3: Run analysis
python main.py --urls https://your-website.com

# Step 4: View reports
# Check reports/ directory for generated files
```

## 🐛 Troubleshooting

### "Gemini API key not configured"
- Create a `.env` file with `GEMINI_API_KEY=your_key`
- Or set environment variable: `set GEMINI_API_KEY=your_key` (Windows)

### "PageSpeed API error"
- Check internet connection
- Verify URL is accessible
- Try again (API has rate limits)

### Module not found errors
- Ensure all dependencies are installed: `pip install -r requirements.txt`
- Use a virtual environment for cleaner setup

### No reports generated
- Check `reports/` directory was created
- Look for error messages in console output
- Verify write permissions

## 🔄 Automation Setup

### Windows Task Scheduler

1. Open Task Scheduler
2. Create Basic Task
3. Set trigger (daily, weekly, etc.)
4. Action: Start a program
5. Program: `python`
6. Arguments: `C:\path\to\Task\main.py`

### Cron (Linux/Mac)

```bash
# Run daily at 9 AM
0 9 * * * cd /path/to/Task && python main.py
```

## 📊 Real-World Use Cases

1. **Website Monitoring**
   - Schedule daily/weekly SEO checks
   - Track score improvements over time
   - Get alerts for new issues

2. **Client Reporting**
   - Generate professional reports
   - Show before/after improvements
   - Provide actionable insights

3. **Competitive Analysis**
   - Compare multiple websites
   - Identify best practices
   - Benchmark performance

4. **Development QA**
   - Check SEO before deployment
   - Catch issues early
   - Maintain SEO standards

## 🎯 Assignment Deliverables Checklist

✅ **Working Automation**
- [x] Automated data collection from real sources
- [x] End-to-end workflow execution
- [x] Multiple URL support

✅ **AI Integration**
- [x] Google Gemini integration
- [x] Actionable insights generation
- [x] Strategic recommendations

✅ **Analysis & Insights**
- [x] Performance metrics
- [x] Technical SEO checks
- [x] On-page SEO analysis
- [x] Issue detection and prioritization

✅ **Report Generation**
- [x] Markdown format
- [x] HTML format
- [x] JSON format
- [x] AI-powered insights included

✅ **Documentation**
- [x] Comprehensive README
- [x] Setup instructions
- [x] Usage examples
- [x] Troubleshooting guide

## 🚀 Advanced Features

### Custom Analysis

You can modify `seo_analyzer.py` to add custom checks:

```python
def analyze_custom_metric(self):
    # Add your custom analysis logic
    pass
```

### Multiple Data Sources

Extend `seo_collector.py` to integrate additional APIs:
- Ahrefs API
- SEMrush API
- Google Search Console
- YouTube Analytics

### Scheduled Reports

Combine with email automation to send reports automatically:

```python
# Example: Send report via email
import smtplib
from email.mime.text import MIMEText

def send_report_email(report_content):
    # Email sending logic
    pass
```

## 📞 Support

For issues or questions:
1. Check this README
2. Review error messages carefully
3. Verify all dependencies are installed
4. Ensure API keys are configured correctly

## 🔐 Security Notes

**🚨 CRITICAL: Protecting Your API Keys**

- **NEVER** commit `.env` file with real API keys to version control
- **NEVER** put API keys in `config.json` or any other tracked files
- **ALWAYS** use environment variables (`.env` file) for sensitive credentials
- The `.gitignore` file excludes `.env` automatically - keep it that way
- If you accidentally commit an API key:
  1. Immediately revoke/regenerate the key at [Google AI Studio](https://makersuite.google.com/app/apikey)
  2. Remove the key from git history using tools like `git-filter-repo` or BFG Repo-Cleaner
  3. Never reuse that compromised key
- Rotate API keys regularly (every 90 days recommended)
- Keep dependencies updated to avoid security vulnerabilities
- Monitor your API usage for unexpected activity

## 📝 License

This project is created for educational purposes as part of an SEO automation assignment.

## 🎉 Success Criteria

This system demonstrates:

✅ **Real Use Case** - Works with actual websites and APIs  
✅ **End-to-End Automation** - Complete workflow from data → insights → reports  
✅ **AI Integration** - Uses Gemini for intelligent recommendations  
✅ **Quality Insights** - Generates actionable, specific recommendations  
✅ **Code Clarity** - Well-structured, documented, easy to follow  
✅ **Professional Output** - Multiple report formats, ready to present

---

**Built with ❤️ for SEO automation**
