# FireCrawl MCP Server
[![smithery badge](https://smithery.ai/badge/mcp-server-firecrawl)](https://smithery.ai/server/mcp-server-firecrawl)

A Model Context Protocol (MCP) server implementation that integrates with FireCrawl for advanced web scraping capabilities.

## Features

- **JavaScript Rendering**: Extract content from JavaScript-heavy websites
- **Mobile/Desktop Views**: Support for different viewport configurations
- **Smart Rate Limiting**: Built-in rate limit handling
- **Multiple Formats**: Support for HTML, Markdown, screenshots, and raw text extraction
- **Batch Processing**: Efficient handling of multiple URLs
- **Content Filtering**: Include or exclude specific HTML tags

## Tools

### fire_crawl_scrape

Scrapes content from a single URL with customizable options.

- Inputs:
  - `url` (string): Target URL to scrape
  - `formats` (array): Output formats (`markdown`, `html`, `rawHtml`, `screenshot`, `links`, `screenshot@fullPage`, `extract`)
  - `waitFor` (number, optional): Wait time in milliseconds
  - `onlyMainContent` (boolean, optional): Extract main content only
  - `includeTags` (array, optional): HTML tags to specifically include
  - `excludeTags` (array, optional): HTML tags to exclude
  - `mobile` (boolean, optional): Use mobile viewport
  - `skipTlsVerification` (boolean, optional): Skip TLS verification

### fire_crawl_batch

Initiates a batch scraping job for multiple URLs.

- Inputs:
  - `urls` (array): List of URLs to scrape
  - `formats` (array): Output formats (same as single scrape)
  - Other options same as `fire_crawl_scrape`

### fire_crawl_status

Checks the status of a batch scraping job.

- Inputs:
  - `id` (string): Batch job ID to check

## Installation

### Installing via Smithery

To install FireCrawl for Claude Desktop automatically via [Smithery](https://smithery.ai/server/mcp-server-firecrawl):

```bash
npx -y @smithery/cli install mcp-server-firecrawl --client claude
```

### Manual Installation
```bash
npm install mcp-server-firecrawl
```

## Configuration

### Getting an API Key

1. Sign up for a [FireCrawl account](https://firecrawl.dev)
2. Generate your API key from the dashboard
3. Set the API key in your environment

### Usage with Claude Desktop

Add this to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "mcp-server-firecrawl": {
      "command": "npx",
      "args": ["-y", "mcp-server-firecrawl"],
      "env": {
        "FIRE_CRAWL_API_KEY": "YOUR_API_KEY_HERE"
      }
    }
  }
}
```

## Development

```bash
# Install dependencies
npm install

# Build
npm run build

# Run tests
npm test
```

## Rate Limits

- 3 requests per minute on free tier
- 25-second cooldown after hitting rate limit
- Higher limits available on paid plans

## License

MIT License - see LICENSE file for details
