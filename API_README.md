# Job Finder API

Job Finder collects job listings from across the web to highlight open roles that meet specific requirements. Major job search websites do not list every job that employers post — and some of their listings might be out of date or closed. This tool solves these problems by surfacing job posts directly from employer websites and niche sites like Hacker News.

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
curl "https://job-scraper.replit.app/api/v1/jobs" \
-H "X-API-Key: YOUR_API_KEY"
```

A successful response returns a jobs array and pagination details:

```json

{
    "jobs": [
        {
            "id": 876,
            "title": "Technical content developer",
            "company": "Klara Systems",
            "platform": "hackernews",
            "location": "Remote",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://news.ycombinator.com/item?id=49161851",
            "postedAt": "2026-08-03T21:43:16.000Z",
            "scrapedAt": "2026-08-25T04:23:47.780Z",
            "searchTerm": "technical content developer"
        },
        {
            "id": 878,
            "title": "Developer advocate",
            "company": "Checkly",
            "platform": "hackernews",
            "location": "Senior Sales Engineer, Sales Engineer",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://news.ycombinator.com/item?id=49157129",
            "postedAt": "2026-08-03T15:31:37.000Z",
            "scrapedAt": "2026-08-25T04:23:47.580Z",
            "searchTerm": "developer advocate"
        },
        {
            "id": 877,
            "title": "Staff Backend Engineer, Founding DevRel, Founder's Associate",
            "company": "Nango",
            "platform": "hackernews",
            "location": "Staff Backend Engineer, Founding DevRel, Founder's Associate",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://news.ycombinator.com/item?id=49168047",
            "postedAt": "2026-08-04T12:45:22.000Z",
            "scrapedAt": "2026-08-25T04:23:47.480Z",
            "searchTerm": "developer advocate"
        },
        {
            "id": 1067,
            "title": "Developer relations content writer",
            "company": "Estuary",
            "platform": "hackernews",
            "location": "US-Based / Remote",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://news.ycombinator.com/item?id=49198416",
            "postedAt": "2026-08-06T15:56:05.000Z",
            "scrapedAt": "2026-08-25T04:23:47.280Z",
            "searchTerm": "developer relations content writer"
        },
        {
            "id": 875,
            "title": "Developer Relations",
            "company": "Friendly Captcha",
            "platform": "hackernews",
            "location": "Munich area, Germany",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://news.ycombinator.com/item?id=49159002",
            "postedAt": "2026-08-03T17:38:48.000Z",
            "scrapedAt": "2026-08-25T04:23:47.180Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1282,
            "title": "Developer Advocate",
            "company": "greptile",
            "platform": "ashby",
            "location": "San Francisco — San Francisco, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://jobs.ashbyhq.com/greptile/294bbe1d-5a40-4aec-ab3c-517832e8f2b8",
            "postedAt": "2026-08-24T21:10:28.795Z",
            "scrapedAt": "2026-08-25T04:23:46.880Z",
            "searchTerm": "developer advocate"
        },
        {
            "id": 707,
            "title": " Senior Instructional Designer",
            "company": "synthesia",
            "platform": "ashby",
            "location": "New York City — New York City, New York, United States",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://jobs.ashbyhq.com/synthesia/a1f0d6c0-7a9a-483d-84a7-e8a4ffb8eee9",
            "postedAt": "2026-08-04T16:52:32.961Z",
            "scrapedAt": "2026-08-25T04:23:46.780Z",
            "searchTerm": "instructional designer"
        },
        {
            "id": 706,
            "title": "Content Creator & Strategist",
            "company": "elevenlabs",
            "platform": "ashby",
            "location": "United States",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://jobs.ashbyhq.com/elevenlabs/13fcee94-512f-4229-b7ab-f91d3fdd24e3",
            "postedAt": "2026-07-30T16:42:21.475Z",
            "scrapedAt": "2026-08-25T04:23:46.581Z",
            "searchTerm": "content strategist"
        },
        {
            "id": 1062,
            "title": "Senior Developer Advocate ",
            "company": "runpod",
            "platform": "ashby",
            "location": "Remote - USA — United States",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://jobs.ashbyhq.com/runpod/8e907491-3242-47ba-8de4-f7e3017e607b",
            "postedAt": "2026-08-07T19:12:55.615Z",
            "scrapedAt": "2026-08-25T04:23:46.480Z",
            "searchTerm": "developer advocate"
        },
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
            "id": 337,
            "title": "Senior Developer Advocate",
            "company": "sanity",
            "platform": "ashby",
            "location": "Remote in the United States — San Francisco, California, United States",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://jobs.ashbyhq.com/sanity/11b54218-44f5-4cec-bc66-9abfb140f3c5",
            "postedAt": "2026-05-26T19:10:34.935Z",
            "scrapedAt": "2026-08-25T04:23:46.080Z",
            "searchTerm": "developer advocate"
        },
        {
            "id": 1271,
            "title": "Senior Content Strategist (Term-Limited)",
            "company": "aclu",
            "platform": "greenhouse",
            "location": "New York, New York, United States; Washington, District of Columbia, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://job-boards.greenhouse.io/aclu/jobs/8516657002",
            "postedAt": "2026-05-04T18:47:47.000Z",
            "scrapedAt": "2026-08-25T04:23:45.980Z",
            "searchTerm": "content strategist"
        },
        {
            "id": 1270,
            "title": "Quality Assurance and Documentation Manager",
            "company": "verramobility",
            "platform": "greenhouse",
            "location": "NY_Manhattan_Office",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://job-boards.greenhouse.io/verramobility/jobs/4677111006",
            "postedAt": "2026-08-21T17:05:12.000Z",
            "scrapedAt": "2026-08-25T04:23:45.780Z",
            "searchTerm": "documentation manager"
        },
        {
            "id": 1269,
            "title": "Learning Experience Designer",
            "company": "metropolis",
            "platform": "greenhouse",
            "location": "New York, New York, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://job-boards.greenhouse.io/metropolis/jobs/7782384003",
            "postedAt": "2026-07-28T21:08:59.000Z",
            "scrapedAt": "2026-08-25T04:23:45.580Z",
            "searchTerm": "learning experience designer"
        },
        {
            "id": 1268,
            "title": "Learning Experience Designer",
            "company": "metropolis",
            "platform": "greenhouse",
            "location": "Los Angeles, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://job-boards.greenhouse.io/metropolis/jobs/7782388003",
            "postedAt": "2026-07-28T21:09:45.000Z",
            "scrapedAt": "2026-08-25T04:23:45.537Z",
            "searchTerm": "learning experience designer"
        },
        {
            "id": 1267,
            "title": "Senior Content Marketing Strategist",
            "company": "payoneer",
            "platform": "greenhouse",
            "location": "Gurugram, India",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://www.payoneer.com/careers/position/8108385/?gh_jid=8108385",
            "postedAt": "2026-08-17T08:18:45.000Z",
            "scrapedAt": "2026-08-25T04:23:45.498Z",
            "searchTerm": "content strategist"
        },
        {
            "id": 1266,
            "title": "Senior Content Marketing Strategist",
            "company": "payoneer",
            "platform": "greenhouse",
            "location": "Bangalore, India",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://www.payoneer.com/careers/position/8121085/?gh_jid=8121085",
            "postedAt": "2026-08-17T08:18:45.000Z",
            "scrapedAt": "2026-08-25T04:23:45.460Z",
            "searchTerm": "content strategist"
        },
        {
            "id": 1265,
            "title": "Technical Writer",
            "company": "wizinc",
            "platform": "greenhouse",
            "location": "Tel Aviv",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://www.wiz.io/careers/job/4701311006/:title?gh_jid=4701311006",
            "postedAt": "2026-08-20T14:10:34.000Z",
            "scrapedAt": "2026-08-25T04:23:45.422Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1264,
            "title": "Instructional Designer",
            "company": "wizinc",
            "platform": "greenhouse",
            "location": "Tel Aviv",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://www.wiz.io/careers/job/4698920006/:title?gh_jid=4698920006",
            "postedAt": "2026-08-20T14:16:16.000Z",
            "scrapedAt": "2026-08-25T04:23:45.383Z",
            "searchTerm": "instructional designer"
        },
        {
            "id": 1263,
            "title": "Technical Writer",
            "company": "k2spacecorporation",
            "platform": "greenhouse",
            "location": "Los Angeles, CA",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://job-boards.greenhouse.io/k2spacecorporation/jobs/5291081008",
            "postedAt": "2026-07-03T17:44:07.000Z",
            "scrapedAt": "2026-08-25T04:23:45.344Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1387,
            "title": "Warfighter Systems - Senior Technical Writer",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5135008007?gh_jid=5135008007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:45.305Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1386,
            "title": "Technical Writer, Warfighter Systems",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5048073007?gh_jid=5048073007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:45.266Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1385,
            "title": "Technical Writer, Maritime",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5048075007?gh_jid=5048075007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:45.227Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1384,
            "title": "Technical Writer III",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Atlanta, Georgia, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5198629007?gh_jid=5198629007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:45.188Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1383,
            "title": "Technical Writer, Ghost",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5048076007?gh_jid=5048076007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:45.149Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1382,
            "title": "Technical Writer, Fury Data Module",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5173069007?gh_jid=5173069007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:44.880Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1381,
            "title": "Technical Writer, Defense Hardware & Systems",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5039865007?gh_jid=5039865007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:44.580Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1380,
            "title": "Technical Writer, Autonomous Airpower",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5091503007?gh_jid=5091503007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:44.380Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1379,
            "title": "Technical Writer, Autonomous Airpower",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Ashville, Ohio, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5212880007?gh_jid=5212880007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:44.280Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1378,
            "title": "Technical Writer, Advanced Effects Missiles",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5048074007?gh_jid=5048074007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:44.180Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1377,
            "title": "Technical Writer - Advanced Effects",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5215345007?gh_jid=5215345007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:44.080Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1376,
            "title": "Technical Writer",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5198659007?gh_jid=5198659007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:43.780Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1375,
            "title": "Technical Publications Operations Manager",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5197256007?gh_jid=5197256007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:43.680Z",
            "searchTerm": "technical publications manager"
        },
        {
            "id": 1374,
            "title": "Senior Technical Writer ",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5032570007?gh_jid=5032570007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:43.580Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1373,
            "title": "Senior Technical Publications Manager",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/4657745007?gh_jid=4657745007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:43.380Z",
            "searchTerm": "technical publications manager"
        },
        {
            "id": 1372,
            "title": "Senior Technical Publications Manager",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5197966007?gh_jid=5197966007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:43.280Z",
            "searchTerm": "technical publications manager"
        },
        {
            "id": 1371,
            "title": "Lead Technical Writer, Maritime & Undersea Systems",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5007838007?gh_jid=5007838007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:43.180Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1370,
            "title": "Lead Technical Writer, Maritime & Undersea Systems",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5195058007?gh_jid=5195058007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:42.880Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 1369,
            "title": "Instructional Designer, RapidLearning ",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5038377007?gh_jid=5038377007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:42.680Z",
            "searchTerm": "instructional designer"
        },
        {
            "id": 1368,
            "title": "Instructional Designer",
            "company": "andurilindustries",
            "platform": "greenhouse",
            "location": "Costa Mesa, California, United States",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://boards.greenhouse.io/andurilindustries/jobs/5173511007?gh_jid=5173511007",
            "postedAt": "2026-08-24T18:07:42.000Z",
            "scrapedAt": "2026-08-25T04:23:42.480Z",
            "searchTerm": "instructional designer"
        },
        {
            "id": 696,
            "title": "Senior Product Writer (UX)",
            "company": "gongio",
            "platform": "greenhouse",
            "location": "Dublin",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://job-boards.greenhouse.io/gongio/jobs/4681233006",
            "postedAt": "2026-07-06T17:12:14.000Z",
            "scrapedAt": "2026-08-25T04:23:42.281Z",
            "searchTerm": "ux writer"
        },
        {
            "id": 694,
            "title": "Senior Technical Writer",
            "company": "starburst",
            "platform": "greenhouse",
            "location": "Boston, MA",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://job-boards.greenhouse.io/starburst/jobs/5288993008",
            "postedAt": "2026-08-18T14:17:12.000Z",
            "scrapedAt": "2026-08-25T04:23:42.242Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 693,
            "title": "Technical Writer (1yr Contract)",
            "company": "sendbird",
            "platform": "greenhouse",
            "location": "Seoul, South Korea",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://sendbird.com/careers?gh_jid=8497886002",
            "postedAt": "2026-06-03T17:58:49.000Z",
            "scrapedAt": "2026-08-25T04:23:42.204Z",
            "searchTerm": "technical writer"
        },
        {
            "id": 692,
            "title": "Information Systems - Open Source Technical Architect",
            "company": "canonical",
            "platform": "greenhouse",
            "location": "Home based - EMEA",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://job-boards.greenhouse.io/canonical/jobs/4551832",
            "postedAt": "2026-08-05T22:23:33.000Z",
            "scrapedAt": "2026-08-25T04:23:42.165Z",
            "searchTerm": "information architect"
        },
        {
            "id": 691,
            "title": "Developer Advocate ",
            "company": "backblaze",
            "platform": "greenhouse",
            "location": "Remote - US",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://job-boards.greenhouse.io/backblaze/jobs/5196139008",
            "postedAt": "2026-08-19T17:57:41.000Z",
            "scrapedAt": "2026-08-25T04:23:42.125Z",
            "searchTerm": "developer advocate"
        },
        {
            "id": 1256,
            "title": "UX Writer",
            "company": "trivago",
            "platform": "greenhouse",
            "location": "Düsseldorf",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://careers.trivago.com/apply/8656533002.?gh_jid=8656533002",
            "postedAt": "2026-08-20T09:44:04.000Z",
            "scrapedAt": "2026-08-25T04:23:42.086Z",
            "searchTerm": "ux writer"
        },
        {
            "id": 1045,
            "title": "Training and Documentation Specialist",
            "company": "branch",
            "platform": "greenhouse",
            "location": "Remote, US",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://job-boards.greenhouse.io/branch/jobs/7860890003",
            "postedAt": "2026-08-22T18:18:23.000Z",
            "scrapedAt": "2026-08-25T04:23:42.028Z",
            "searchTerm": "documentation specialist"
        },
        {
            "id": 689,
            "title": "Instructional Designer, Revenue Enablement",
            "company": "solarwinds",
            "platform": "greenhouse",
            "location": "Bangalore, India",
            "isRemote": false,
            "salaryRaw": null,
            "url": "https://jobs.solarwinds.com/job-detail/?gh_jid=4714678005&gh_jid=4714678005",
            "postedAt": "2026-07-31T15:20:21.000Z",
            "scrapedAt": "2026-08-25T04:23:40.281Z",
            "searchTerm": "instructional designer"
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
            "id": 686,
            "title": "Developer Advocate (Database) ",
            "company": "jetbrains",
            "platform": "greenhouse",
            "location": "Amsterdam, Netherlands; Belgrade, Serbia; Limassol, Cyprus; London, United Kingdom; Madrid, Spain; Prague, Czech Republic; Remote, Germany; Warsaw, Poland; Yerevan, Armenia",
            "isRemote": true,
            "salaryRaw": null,
            "url": "https://job-boards.eu.greenhouse.io/jetbrains/jobs/4918398101",
            "postedAt": "2026-08-20T16:59:01.000Z",
            "scrapedAt": "2026-08-25T04:23:39.980Z",
            "searchTerm": "developer advocate"
        }
    ],
    "total": 151,
    "page": 1,
    "pageSize": 50
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
| `isRemote` | string | — | Filter to remote-only jobs (`true` or `false`) |
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
curl "https://job-scraper.replit.app/api/v1/jobs?searchTerm=technical%20writer&isRemote=true&pageSize=50" \
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
| `id` | number | Unique identifier for the job listing |
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
| `location` | string | Location of the job |
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

The full OpenAPI document — including all five paths, complete parameter lists, and every response schema — is available live at `GET /api/v1/openapi.json`.

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


