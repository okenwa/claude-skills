---
name: agent-browser
description: Browser automation - navigate sites, scrape content, fill forms, click elements. Triggers on: browse, scrape, click, fill form, open site, screenshot.
---

# Agent Browser Skill

Browser automation via Puppeteer/Playwright MCP.

## Capabilities

- Navigate to URLs
- Scrape page content
- Fill and submit forms
- Click buttons/links
- Take screenshots
- Extract structured data

## Process

1. **Identify goal** - what site, what action
2. **Navigate** - go to URL
3. **Interact** - click, type, scroll as needed
4. **Extract** - get data or confirm action
5. **Report** - return results or screenshot

## Rules

- Always report current URL after navigation
- Handle login walls gracefully - ask for creds if needed
- For scraping, return structured data not raw HTML
- Take screenshots for visual confirmation when useful
- Respect rate limits and robots.txt
- Close browser sessions when done
