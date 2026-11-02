# llms-install.md: Rowfield Data MCP

Instructions for an AI agent installing this MCP configuration for a user.

> Our own tools, published by Rowfield Data on Apify, built and operated with an AI agent.

1. This is a **remote** MCP server hosted by Apify. There is nothing to build or download.
2. Ask the user for their own Apify API token, or use OAuth if the client supports it. Never invent or reuse a token. Tokens are at https://console.apify.com/settings/integrations
3. Add this server to the client's MCP config (Claude Desktop: `claude_desktop_config.json`; Cursor: `~/.cursor/mcp.json` or `.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "rowfield-data": {
      "url": "https://mcp.apify.com?tools=founder-experiment/civicplus-job-postings,founder-experiment/k12-school-district-jobs-applitrack,founder-experiment/california-state-jobs-calcareers,founder-experiment/new-york-state-jobs-statejobsny,founder-experiment/wisconsin-state-government-jobs,founder-experiment/us-state-government-jobs,founder-experiment/canada-provincial-government-jobs,founder-experiment/manitoba-government-jobs,founder-experiment/victoria-government-jobs-careers-vic,founder-experiment/latvia-public-sector-vacancies,founder-experiment/civicplus-bid-postings,founder-experiment/eu-ted-tenders-scraper,founder-experiment/federal-register-documents-scraper,founder-experiment/sitemap-url-extractor,founder-experiment/website-logo-extractor,founder-experiment/nvd-cve-scraper,founder-experiment/saashub-alternatives-scraper,founder-experiment/empire-flippers-listings,founder-experiment/usgs-earthquake-catalog,founder-experiment/link-preview-open-graph-api",
      "headers": {
        "Authorization": "Bearer <APIFY_TOKEN>"
      }
    }
  }
}
```

4. For OAuth, drop the `headers` block. The client opens an Apify sign-in on first connection.
5. If the client cannot use remote servers, use the local stdio config:

```json
{
  "mcpServers": {
    "rowfield-data": {
      "command": "npx",
      "args": [
        "-y",
        "@apify/actors-mcp-server",
        "--tools",
        "founder-experiment/civicplus-job-postings,founder-experiment/k12-school-district-jobs-applitrack,founder-experiment/california-state-jobs-calcareers,founder-experiment/new-york-state-jobs-statejobsny,founder-experiment/wisconsin-state-government-jobs,founder-experiment/us-state-government-jobs,founder-experiment/canada-provincial-government-jobs,founder-experiment/manitoba-government-jobs,founder-experiment/victoria-government-jobs-careers-vic,founder-experiment/latvia-public-sector-vacancies,founder-experiment/civicplus-bid-postings,founder-experiment/eu-ted-tenders-scraper,founder-experiment/federal-register-documents-scraper,founder-experiment/sitemap-url-extractor,founder-experiment/website-logo-extractor,founder-experiment/nvd-cve-scraper,founder-experiment/saashub-alternatives-scraper,founder-experiment/empire-flippers-listings,founder-experiment/usgs-earthquake-catalog,founder-experiment/link-preview-open-graph-api"
      ],
      "env": {
        "APIFY_TOKEN": "<APIFY_TOKEN>"
      }
    }
  }
}
```

6. To load fewer tools, swap the URL for one of the grouped URLs in README.md.
7. Verify: list tools. You should see tools named `founder-experiment--<actor-name>`.
8. Tell the user: each tool call starts an Apify Actor run billed to their Apify account at the price on the Actor's Store page.
