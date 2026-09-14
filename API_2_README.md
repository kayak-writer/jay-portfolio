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

* [Heatlh](#healthz)
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

### Healthz

**Endpoint**

Check the directory status and database metadata.

```bash
curl "https://rowfinder.xyz/api/v1/healthz"
```

**Response**

```json

{
    "status": "ok",
    "service": "rowfinder-api",
    "version": "v1"
}

```

**Response Fields Explained**

| Field | Type | Description |
| --- | --- | ---|
| Status | String | Current health status of the API. The value ` "ok" ` indicates that the service is running and responding normally. |
| Service | String | Name of the service returning the response. This identifies the service as `rowfinder-api`. |
| Version | String | Version of the public API responding to the request. The current version is `v1`. |

### Hotels

**Endpoint**

Retrieve a listing of hotels.

```bash
curl "https://rowfinder.xyz/api/v1/hotels"
```

**Response**

```json

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

**Response Fields Explained**

| Field | Type | Description |
| --- | --- | --- | 
| `id` | number | Unique hotel identifier 
| `name` | string | Hotel name 
| `city` | string | City and region or country, such as `Boston, MA.` 
| `brand` | string | Normalized rowing-machine brand identifier, such as `"hydrow"` or `"concept2"`. 
| `model` | string  or null | Specific machine model when known. `null` means no model was provided. 
| `notes` | string or null | Additional information about the equipment or gym. `null` means no notes were provided. 
| `votes` | number | Number of upvotes the hotel has received. 
| `createdAt` | number | Unix timestamp in seconds indicating when the listing was created. 

### Stats

**Endpoint**

Retrieves statistics for the listing of hotels.

```bash
curl "https://rowfinder.xyz/api/v1/stats"
```

**Response**

``` json

{
    "data": {
        "total": 8,
        "cities": 5,
        "byBrand": [
            {
                "brand": "concept2",
                "total": 2
            },
            {
                "brand": "other",
                "total": 2
            },
            {
                "brand": "peloton",
                "total": 2
            },
            {
                "brand": "hydrow",
                "total": 1
            },
            {
                "brand": "technogym",
                "total": 1
            }
        ]
    }
}

```
**Response Fields Explained**

| Field | Type | Description |
| --- | --- | --- | 
| `data.total` | number | Total number of approved hotels
| `cities` | number | Total number of cities covered
| `brand` | string | Brand name of erg (e.g., Concept 2 or Hydrow)
| `byBrand.total` | number | Total number of each brand (e.g., Concept 2 or Hydrow)

### Brands

**Endpoint**

Retrieves statistics for the listing of hotels.

```bash
curl "https://rowfinder.xyz/api/v1/brands"
```

**Response**

```json

{
    "data": [
        {
            "brand": "concept2",
            "total": 2
        },
        {
            "brand": "hydrow",
            "total": 1
        },
        {
            "brand": "aviron",
            "total": 0
        },
        {
            "brand": "nordictrack",
            "total": 0
        },
        {
            "brand": "ergatta",
            "total": 0
        },
        {
            "brand": "sunny",
            "total": 0
        },
        {
            "brand": "waterrower",
            "total": 0
        },
        {
            "brand": "peloton",
            "total": 2
        },
        {
            "brand": "technogym",
            "total": 1
        },
        {
            "brand": "other",
            "total": 2
        },
        {
            "brand": "unknown",
            "total": 0
        }
    ]
}

```

**Response Fields Explained**

| Field | Type | Description |
| --- | --- | --- | 
| `data.brand` | number | Brand name | (e.g., Concept 2 or Hydrow)
| `data.total` | number | Total number of each brand of erg (e.g., Concept 2 or Hydrow)


### Cities

**Endpoint**

Retrieves statistics for the listing of hotels.

```bash
curl "https://rowfinder.xyz/api/v1/Cities"
```

**Responses**

```json

{
    "data": [
        {
            "city": "San Francisco, CA",
            "total": 3
        },
        {
            "city": "Boston, MA",
            "total": 2
        },
        {
            "city": "Chicago, IL",
            "total": 1
        },
        {
            "city": "Stavanger, Norway",
            "total": 1
        },
        {
            "city": "Washington, DC",
            "total": 1
        }
    ],
    "pagination": {
        "page": 1,
        "limit": 20,
        "total": 5,
        "totalPages": 1,
        "hasNextPage": false,
        "hasPreviousPage": false
    }
}

```

**Response Fields Explained**

| Field | Type | Description |
| --- | --- | --- | 
| `data.city` | number | City name
| `data.total` | number | Total number of listed ergs in each city

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

IPs are limited to 120 requests per minute. If you exceed this limit, the API returns `429 RATE_LIMITED`.

## Data Freshness

New listings display as soon as a listing is approved. Use `GET /api/v1/healthZ` to check the latest run.

## Contact

For questions or feedback, contact `jay@technicalwriting.io`.
