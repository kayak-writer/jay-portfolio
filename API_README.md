# Job Finder

Job Finder collects job listings from across the web to highlight open roles that meet specific requirements. Major job search websites do not list every job that employers post — and some of their listings might be out of date or closed. This tool solves these problems by surfacing job posts directly from employer websites.

## Index
* [Overview](#overview)
* [Base URL](#base-url)
* [Authentication](#authentication)
* [Quick Start](#quick-start)
* [Endpoints](#endpoints)
* [Errors](#errors)
* [Rate Limits](#rate-limits)
* [Data Freshness](#data-freshness)
* [Contact](#contact)

## Overview

Job Finder aggregates technical writer, developer advocate, and instructional designer roles directly from employers across the web through platforms such as Greenhouse, Ashby, Lever, HackerNews, and more. Find relevant positions without relying on job boards.

## Base URL

`https://job-scraper.replit.app`

## Authentication

The API uses API key authentication.

`X-API-Key: YOUR_API_KEY`

To request API access, contact the API owner at `jay@technicalwriting.io`. Keys are issued individually and should be stored securely.

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

The following endpoints are available:

* [Status](#status)
* [Jobs](#jobs)
* [Stats](#stats)
* [Locations](#locations)
* [OpenAPI](#openapi)

**Endpoints:**

| Method | Endpoint | Purpose |
| --- | --- | --- |
| GET | `/api/v1/jobs` | Retrieve and filter current job listings |
| GET | `/api/v1/jobs/stats` | Display job totals and platform breakdown | 
| GET | `/api/v1/locations` | Display the number of jobs available in each location |
| GET | `/api/v1/status` | Check the aggregator's latest run |
| GET | `/api/v1/openapi.json` | Download the live API definition |

**Query Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `page` | integer | 1 | Page number for pagination |
| `pageSize` | integer | 50 | Number of results per page (max 100) |
| `searchTerm` | string | — | Filter by a parameter such as job title (e.g., "technical writing") |
| `location` | string | — | Filter by location (e.g., "Remote", "New York, NY") |
| `platform` | string | — | Filter by source platform (e.g., "hackernews", "lever") |
| `isRemote` | boolean | — | Filter to remote-only jobs (`true` or `false`) |
| `sortBy` | string | "postedAt" | Sort by "postedAt" or "scrapedAt" |
| `sortOrder` | string | "desc" | Sort order: "asc" or "desc" |
| `keyword` | string | — | Filter by keyword |

### Status

**Endpoint:** 

Check the scraper status and database metadata.

```bash
curl "https://job-scraper.replit.app/api/v1/status" \
-H "X-API-Key: YOUR_API_KEY"
```

**Response:**

```json

{
    "isRunning": false,
    "lastRunAt": "2026-09-09T00:00:05.096Z",
    "lastRunJobsFound": 116,
    "nextRunAt": null,
    "totalJobs": 151,
    "enabledCompanies": 760
}

```

**Response Fields Explained:**

| Field | Type | Description |
|-------|------|-------------|
| `isRunning` | boolean | Whether scraper is currently running |
| `lastRunAt` | ISO 8601 | Timestamp of most recent scrape |
| `lastRunJobsFound` | integer | Jobs found in last scrape |
| `nextRunAt` | string \| null | When next scrape is scheduled |
| `totalJobs` | integer | Total jobs in database |
| `enabledCompanies` | integer | Number of companies being scraped |

### Jobs

**Endpoint:** 

Retrieve and filter current job listings.

```bash
curl "https://job-scraper.replit.app/api/v1/jobs?searchTerm=technical%20writer&isRemote=true&pageSize=5" \
-H "X-API-Key: YOUR_API_KEY"
```

**Response:**

```json
{
    "jobs": [
        {
            "id": 338,
            "title": "Technical Writer",
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

**Response Fields Explained:**

| Field | Type | Description |
|-------|------|-------------|
| `id` | integer | Unique identifier for the job listing |
| `title` | string | Job title |
| `company` | string | Company name |
| `platform` | string | Source platform (e.g., Greenhouse, Ashby, or Lever) |
| `location` | string | Job location |
| `isRemote` | boolean | Whether the job is remote |
| `salaryRaw` | string \| null | Raw salary from posting (null if not provided) |
| `url` | string | Direct link to the job posting |
| `postedAt` | ISO 8601 | When posted on source platform |
| `scrapedAt` | ISO 8601 | When Job Finder indexed it |
| `searchTerm` | string | Keyword used to find this listing |


### Stats

**Endpoint:** 

Get job listing statistics and breakdowns.

```bash
curl "https://job-scraper.replit.app/api/v1/jobs/stats" \
-H "X-API-Key: YOUR_API_KEY"
```

**Response:**

```json

{
    "total": 151,
    "byPlatform": [
        {
            "platform": "lever",
            "count": 10
        },
        {
            "platform": "smartrecruiters",
            "count": 1
        },
        {
            "platform": "ashby",
            "count": 13
        },
        {
            "platform": "greenhouse",
            "count": 122
        },
        {
            "platform": "hackernews",
            "count": 5
        }
    ],
    "bySearchTerm": [
        {
            "searchTerm": "documentation coordinator",
            "count": 1
        },
        {
            "searchTerm": "documentation manager",
            "count": 3
        },
        {
            "searchTerm": "content designer",
            "count": 4
        },
        {
            "searchTerm": "knowledge management",
            "count": 1
        },
        {
            "searchTerm": "knowledge manager",
            "count": 6
        },
        {
            "searchTerm": "instructional designer",
            "count": 15
        },
        {
            "searchTerm": "documentation engineer",
            "count": 6
        },
        {
            "searchTerm": "technical communications manager",
            "count": 1
        },
        {
            "searchTerm": "developer advocate",
            "count": 43
        },
        {
            "searchTerm": "information architect",
            "count": 1
        },
        {
            "searchTerm": "knowledge engineer",
            "count": 4
        },
        {
            "searchTerm": "content strategist",
            "count": 13
        },
        {
            "searchTerm": "documentation specialist",
            "count": 1
        },
        {
            "searchTerm": "ux writer",
            "count": 3
        },
        {
            "searchTerm": "technical publications manager",
            "count": 3
        },
        {
            "searchTerm": "learning experience designer",
            "count": 5
        },
        {
            "searchTerm": "technical writer",
            "count": 38
        },
        {
            "searchTerm": "developer relations content writer",
            "count": 1
        },
        {
            "searchTerm": "technical content developer",
            "count": 2
        }
    ],
    "remoteCount": 42,
    "lastScrapedAt": "2026-09-09T00:00:05.096Z"
}

```

**Response Fields Explained:**

| Field | Type | Description |
|-------|------|-------------|
| `total` | integer | Total number of jobs indexed |
| `byPlatform` | array | Jobs broken down by source platform |
| `bySearchTerm` | array | Jobs broken down by search term |
| `remoteCount` | integer | Number of remote jobs |
| `lastScrapedAt` | ISO 8601 | Timestamp of last scrape run |

### Locations

**Endpoint:** 

Get all locations with available jobs.

```bash
curl "https://job-scraper.replit.app/api/v1/locations" \
-H "X-API-Key: YOUR_API_KEY"
```

**Response:**

```json

{
    "locations": [
        {
            "location": "Amsterdam, Netherlands; Belgrade, Serbia; Limassol, Cyprus; London, United Kingdom; Madrid, Spain; Prague, Czech Republic; Remote, Germany; Warsaw, Poland; Yerevan, Armenia",
            "count": 1
        },
        {
            "location": "Ashville, Ohio, United States",
            "count": 1
        },
        {
            "location": "Atlanta",
            "count": 1
        },
        {
            "location": "Atlanta, Georgia",
            "count": 1
        },
        {
            "location": "Atlanta, Georgia, United States",
            "count": 1
        },
        {
            "location": "Austin, Texas",
            "count": 1
        },
        {
            "location": "Bangalore, India",
            "count": 4
        },
        {
            "location": "Belgrade, Serbia; Berlin, Germany; Limassol, Cyprus; Madrid, Spain; Munich, Germany; Paphos, Cyprus; Prague, Czech Republic; Remote, Germany; Warsaw, Poland; Yerevan, Armenia",
            "count": 1
        },
        {
            "location": "Bengaluru, India",
            "count": 3
        },
        {
    ]
}

```

Note: The above example was truncated. Call the endpoint for the full list.

**Response Fields Explained:**

| Field | Type | Description |
|-------|------|-------------|
| `location` | string | Job location string |
| `count` | integer | Number of jobs in that location |

### OpenAPI

**Endpoint:** 

Download the live API definition.

```bash
curl "https://job-scraper.replit.app/api/v1/openapi.json" \
-H "X-API-Key: YOUR_API_KEY"
```
**Response:**

``` json
{
  "openapi": "3.1.0",
  "info": {
    "title": "Job Board Public API",
    "version": "1.0.0",
    "description": "Read-only access to job listings collected by the job board scraper. API keys are limited to 10 requests per minute."
  },
  "servers": [
    { "url": "/api/v1", "description": "Public API base path" }
  ],
  "security": [{ "ApiKeyAuth": [] }],
  "paths": {
    "/jobs": {
      "get": {
        "operationId": "listPublicJobs",
        "summary": "List job listings",
        "parameters": [
          { "name": "searchTerm", "in": "query", "schema": { "type": "string" } },
          { "name": "isRemote", "in": "query", "schema": { "type": "string", "enum": ["true", "false"] } },
          { "name": "page", "in": "query", "schema": { "type": "integer", "default": 1, "minimum": 1 } },
          { "name": "pageSize", "in": "query", "schema": { "type": "integer", "default": 50, "maximum": 100 } }
        ],
        "responses": {
          "200": {
            "description": "Paginated job listings",
            "content": {
              "application/json": {
                "schema": { "$ref": "#/components/schemas/JobListResponse" }
              }
            }
          },
          "401": {
            "description": "Missing or invalid API key",
            "content": {
              "application/json": {
                "schema": { "$ref": "#/components/schemas/ErrorResponse" }
              }
            }
          }
        }
      }
    },
    "/status": {
      "get": {
        "operationId": "getPublicScrapeStatus",
        "summary": "Get scraper status",
        "responses": {
          "200": {
            "description": "Scraper status",
            "content": {
              "application/json": {
                "schema": { "$ref": "#/components/schemas/ScrapeStatus" }
              }
            }
          }
        }
      }
    }
  },
  "components": {
    "securitySchemes": {
      "ApiKeyAuth": { "type": "apiKey", "in": "header", "name": "X-API-Key" }
    },
    "schemas": {
      "JobListing": {
        "type": "object",
        "required": ["id", "title", "company", "platform", "url", "scrapedAt"],
        "properties": {
          "id": { "type": "number" },
          "title": { "type": "string" },
          "company": { "type": "string" },
          "isRemote": { "type": "boolean" },
          "url": { "type": "string" }
        }
      }
    }
  }
}

```

The full OpenAPI document — including all five paths, complete parameter lists, and every response schema — is available live at GET /api/v1/openapi.json.

**Response Fields Explained:**

| Field | Type | Description |
|-------|------|-------------|
| `openapi` | string | OpenAPI specification version (e.g., "3.1.0") |
| `info` | object | API metadata, including title, version, and description |
| `servers` | array | Base URL(s) the API is served from |
| `security` | array | Global authentication requirements for the API |
| `paths` | object | All available endpoints, their parameters, and response schemas |
| `components` | object | Reusable schema definitions referenced throughout `paths` |

## Errors

| Status Code | Error Code | Meaning |
| --- | --- | --- |
| 400 | `INVALID_QUERY` | One or more query parameters are invalid |
| 401 | `UNAUTHORIZED` | A valid API key is required |
| 404 | `NOT_FOUND` | The requested public API endpoint does not exist | 
| 429 | `RATE_LIMITED` | The rate limit was exceeded | 
| 500 | `INTERNAL_ERROR` | An unexpected server-side error occurred | 

**Example:**

``` json

 {
     "error": {
       "code": "UNAUTHORIZED",
       "message": "API key is missing or invalid"
     }
   }

```

## Rate Limits

API keys are limited to 10 requests per minute. If you exceed this limit, the API returns `429 RATE_LIMITED`.

## Data Freshness

Job listings are refreshed periodically when a scrape runs. Use `GET /api/v1/status` to check the latest aggregator run.

## Contact

For API access, questions, or feedback, contact `jay@technicalwriting.io`.


