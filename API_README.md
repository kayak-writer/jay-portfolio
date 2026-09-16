# Job Finder

Job Finder aggregates job listings from across the web to highlight technical writing, developer advocate, and Learning & Development (L&D) roles.

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

Job Finder aggregates technical writing, developer advocate, and L&D roles from across the web—Greenhouse, Ashby, Lever, HackerNews, and more. Find relevant positions without manually checking multiple job boards.

## Base URL

https://job-scraper.replit.app

## Authentication

The API uses API-key authentication.

`X-API-Key: YOUR_API_KEY`

To request API access, contact the API owner at ` jay@technicalwriting.io `. Keys are issued individually and should be stored securely.

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
* [OpenAPI](#open-api)

**Endpoints:**

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
| `pageSize` | integer | 50 | Number of results per page (max 100) |
| `searchTerm` | string | — | Filter by job title or keywords (e.g., "technical writing") |
| `location` | string | — | Filter by location (e.g., "Remote", "New York, NY") |
| `platform` | string | — | Filter by source platform (e.g., "hackernews", "remoteok") |
| `company` | string | — | Filter by company name |
| `isRemote` | boolean | — | Filter to remote-only jobs (`true` or `false`) |
| `sortBy` | string | "postedAt" | Sort by "postedAt", "scrapedAt", or "company" |
| `sortOrder` | string | "desc" | Sort order: "asc" or "desc" |

### Status

**Endpoint** 

Check the scraper status and database metadata.

```bash
curl "https://job-scraper.replit.app/api/v1/status" \
-H "X-API-Key: YOUR_API_KEY"
```

**Response**

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

**Response Fields Explained**

| Field | Type | Description |
|-------|------|-------------|
| `isRunning` | boolean | Whether scraper is currently running |
| `lastRunAt` | ISO 8601 | Timestamp of most recent scrape |
| `lastRunJobsFound` | integer | Jobs found in last scrape |
| `nextRunAt` | string \| null | When next scrape is scheduled |
| `totalJobs` | integer | Total jobs in database |
| `enabledCompanies` | integer | Number of companies being scraped |

### Jobs

**Endpoint** 

Retrieve and filter current job listings.

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

**Response Fields Explained**

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

Get job listing statistics and breakdowns.

**Endpoint** 

```bash
curl "https://job-scraper.replit.app/api/v1/jobs/stats" \
-H "X-API-Key: YOUR_API_KEY"
```

**Response**

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

**Response Fields Explained**

| Field | Type | Description |
|-------|------|-------------|
| `total` | integer | Total number of jobs indexed |
| `byPlatform` | array | Jobs broken down by source platform |
| `bySearchTerm` | array | Jobs broken down by search term |
| `remoteCount` | integer | Number of remote jobs |
| `lastScrapedAt` | ISO 8601 | Timestamp of last scrape run |

### Locations

**Endpoint** 

Get all locations with available jobs.

```bash
curl "https://job-scraper.replit.app/api/v1/locations" \
-H "X-API-Key: YOUR_API_KEY"
```

**Response**

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
            "location": "Berlin Office — Berlin, Berlin-Brandenburg, Germany",
            "count": 1
        },
        {
            "location": "Berlin, Germany",
            "count": 1
        },
        {
            "location": "Boston, MA",
            "count": 1
        },
        {
            "location": "Boston, Massachusetts; Foster City, California; Marlton, New Jersey; Remote, United States",
            "count": 1
        },
        {
            "location": "Bucharest",
            "count": 1
        },
        {
            "location": "California - San Francisco",
            "count": 2
        },
        {
            "location": "California, USA, Remote; Colorado, USA, Remote; Illinois, USA, Remote; New York, USA, Remote; Washington, USA, Remote",
            "count": 2
        },
        {
            "location": "California, USA, Remote; Nevada, USA, Remote; Texas, USA, Remote; Washington, USA, Remote",
            "count": 1
        },
        {
            "location": "California, USA, Remote; New York, USA, Remote",
            "count": 1
        },
        {
            "location": "Canada (Remote)",
            "count": 1
        },
        {
            "location": "Costa Mesa, California, United States",
            "count": 18
        },
        {
            "location": "Denver, CO - Louisville",
            "count": 1
        },
        {
            "location": "Dublin",
            "count": 2
        },
        {
            "location": "Düsseldorf",
            "count": 1
        },
        {
            "location": "Europe",
            "count": 1
        },
        {
            "location": "Geneva",
            "count": 1
        },
        {
            "location": "Ghent",
            "count": 1
        },
        {
            "location": "Gurgaon, India",
            "count": 1
        },
        {
            "location": "Gurugram, India",
            "count": 1
        },
        {
            "location": "Hawthorne, CA",
            "count": 2
        },
        {
            "location": "Home based - EMEA",
            "count": 1
        },
        {
            "location": "Lehi, Utah; Raleigh, North Carolina; Santa Clara, California",
            "count": 2
        },
        {
            "location": "London",
            "count": 2
        },
        {
            "location": "london",
            "count": 1
        },
        {
            "location": "London, United Kingdom",
            "count": 1
        },
        {
            "location": "Los Angeles, CA",
            "count": 1
        },
        {
            "location": "Los Angeles, California, United States",
            "count": 1
        },
        {
            "location": "Massachusetts - Boston",
            "count": 2
        },
        {
            "location": "Minneapolis, MN",
            "count": 1
        },
        {
            "location": "Munich area, Germany",
            "count": 1
        },
        {
            "location": "New York City — New York City, New York, United States",
            "count": 1
        },
        {
            "location": "New York City, NY; San Francisco, CA; Seattle, WA",
            "count": 1
        },
        {
            "location": "New York City; Palo Alto; Seattle",
            "count": 1
        },
        {
            "location": "New York, New York",
            "count": 3
        },
        {
            "location": "New York, New York — New York, New York, United States",
            "count": 1
        },
        {
            "location": "New York, New York, United States",
            "count": 1
        },
        {
            "location": "New York, New York, United States; Washington, District of Columbia, United States",
            "count": 1
        },
        {
            "location": "NY_Manhattan_Office",
            "count": 1
        },
        {
            "location": "Oakland, California, United States",
            "count": 1
        },
        {
            "location": "Olympia, WA",
            "count": 1
        },
        {
            "location": "Palo Alto, California",
            "count": 1
        },
        {
            "location": "Prague, Czech Republic",
            "count": 1
        },
        {
            "location": "Prague, Czechia",
            "count": 1
        },
        {
            "location": "Pune, Maharashtra",
            "count": 1
        },
        {
            "location": "Redlands, CA",
            "count": 4
        },
        {
            "location": "Remote",
            "count": 1
        },
        {
            "location": "Remote - Europe",
            "count": 1
        },
        {
            "location": "Remote - US",
            "count": 6
        },
        {
            "location": "Remote - USA",
            "count": 2
        },
        {
            "location": "Remote - USA — United States",
            "count": 1
        },
        {
            "location": "Remote — USA",
            "count": 1
        },
        {
            "location": "Remote Eligible, US",
            "count": 1
        },
        {
            "location": "Remote in the United States — San Francisco, California, United States",
            "count": 1
        },
        {
            "location": "Remote-Friendly (Travel-Required) | San Francisco, CA | Seattle, WA | New York City, NY",
            "count": 1
        },
        {
            "location": "Remote, Colorado, United States, AMER",
            "count": 1
        },
        {
            "location": "Remote, North Carolina, United States, AMER",
            "count": 1
        },
        {
            "location": "Remote, US",
            "count": 1
        },
        {
            "location": "Remote, USA",
            "count": 1
        },
        {
            "location": "Remote: San Mateo area",
            "count": 1
        },
        {
            "location": "San Francisco",
            "count": 1
        },
        {
            "location": "San Francisco — San Francisco, California, United States",
            "count": 1
        },
        {
            "location": "San Francisco, CA",
            "count": 2
        },
        {
            "location": "San Francisco, CA | New York City, NY",
            "count": 3
        },
        {
            "location": "San Francisco, CA or Remote, US ",
            "count": 1
        },
        {
            "location": "San Francisco, California",
            "count": 7
        },
        {
            "location": "San Francisco, California, United States",
            "count": 1
        },
        {
            "location": "San Jose, CR",
            "count": 1
        },
        {
            "location": "San Mateo, CA, United States",
            "count": 1
        },
        {
            "location": "Santa Clara, CALIFORNIA, United States",
            "count": 1
        },
        {
            "location": "São Paulo, Brazil",
            "count": 1
        },
        {
            "location": "Seattle, Washington",
            "count": 2
        },
        {
            "location": "Senior Sales Engineer, Sales Engineer",
            "count": 1
        },
        {
            "location": "Seoul",
            "count": 1
        },
        {
            "location": "Seoul, South Korea",
            "count": 1
        },
        {
            "location": "Singapore, Singapore",
            "count": 1
        },
        {
            "location": "Staff Backend Engineer, Founding DevRel, Founder's Associate",
            "count": 1
        },
        {
            "location": "Tel Aviv",
            "count": 2
        },
        {
            "location": "Tel Aviv/ Netanya, Israel",
            "count": 1
        },
        {
            "location": "Tokyo, Japan",
            "count": 1
        },
        {
            "location": "Toronto",
            "count": 1
        },
        {
            "location": "Toronto, Ontario, Canada",
            "count": 2
        },
        {
            "location": "United States",
            "count": 3
        },
        {
            "location": "United States (Remote)",
            "count": 1
        },
        {
            "location": "United States of America",
            "count": 1
        },
        {
            "location": "US Remote",
            "count": 1
        },
        {
            "location": "US-Based / Remote",
            "count": 1
        },
        {
            "location": "US, Remote",
            "count": 1
        },
        {
            "location": "Vienna, Virginia, United States",
            "count": 1
        }
    ]
}

```

**Response Fields Explained**

| Field | Type | Description |
|-------|------|-------------|
| `location` | string | Job location string |
| `count` | integer | Number of jobs in that location |

### Open API

**Endpoint** 

Download the full OpenAPI 3.1.0 specification.

```bash
curl "https://job-scraper.replit.app/api/v1/openapi.json" \
-H "X-API-Key: YOUR_API_KEY"
```
**Response**

``` json

{
    "openapi": "3.1.0",
    "info": {
        "title": "Job Board Public API",
        "version": "1.0.0",
        "description": "Read-only access to job listings collected by the job board scraper. API keys are limited to 10 requests per minute."
    },
    "servers": [
        {
            "url": "/api/v1",
            "description": "Public API base path"
        }
    ],
    "security": [
        {
            "ApiKeyAuth": []
        }
    ],
    "paths": {
        "/jobs": {
            "get": {
                "operationId": "listPublicJobs",
                "summary": "List job listings",
                "parameters": [
                    {
                        "name": "keyword",
                        "in": "query",
                        "schema": {
                            "type": "string"
                        }
                    },
                    {
                        "name": "platform",
                        "in": "query",
                        "schema": {
                            "type": "string",
                            "enum": [
                                "lever",
                                "greenhouse",
                                "adp",
                                "ashby",
                                "smartrecruiters",
                                "workday",
                                "hackernews",
                                "workable"
                            ]
                        }
                    },
                    {
                        "name": "location",
                        "in": "query",
                        "schema": {
                            "type": "string"
                        }
                    },
                    {
                        "name": "isRemote",
                        "in": "query",
                        "schema": {
                            "type": "string",
                            "enum": [
                                "true",
                                "false"
                            ]
                        }
                    },
                    {
                        "name": "searchTerm",
                        "in": "query",
                        "schema": {
                            "type": "string"
                        }
                    },
                    {
                        "name": "page",
                        "in": "query",
                        "schema": {
                            "type": "integer",
                            "default": 1,
                            "minimum": 1
                        }
                    },
                    {
                        "name": "pageSize",
                        "in": "query",
                        "schema": {
                            "type": "integer",
                            "default": 50,
                            "minimum": 1,
                            "maximum": 100
                        }
                    },
                    {
                        "name": "sortBy",
                        "in": "query",
                        "schema": {
                            "type": "string",
                            "enum": [
                                "postedAt",
                                "scrapedAt"
                            ]
                        }
                    },
                    {
                        "name": "sortOrder",
                        "in": "query",
                        "schema": {
                            "type": "string",
                            "enum": [
                                "asc",
                                "desc"
                            ]
                        }
                    }
                ],
                "responses": {
                    "200": {
                        "description": "Paginated job listings",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/JobListResponse"
                                }
                            }
                        }
                    },
                    "400": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "401": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "404": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "429": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "500": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    }
                }
            }
        },
        "/jobs/stats": {
            "get": {
                "operationId": "getPublicJobStats",
                "summary": "Get job listing statistics",
                "responses": {
                    "200": {
                        "description": "Job statistics",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/JobStats"
                                }
                            }
                        }
                    },
                    "401": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "404": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "429": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "500": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    }
                }
            }
        },
        "/locations": {
            "get": {
                "operationId": "getPublicJobLocations",
                "summary": "List available job locations",
                "responses": {
                    "200": {
                        "description": "Distinct job locations with listing counts",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/JobLocationsResponse"
                                }
                            }
                        }
                    },
                    "401": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "404": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "429": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "500": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
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
                                "schema": {
                                    "$ref": "#/components/schemas/ScrapeStatus"
                                }
                            }
                        }
                    },
                    "401": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "404": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "429": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "500": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    }
                }
            }
        },
        "/openapi.json": {
            "get": {
                "operationId": "getPublicOpenApiSpec",
                "summary": "Get the OpenAPI document",
                "responses": {
                    "200": {
                        "description": "OpenAPI document",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "type": "object"
                                }
                            }
                        }
                    },
                    "401": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "404": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "429": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    },
                    "500": {
                        "description": "Error response",
                        "content": {
                            "application/json": {
                                "schema": {
                                    "$ref": "#/components/schemas/ErrorResponse"
                                }
                            }
                        }
                    }
                }
            }
        }
    },
    "components": {
        "securitySchemes": {
            "ApiKeyAuth": {
                "type": "apiKey",
                "in": "header",
                "name": "X-API-Key"
            }
        },
        "schemas": {
            "JobListing": {
                "type": "object",
                "required": [
                    "id",
                    "title",
                    "company",
                    "platform",
                    "url",
                    "scrapedAt"
                ],
                "properties": {
                    "id": {
                        "type": "number"
                    },
                    "title": {
                        "type": "string"
                    },
                    "company": {
                        "type": "string"
                    },
                    "platform": {
                        "type": "string",
                        "enum": [
                            "lever",
                            "greenhouse",
                            "adp",
                            "ashby",
                            "smartrecruiters",
                            "workday",
                            "hackernews",
                            "workable"
                        ]
                    },
                    "location": {
                        "type": [
                            "string",
                            "null"
                        ]
                    },
                    "isRemote": {
                        "type": "boolean"
                    },
                    "salaryRaw": {
                        "type": [
                            "string",
                            "null"
                        ]
                    },
                    "url": {
                        "type": "string"
                    },
                    "postedAt": {
                        "type": [
                            "string",
                            "null"
                        ]
                    },
                    "scrapedAt": {
                        "type": "string"
                    },
                    "searchTerm": {
                        "type": "string"
                    }
                }
            },
            "JobListResponse": {
                "type": "object",
                "required": [
                    "jobs",
                    "total",
                    "page",
                    "pageSize"
                ],
                "properties": {
                    "jobs": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/JobListing"
                        }
                    },
                    "total": {
                        "type": "number"
                    },
                    "page": {
                        "type": "number"
                    },
                    "pageSize": {
                        "type": "number"
                    }
                }
            },
            "JobStats": {
                "type": "object",
                "required": [
                    "total",
                    "byPlatform",
                    "bySearchTerm",
                    "remoteCount",
                    "lastScrapedAt"
                ],
                "properties": {
                    "total": {
                        "type": "number"
                    },
                    "byPlatform": {
                        "type": "array",
                        "items": {
                            "type": "object",
                            "required": [
                                "platform",
                                "count"
                            ],
                            "properties": {
                                "platform": {
                                    "type": "string"
                                },
                                "count": {
                                    "type": "number"
                                }
                            }
                        }
                    },
                    "bySearchTerm": {
                        "type": "array",
                        "items": {
                            "type": "object",
                            "required": [
                                "searchTerm",
                                "count"
                            ],
                            "properties": {
                                "searchTerm": {
                                    "type": "string"
                                },
                                "count": {
                                    "type": "number"
                                }
                            }
                        }
                    },
                    "remoteCount": {
                        "type": "number"
                    },
                    "lastScrapedAt": {
                        "type": [
                            "string",
                            "null"
                        ]
                    }
                }
            },
            "JobLocationsResponse": {
                "type": "object",
                "required": [
                    "locations"
                ],
                "properties": {
                    "locations": {
                        "type": "array",
                        "items": {
                            "type": "object",
                            "required": [
                                "location",
                                "count"
                            ],
                            "properties": {
                                "location": {
                                    "type": "string"
                                },
                                "count": {
                                    "type": "number"
                                }
                            }
                        }
                    }
                }
            },
            "ScrapeStatus": {
                "type": "object",
                "required": [
                    "isRunning",
                    "totalJobs",
                    "enabledCompanies"
                ],
                "properties": {
                    "isRunning": {
                        "type": "boolean"
                    },
                    "lastRunAt": {
                        "type": [
                            "string",
                            "null"
                        ]
                    },
                    "lastRunJobsFound": {
                        "type": [
                            "number",
                            "null"
                        ]
                    },
                    "nextRunAt": {
                        "type": [
                            "string",
                            "null"
                        ]
                    },
                    "totalJobs": {
                        "type": "number"
                    },
                    "enabledCompanies": {
                        "type": "number"
                    }
                }
            },
            "ErrorResponse": {
                "type": "object",
                "required": [
                    "error"
                ],
                "properties": {
                    "error": {
                        "type": "object",
                        "required": [
                            "code",
                            "message"
                        ],
                        "properties": {
                            "code": {
                                "type": "string"
                            },
                            "message": {
                                "type": "string"
                            }
                        }
                    }
                }
            }
        }
    }
}

```

**Response Fields Explained**

Returns the full OpenAPI 3.1.0 specification document for the API.
This can be imported into Postman, Swagger UI, or other API tools for interactive documentation and testing.

## Errors

| Status Code | Error Code | Meaning |
| --- | --- | --- |
| 400 | `INVALID_QUERY` | One or more query parameters are invalid. |
| 401 | `UNAUTHORIZED` | A valid API key is required. |
| 404 | `NOT_FOUND` | The requested public API endpoint does not exist. | 
| 429 | `RATE_LIMITED` | The rate limit was exceeded. | 
| 500 | `INTERNAL_ERROR` | An unexpected server-side error occurred. | 

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


