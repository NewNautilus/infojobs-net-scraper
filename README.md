[Infojobs Net Scraper](https://apify.com/unfenced-group/infojobs-net-scraper?fpr=data)

![InfoJobs Scraper](https://images.apifyusercontent.com/ctnrCwV9j2g1PD1wsWfDBhIc14hMvRLKVaw7J785sso/w:1800/cb:1/aHR0cHM6Ly9pLmltZ3VyLmNvbS9IUzJZVFdRLnBuZw.webp)

# InfoJobs Scraper — Spain Jobs

Extract structured job listings from [InfoJobs.net](https://www.infojobs.net), Spain's largest employment platform with over 3 million registered professionals. Get titles, companies, locations, work modes, contract types, full descriptions, and more — no API key required.

## Features

- **Full job descriptions** included directly from search results — no extra requests per listing
- **All 50 Spanish provinces** supported via name or ID
- **Incremental runs** with 90-day cross-run deduplication to skip previously seen jobs
- **Date filtering** to retrieve only recent listings (1, 7, 15, or 30 days)
- **Pagination** automatically handles all result pages up to your `maxResults` limit

## Output fields

| Field | Description |
| --- | --- |
| `id` | Unique job identifier |
| `url` | Direct link to the job listing |
| `title` | Job title |
| `company` | Hiring company name |
| `companyUrl` | Company profile link |
| `city` | City or region |
| `workMode` | `Remote`, `Hybrid`, or `On-site` |
| `contractType` | Contract type (e.g. `Contrato indefinido`) |
| `workSchedule` | Work schedule (e.g. `Jornada completa`) |
| `publishDate` | Publication date (ISO 8601) |
| `daysOld` | Days since publication |
| `descriptionText` | Full job description (plain text) |
| `descriptionHtml` | Full job description (HTML) |
| `descriptionMarkdown` | Full job description (Markdown) |
| `isFeatured` | Whether the listing is promoted |
| `applyUrl` | Application link |
| `isRepost` | Whether this job was seen in a previous run |
| `scrapedAt` | Timestamp of data collection |

## Input parameters

| Parameter | Type | Description |
| --- | --- | --- |
| `searchQuery` | String | Keywords to search (e.g. `developer`, `enfermero`) |
| `location` | String | Province name (e.g. `Madrid`, `Barcelona`, `Sevilla`) or leave empty for all Spain |
| `maxResults` | Integer | Maximum results to return (default: `100`) |
| `daysOld` | Integer | Only return jobs posted within N days (1, 7, 15, or 30) |
| `skipReposts` | Boolean | Skip jobs already seen in previous runs |
| `startUrls` | Array | Optional InfoJobs search page URLs to scrape directly |

## Example input

```
{
  "searchQuery": "data engineer",
  "location": "Barcelona",
  "maxResults": 200,
  "daysOld": 7,
  "skipReposts": true
}
```

## Usage notes

- Results are sorted by **relevance** by default, or by **publication date** when `daysOld` is set
- `startUrls` accepts InfoJobs search page URLs (e.g. from your own filtered search on the website)
- The deduplication store persists for 90 days across runs — ideal for scheduled daily/weekly scrapes
- Province names are matched flexibly: `Madrid`, `madrid`, `MADRID` all work

## Use cases

- **Recruitment analytics** — track hiring trends across Spanish industries
- **Salary benchmarking** — collect compensation data by role and region
- **Job aggregation** — feed listings into your own platform or database
- **Market research** — monitor competitor hiring activity and skill demand

## Pricing

This actor uses **Pay-Per-Result** pricing: **$1.49 per 1,000 results**. A typical run fetching 500 jobs costs approximately $0.75.

---

*Data is collected from publicly available job listings on InfoJobs.net. Only public information is extracted — no personal data of candidates or private employer information.*