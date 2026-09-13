# Job Finder

Job Finder aggregates job listings from across the web to highlight technical writing, developer advocate, and Learning & Development (L&D) roles.

## Overview

This Application Programming Interface (API) seeks to streamline the job application process by making it easier to find open roles.

## Base URL

https://job-scraper.replit.app

## Authentication

The API uses API-key authentication.

`X-API-Key: YOUR_API_KEY`

To request API access, contact the API owner ` jay@technicalwriting.io `. Keys are issued individually and should be stored securely.

## Quick Start

Make your first request:

```bash
curl "https://job-scraper.replit.app/api/v1/jobs?pageSize=1" \
-H "X-API-Key: YOUR_API_KEY"
```

A successful response returns a jobs array and pagination details:

```json

{
    "jobs": [
        {
            "id": 236,
            "title": "Technical content developer",
            "company": "Klara Systems",
            "platform": "hackernews",
            "location": "Remote",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://news.ycombinator.com/item?id=49161851",
            "postedAt": "2026-08-03T21:43:16.000Z",
            "scrapedAt": "2026-08-19T20:04:53.339Z",
            "searchTerm": "technical content developer"
        }
     ],
    "total": 1,
    "page": 1,
    "pageSize": 1
}

```

## Endpoints

Job Finder's public API lets you retrieve current job listings, review statistics and location counts, check the aggregator status, and download the live API definition. Every endpoint requires an `X-API-Key` header.

| Method | Endpoint | Purpose |
| --- | --- | --- |
| GET | `/api/v1/jobs` | Retrieve and filter current job listings. |
| GET | `/api/v1/jobs/stats` | Display job totals and platform breakdown. | 
| GET | `/api/v1/locations` | Display the number of jobs available in each location. |
| GET | `/api/v1/status` | Check the aggregator's latest run. |
| GET | `/api/v1/openapi.json` | Download the API definition. |

**Query Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `page` | integer | 1 | Page number for pagination |
| `pageSize` | integer | 20 | Number of results per page (max 100) |
| `searchTerm` | string | — | Filter by job title or keywords (e.g., "technical writing") |
| `location` | string | — | Filter by location (e.g., "Remote", "New York, NY") |
| `platform` | string | — | Filter by source platform (e.g., "hackernews", "remoteok") |
| `company` | string | — | Filter by company name |
| `isRemote` | boolean | — | Filter to remote-only jobs (`true` or `false`) |
| `sortBy` | string | "postedAt" | Sort by "postedAt", "scrapedAt", or "company" |
| `sortOrder` | string | "desc" | Sort order: "asc" or "desc" |

**Example Request (Technical Writer roles that offer remote work):**
```bash
curl "https://job-scraper.replit.app/api/v1/jobs?searchTerm=technical%20writer&isRemote=true&pageSize=5" \
-H "X-API-Key: YOUR_API_KEY"
```

**Response**

```json
{
    "jobs": [
        {
            "id": 338,
            "title": "Technical Writer ",
            "company": "deepnote",
            "platform": "ashby",
            "location": "Remote — USA",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://jobs.ashbyhq.com/deepnote/eb00d9b0-0dfc-4ff7-9aa4-19cf22e9644c",
            "postedAt": "2026-03-20T17:30:39.706Z",
            "scrapedAt": "2026-08-25T04:23:46.280Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 687,
            "title": "Senior Technical Writer (Data Documentation)",
            "company": "jetbrains",
            "platform": "greenhouse",
            "location": "Belgrade, Serbia; Berlin, Germany; Limassol, Cyprus; Madrid, Spain; Munich, Germany; Paphos, Cyprus; Prague, Czech Republic; Remote, Germany; Warsaw, Poland; Yerevan, Armenia",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://job-boards.eu.greenhouse.io/jetbrains/jobs/4860224101",
            "postedAt": "2026-08-20T16:59:01.000Z",
            "scrapedAt": "2026-08-25T04:23:40.080Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 545,
            "title": "Technical Writer",
            "company": "pantheon",
            "platform": "greenhouse",
            "location": "United States (Remote)",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://pantheon.io/about/careers/detail?gh_jid=8077481",
            "postedAt": "2026-07-31T15:29:15.000Z",
            "scrapedAt": "2026-08-06T03:01:50.464Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 471,
            "title": "Technical Writer, Docs Content",
            "company": "stripe",
            "platform": "greenhouse",
            "location": "US Remote",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://stripe.com/jobs/search?gh_jid=8036155",
            "postedAt": "2026-08-05T17:44:32.000Z",
            "scrapedAt": "2026-08-06T03:01:50.310Z",
            "searchTerm": "technical writer"
        }
    ],
    "total": 4,
    "page": 1,
    "pageSize": 50
}
```

**More Examples:**

Filter by Platform (Hacker News only):
```bash
curl
"https://job-scraper.replit.app/api/v1/jobs?platform=hackernews&pageSize=10 \
-H "X-API-Key: YOUR_API_KEY"
```

Filter by Location and Company:
``` bash
curl
"https://job-scraper.replit.app/api/v1/jobs?location=Boston&company=Starburst \
-H "X-API-Key: YOUR_API_KEY"
```

---

## Errors

| Status Code | Error Code | Meaning |
| --- | --- | --- |
| 400 | `INVALID_QUERY` | One or more query parameters are invalid. |
| 401 | `UNAUTHORIZED` | A valid API key is required. |
| 404 | `NOT_FOUND` | The requested public API endpoint does not exist. | 
| 429 | `RATE_LIMITED` | The rate limit was exceeded. | 
| 500 | `INTERNAL_ERROR` | An unexpected server-side error occurred. | 

## Rate Limits

API keys are limited to 60 requests per minute. If you exceed this limit, the API returns `429 RATE_LIMITED`.

## Data Freshness

Job listings are refreshed periodically when a scrape runs. Use `GET /api/v1/status` to check the latest aggregator run.

## Contact

For API access, questions, or feedback, contact `jay@technicalwriting.io`.


