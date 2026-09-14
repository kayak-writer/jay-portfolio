# RowFinder

RowFinder lists hotel fitness centers that have rowing machines, including Concept2 and Hydrow ergs.

## Index
* [Overview](#overview)
* [Base URL](#base-url)
* [Quick Start](#quick-start)
* [Endpoints](#endpoints)
* [Errors](#errors)
* [Rate Limits](#rate-limits)
* [Data Freshness](#data-freshness)
* [Contact](#contact)

## Overview

RowFinder makes it easier to find hotels that have rowing machines by providing a single directory that is brand agnostic. 

## Base Url

https://rowfinder.xyz

## Quick Start

Make your first request

```bash
curl "https://rowfinder.xyz/api/v1/hotels"
```

A sucessfull response contains a hotels array:

``` json
{
    "data": [
        {
            "id": 22,
            "name": "The Whitney Hotel",
            "city": "Boston, MA",
            "brand": "hydrow",
            "model": null,
            "notes": "Hydrow in the fitness center.",
            "votes": 1,
            "createdAt": 1783388038
        },
        {
            "id": 21,
            "name": "Axiom Hotel",
            "city": "San Francisco, CA",
            "brand": "concept2",
            "model": "RowErg",
            "notes": "1 Concept2 RowErg in our 24/7 Core Fitness Center.",
            "votes": 1,
            "createdAt": 1783025239
        },
        {
            "id": 20,
            "name": "Beacon Grand, A Union Square Hotel",
            "city": "San Francisco, CA",
            "brand": "other",
            "model": "Origin Rower",
            "notes": "One Rower in the Fitness Studio, guest access 24h.",
            "votes": 1,
            "createdAt": 1783011746
        },
        {
            "id": 19,
            "name": "InterContinental Boston",
            "city": "Boston, MA",
            "brand": "technogym",
            "model": null,
            "notes": "2 Technogym rowers.",
            "votes": 1,
            "createdAt": 1782533327
        },
        {
            "id": 18,
            "name": "Huntington Hotel",
            "city": "San Francisco, CA",
            "brand": "peloton",
            "model": null,
            "notes": "One rower in the fitness center.",
            "votes": 1,
            "createdAt": 1782522832
        },
        {
            "id": 17,
            "name": "Park Hyatt Chicago",
            "city": "Chicago, IL",
            "brand": "peloton",
            "model": null,
            "notes": "For hotel guests only. Open 24/7.",
            "votes": 1,
            "createdAt": 1782417277
        },
        {
            "id": 5,
            "name": "Radisson Blu Atlantic Hotel",
            "city": "Stavanger, Norway",
            "brand": "other",
            "model": "Technogym Skillrow",
            "notes": "One machine plus spin bike and some other bits. Gym has with amazing view of city. 12th floor. Open 0600-2000hrs.",
            "votes": 1,
            "createdAt": 1781905715
        },
        {
            "id": 4,
            "name": "Fairmont Washington D.C. Georgetown",
            "city": "Washington, DC",
            "brand": "concept2",
            "model": null,
            "notes": "About a dozen Concept2s in the Balance Gym",
            "votes": 1,
            "createdAt": 1781822870
        }
    ],
    "pagination": {
        "page": 1,
        "limit": 20,
        "total": 8,
        "totalPages": 1,
        "hasNextPage": false,
        "hasPreviousPage": false
    }
}

```

### Endpoints

RowFinder allows you to retrieve listings of hotels with rowing machines, review statistics and location counts, check the listing status, and download the live API definition.

The following endpoints are available:

* [Heatlh](#health)
* [Hotels](#hotels)
* [Stats](#stats)
* [Brands](#brands)
* [Cities](#cities)

**Endpoints**

| Method | Endpoint | Purpose |
| --- | --- | --- |
| GET | `/api/v1/healthz` | Checks API health. |
| GET | `/api/v1/hotels` | List approved hotels. | 
| GET | `/api/v1/stats` | Get approved hotel totals and brand counts. |
| GET | `/api/v1/brands` | 	List brands and hotel counts. |
| GET | `/api/v1/cities` | 	List cities and hotel counts. |

**Query Parameters**

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `search` | string | - | Filter city names |
| `page` | integer | - | Page number; defaults to `1` |
| `limit` | integer | - | 	Results per page; defaults to `20`, maximum `100` |

