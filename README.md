# Rowfield Data MCP

Use the 19 Rowfield Data scrapers on Apify as **MCP tools** in Claude Desktop, Cursor or other MCP clients.

> Our own tools, published by Rowfield Data on Apify, built and operated with an AI agent.

This repo has **no server code**.
It is a config and docs repo.
The tools run on **Apify's hosted MCP server** (`https://mcp.apify.com`), which turns any Apify Actor into an MCP tool.
You pick Actors with the `tools` URL parameter, as described in the [Apify MCP docs](https://docs.apify.com/platform/integrations/mcp).

## What you need

- An MCP client that supports remote (streamable HTTP) servers, or Node.js for the local option.
- An Apify account. Sign in with OAuth when your client asks, or use your own Apify API token from [Apify Console > API & Integrations](https://console.apify.com/settings/integrations).
- Runs are billed by Apify to **your** account at the Actor prices below.

## Quick start (all 19 tools)

Server URL:

```
https://mcp.apify.com?tools=founder-experiment/civicplus-job-postings,founder-experiment/k12-school-district-jobs-applitrack,founder-experiment/california-state-jobs-calcareers,founder-experiment/new-york-state-jobs-statejobsny,founder-experiment/wisconsin-state-government-jobs,founder-experiment/us-state-government-jobs,founder-experiment/canada-provincial-government-jobs,founder-experiment/manitoba-government-jobs,founder-experiment/victoria-government-jobs-careers-vic,founder-experiment/latvia-public-sector-vacancies,founder-experiment/civicplus-bid-postings,founder-experiment/eu-ted-tenders-scraper,founder-experiment/federal-register-documents-scraper,founder-experiment/sitemap-url-extractor,founder-experiment/website-logo-extractor,founder-experiment/nvd-cve-scraper,founder-experiment/saashub-alternatives-scraper,founder-experiment/empire-flippers-listings,founder-experiment/usgs-earthquake-catalog
```

### Option 1: OAuth (no token in the config)

```json
{
  "mcpServers": {
    "rowfield-data": {
      "url": "https://mcp.apify.com?tools=founder-experiment/civicplus-job-postings,founder-experiment/k12-school-district-jobs-applitrack,founder-experiment/california-state-jobs-calcareers,founder-experiment/new-york-state-jobs-statejobsny,founder-experiment/wisconsin-state-government-jobs,founder-experiment/us-state-government-jobs,founder-experiment/canada-provincial-government-jobs,founder-experiment/manitoba-government-jobs,founder-experiment/victoria-government-jobs-careers-vic,founder-experiment/latvia-public-sector-vacancies,founder-experiment/civicplus-bid-postings,founder-experiment/eu-ted-tenders-scraper,founder-experiment/federal-register-documents-scraper,founder-experiment/sitemap-url-extractor,founder-experiment/website-logo-extractor,founder-experiment/nvd-cve-scraper,founder-experiment/saashub-alternatives-scraper,founder-experiment/empire-flippers-listings,founder-experiment/usgs-earthquake-catalog"
    }
  }
}
```

On first connection your browser opens an Apify sign-in.

### Option 2: Bearer token

```json
{
  "mcpServers": {
    "rowfield-data": {
      "url": "https://mcp.apify.com?tools=founder-experiment/civicplus-job-postings,founder-experiment/k12-school-district-jobs-applitrack,founder-experiment/california-state-jobs-calcareers,founder-experiment/new-york-state-jobs-statejobsny,founder-experiment/wisconsin-state-government-jobs,founder-experiment/us-state-government-jobs,founder-experiment/canada-provincial-government-jobs,founder-experiment/manitoba-government-jobs,founder-experiment/victoria-government-jobs-careers-vic,founder-experiment/latvia-public-sector-vacancies,founder-experiment/civicplus-bid-postings,founder-experiment/eu-ted-tenders-scraper,founder-experiment/federal-register-documents-scraper,founder-experiment/sitemap-url-extractor,founder-experiment/website-logo-extractor,founder-experiment/nvd-cve-scraper,founder-experiment/saashub-alternatives-scraper,founder-experiment/empire-flippers-listings,founder-experiment/usgs-earthquake-catalog",
      "headers": {
        "Authorization": "Bearer <APIFY_TOKEN>"
      }
    }
  }
}
```

Replace `<APIFY_TOKEN>` with your own Apify API token. Do not commit it.

### Option 3: Local stdio (clients without remote server support)

```json
{
  "mcpServers": {
    "rowfield-data": {
      "command": "npx",
      "args": [
        "-y",
        "@apify/actors-mcp-server",
        "--tools",
        "founder-experiment/civicplus-job-postings,founder-experiment/k12-school-district-jobs-applitrack,founder-experiment/california-state-jobs-calcareers,founder-experiment/new-york-state-jobs-statejobsny,founder-experiment/wisconsin-state-government-jobs,founder-experiment/us-state-government-jobs,founder-experiment/canada-provincial-government-jobs,founder-experiment/manitoba-government-jobs,founder-experiment/victoria-government-jobs-careers-vic,founder-experiment/latvia-public-sector-vacancies,founder-experiment/civicplus-bid-postings,founder-experiment/eu-ted-tenders-scraper,founder-experiment/federal-register-documents-scraper,founder-experiment/sitemap-url-extractor,founder-experiment/website-logo-extractor,founder-experiment/nvd-cve-scraper,founder-experiment/saashub-alternatives-scraper,founder-experiment/empire-flippers-listings,founder-experiment/usgs-earthquake-catalog"
      ],
      "env": {
        "APIFY_TOKEN": "<APIFY_TOKEN>"
      }
    }
  }
}
```

Ready-made files: [`configs/`](configs/).

## Smaller tool sets

Fewer tools keep the client's tool list short. Use one of these URLs instead:

- **Government and public sector jobs**

  ```
  https://mcp.apify.com?tools=founder-experiment/civicplus-job-postings,founder-experiment/k12-school-district-jobs-applitrack,founder-experiment/california-state-jobs-calcareers,founder-experiment/new-york-state-jobs-statejobsny,founder-experiment/wisconsin-state-government-jobs,founder-experiment/us-state-government-jobs,founder-experiment/canada-provincial-government-jobs,founder-experiment/manitoba-government-jobs,founder-experiment/victoria-government-jobs-careers-vic,founder-experiment/latvia-public-sector-vacancies
  ```
- **Bids, tenders and regulations**

  ```
  https://mcp.apify.com?tools=founder-experiment/civicplus-bid-postings,founder-experiment/eu-ted-tenders-scraper,founder-experiment/federal-register-documents-scraper
  ```
- **Developer, SEO and security data**

  ```
  https://mcp.apify.com?tools=founder-experiment/sitemap-url-extractor,founder-experiment/website-logo-extractor,founder-experiment/nvd-cve-scraper
  ```
- **Market and science data**

  ```
  https://mcp.apify.com?tools=founder-experiment/saashub-alternatives-scraper,founder-experiment/empire-flippers-listings,founder-experiment/usgs-earthquake-catalog
  ```

Example (government jobs only):

```json
{
  "mcpServers": {
    "rowfield-gov-jobs": {
      "url": "https://mcp.apify.com?tools=founder-experiment/civicplus-job-postings,founder-experiment/k12-school-district-jobs-applitrack,founder-experiment/california-state-jobs-calcareers,founder-experiment/new-york-state-jobs-statejobsny,founder-experiment/wisconsin-state-government-jobs,founder-experiment/us-state-government-jobs,founder-experiment/canada-provincial-government-jobs,founder-experiment/manitoba-government-jobs,founder-experiment/victoria-government-jobs-careers-vic,founder-experiment/latvia-public-sector-vacancies",
      "headers": {
        "Authorization": "Bearer <APIFY_TOKEN>"
      }
    }
  }
}
```

## What the client sees

Each Actor shows up as a tool named `founder-experiment--<actor-name>` (for example `founder-experiment--sitemap-url-extractor`).
When Actor tools are loaded, Apify's server also adds helper tools such as `get-actor-run`, `get-dataset-items`, `get-key-value-store-record` and `abort-actor-run`.

## Tools

Descriptions and prices are copied from the live Apify Store listings (checked 2026-11-02).
Prices can change; the Store listing is the source of truth.

### Government and public sector jobs

| Tool (Apify Actor) | What it does | Price (pay per event) |
|---|---|---|
| [Government Jobs Scraper: City & County Jobs (CivicPlus)](https://apify.com/founder-experiment/civicplus-job-postings)<br>`founder-experiment/civicplus-job-postings` | Government jobs scraper for US public sector jobs: city jobs and county jobs on CivicPlus sites (Jobs.aspx). | $2 per 1,000 results (job posting) + $0.00005 per Actor start (per GB of memory) |
| [K-12 School & Teacher Jobs (AppliTrack) \| $0.30/1k](https://apify.com/founder-experiment/k12-school-district-jobs-applitrack)<br>`founder-experiment/k12-school-district-jobs-applitrack` | School district, teacher and substitute jobs scraper: K-12 job postings from 50 AppliTrack portals in 36 states (JSON, CSV, API). | $0.30 per 1,000 results (job posting) + $0.00005 per Actor start (per GB of memory) |
| [California State Government Jobs Scraper (CalCareers)](https://apify.com/founder-experiment/california-state-jobs-calcareers)<br>`founder-experiment/california-state-jobs-calcareers` | CalCareers California state government jobs: title, department, county, telework, salary, dates, link. | $0.50 per 1,000 results (job posting) + $0.00005 per Actor start (per GB of memory) |
| [New York State Government Jobs Scraper (StateJobsNY)](https://apify.com/founder-experiment/new-york-state-jobs-statejobsny)<br>`founder-experiment/new-york-state-jobs-statejobsny` | New York State government job listings from StateJobsNY job board: title, grade, agency, county, posted date, deadline, link. | $0.50 per 1,000 results (job posting) + $0.00005 per Actor start (per GB of memory) |
| [Wisconsin State Government Jobs Scraper](https://apify.com/founder-experiment/wisconsin-state-government-jobs)<br>`founder-experiment/wisconsin-state-government-jobs` | Wisconsin state government jobs from the public wisc.jobs list: title, agency, job class, category, location, posted/deadline date, link. | $0.50 per 1,000 results (job posting) + $0.00005 per Actor start (per GB of memory) |
| [US State Government Jobs Scraper](https://apify.com/founder-experiment/us-state-government-jobs)<br>`founder-experiment/us-state-government-jobs` | US state government job listings for California, New York, Wisconsin, North Dakota: civil service jobs, one schema (state, title, agency, location, dates, link). | $1 per 1,000 results (job posting) + $0.00005 per Actor start (per GB of memory) |
| [Canada Provincial Government Jobs Scraper](https://apify.com/founder-experiment/canada-provincial-government-jobs)<br>`founder-experiment/canada-provincial-government-jobs` | Canada government jobs scraper for provincial jobs in Manitoba, New Brunswick, Newfoundland and Labrador: public sector jobs, one schema (title, department, location, dates, link). | $1 per 1,000 results (job posting) + $0.00005 per Actor start (per GB of memory) |
| [Manitoba Government Jobs Scraper (Canada)](https://apify.com/founder-experiment/manitoba-government-jobs)<br>`founder-experiment/manitoba-government-jobs` | Manitoba (Canada) government job listings, daily new-jobs feed: title, department, classification, salary, location, posted, closing date, link. | $0.50 per 1,000 results (job posting) + $0.00005 per Actor start (per GB of memory) |
| [Victoria Government Jobs Scraper (Australia, Careers Vic)](https://apify.com/founder-experiment/victoria-government-jobs-careers-vic)<br>`founder-experiment/victoria-government-jobs-careers-vic` | Victoria government job listings from Careers Vic job board: title, organisation, salary, grade, location, closing date, link. | $0.50 per 1,000 results (job posting) + $0.00005 per Actor start (per GB of memory) |
| [Latvia Public Sector Vacancies (NVA) \| $0.50/1k](https://apify.com/founder-experiment/latvia-public-sector-vacancies)<br>`founder-experiment/latvia-public-sector-vacancies` | Current Latvian public sector vacancies from the NVA open data set (CC0): title, employer name, salary range, workload, address, deadline, link. | $0.50 per 1,000 results (vacancy) + $0.00005 per Actor start (per GB of memory) |

### Bids, tenders and regulations

| Tool (Apify Actor) | What it does | Price (pay per event) |
|---|---|---|
| [Government Bids Scraper: City & County RFPs (CivicPlus)](https://apify.com/founder-experiment/civicplus-bid-postings)<br>`founder-experiment/civicplus-bid-postings` | Government bids and RFP scraper for US city and county CivicPlus sites (Bids.aspx): open public bids, RFPs and RFQs with deadlines and links. | $3 per 1,000 results (bid) + $0.00005 per Actor start (per GB of memory) |
| [EU TED Tenders Scraper: Calls for Tender \| $1.5/1k](https://apify.com/founder-experiment/eu-ted-tenders-scraper)<br>`founder-experiment/eu-ted-tenders-scraper` | Export new EU calls for tender from TED: notice number, title, buyer, country, CPV codes, publication date, links. | $1.5 per 1,000 results (call for tender) + $0.00005 per Actor start (per GB of memory) |
| [Federal Register Documents Scraper \| $1.5/1k](https://apify.com/founder-experiment/federal-register-documents-scraper)<br>`founder-experiment/federal-register-documents-scraper` | New US Federal Register rules, proposed rules, notices and presidential documents via the FederalRegister.gov API: agencies, dockets, CFR parts, comment deadlines. | $1.5 per 1,000 results (document) + $0.00005 per Actor start (per GB of memory) |

### Developer, SEO and security data

| Tool (Apify Actor) | What it does | Price (pay per event) |
|---|---|---|
| [Sitemap URL Extractor & Scraper: All Website URLs](https://apify.com/founder-experiment/sitemap-url-extractor)<br>`founder-experiment/sitemap-url-extractor` | Get every URL of a website from its XML sitemaps: robots.txt and sitemap.xml discovery, indexes, .gz, lastmod and path filters. | $0.25 per 1,000 results (url) + $0.00005 per Actor start (per GB of memory) |
| [Company Logo & Favicon: Clearbit Logo Alternative](https://apify.com/founder-experiment/website-logo-extractor)<br>`founder-experiment/website-logo-extractor` | Domain to logo in bulk: best logo URL, favicon set, apple-touch and manifest icons, og:image, site name, theme color. | $0.80 per 1,000 results (site result) + $0.00005 per Actor start (per GB of memory) |
| [NVD CVE Scraper \| $1.5/1k](https://apify.com/founder-experiment/nvd-cve-scraper)<br>`founder-experiment/nvd-cve-scraper` | New and updated CVEs from the NIST NVD API: CVSS 4.0/3.1 scores, severity, CWE, CISA KEV flag, affected products, references. | $1.5 per 1,000 results (cve) + $0.00005 per Actor start (per GB of memory) |

### Market and science data

| Tool (Apify Actor) | What it does | Price (pay per event) |
|---|---|---|
| [SaaSHub Software Alternatives Scraper \| $1.5/1k](https://apify.com/founder-experiment/saashub-alternatives-scraper)<br>`founder-experiment/saashub-alternatives-scraper` | Software alternatives and competitors from SaaSHub: ranked list, votes and rating per product, with CC BY-SA 4.0 source and attribution on every row. | $1.5 per 1,000 results (alternative) + $0.00005 per Actor start (per GB of memory) |
| [Empire Flippers Listings Scraper \| $1.5/1k](https://apify.com/founder-experiment/empire-flippers-listings)<br>`founder-experiment/empire-flippers-listings` | Online businesses for sale on Empire Flippers: price, multiple, profit, revenue, niche, monetization. | $1.5 per 1,000 results (listing) + $0.00005 per Actor start (per GB of memory) |
| [USGS Earthquake Data Scraper: Catalog \| $0.8/1k](https://apify.com/founder-experiment/usgs-earthquake-catalog)<br>`founder-experiment/usgs-earthquake-catalog` | Export earthquakes from the USGS catalog: time, magnitude, place, coordinates, depth, alert, tsunami flag, felt reports. | $0.80 per 1,000 results (earthquake) + $0.00005 per Actor start (per GB of memory) |

## Example prompts

- "Use the US state government jobs tool to list new jobs in Wisconsin."
- "Get every URL from the sitemap of example.com and give me a CSV."
- "Find the logo and favicon for these 20 domains."
- "List new EU TED calls for tender for Germany."

## Files

- [`llms-install.md`](llms-install.md): install steps for AI coding agents.
- [`server.json`](server.json): draft entry for the official MCP Registry (not published yet).
- [`configs/`](configs/): client config snippets.

## License

MIT, see [LICENSE](LICENSE). The Actors themselves are Apify Store listings with their own terms and prices.

## Disclosure

Our own tools, published by Rowfield Data on Apify, built and operated with an AI agent.
Publisher profile: [apify.com/founder-experiment](https://apify.com/founder-experiment).
