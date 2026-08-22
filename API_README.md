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

For API access, questions, or feedback, contact ` jay@technicalwriting.io `.


