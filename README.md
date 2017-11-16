# My Hacker News ("MyHN") Project

## Overview

This is a full stack implementation of a "Hacker News" reader app. The project structure and a high-level specification are outlined below.

**To run this project as a whole, read the instructions in [my-hn-dev-env]().**

## Services / Apps / Environments

**Dev Environment** is a local development environment for bootstrapping the whole stack locally.

**Tests** is a set of 2 test suites. The first an agnostic API test suite. The second uses headless chrome to consume the the front-end app and API as a an user would.

**API** is the primary API that will provide stories, comments, and bookmarks.

**App** is the UI to consume the API. It will allow for stories, comments, and bookmarks to be viewed. Bookmarks can also be created, updated, and deleted.

**Crawler Importer** is a script that can be ran to idempotently import the top 500 stories from the actual Hacker News API.

**Search Sync** is a worker service that will import any new records or chnages to records from MySQL to ElasticSearch.

**Data Analysis** is a set of scripts to determine things like most popular topics of all time (within the scope of the imported data) or the popularity of a topic over time.


## Implementations

Below are links to my various implementations of the services and apps. Parts of the stack are written in multiple languages to demonstrate the flexibility of microservice/service-oriented architecture and competency in those languages. (I obviously would not suggest writing every part of the stack in a different language for a real use case.)

* **Dev Environment**
    * [Docker <small>– my-hn-dev-env</small>]()
* **Tests**
    * [Node.js <small>— my-hn-tests-node-js</small>]()
* **API**
    * [Node.js <small>— my-hn-api-node-js</small>]()
    * [Python <small>— my-hn-api-python</small>]()
    <!--* [Scala <small>— my-hn-api-scala</small>]()-->
* **App**
    * [React + Redux <small>— my-hn-app-react</small>]()
* **Crawler Importer**
    * [Node.js <small>— my-hn-crawler-importer-node-js</small>]()
 <!--   * [Golang <small>— my-hn-crawler-importer-go</small>]() -->
* **Search Sync**
    * [Node.js <small>— my-hn-search-sync-node-js</small>]()
* **Data Analysis**
    * [R <small>– my-hn-data-analysis-r]()
    * [Python <small>– my-hn-data-analysis-python</small>]()

## Supporting Data Stores

All service implementations above leverage the same underlying stack of data stores.

* **MySQL** acts the primary data store. It's structured and relational, allowing for an organized, easy-to-follow schema.
* **Elasticsearch** provides advanced full-text search beyond what MySQL can provide efficiently and effectively, including fuzzy-matching and weighting.
* **Redis** is used for fast and simple caching.

## MyHN v0.1 Spec

* **Test Stack**
    * [ ] API Test Suite
    * [ ] App Test Suite
* **API**
    * [ ] Basic API Requirements
    * [ ] A `.env` file should be used for bootstrapping environment variables.
        * [ ] `COMMENTS_RESPONSE_CACHE_TTL`
    * [ ] Endpoints
        * [ ] `GET: /stories`
        * [ ] `POST: /stories/search`
        * [ ] `GET: /stories/{id}/comments`
            * [ ] Recursively builds a tree of comments for the given story
            * [ ] Redis should cache the built tree of comments for the specified TTL
        * [ ] `GET: /bookmarks`
        * [ ] `POST: /bookmarks`
            * [ ] Creates a bookmark
            * [ ] Validates input
                * [ ] Require `story_id`; validate existence
                * [ ] Allow `all_time_favorite`, validate boolean.
                * [ ] Reject anything other than `story_id`, `all_time_favorite`, or `notes`.
        * [ ] `PATCH: /bookmarks/{id}`
        * [ ] `DELETE: /bookmarks/{id}`
* **App**
    * [ ] A simple response app with two views/tabs, "Top Stories" and "Bookmarked Stories".
    * [ ] Stories View
        * [ ] A search box will be available
* **Crawler Importer**
    * [ ] If the database doesn't exist, the database and tables should be created.
    * [ ] A `.env` file should be used for bootstrapping environment variables.
        * [ ] `ACTUAL_HN_API_BASE_URL`
        * [ ] `CONCURRENT_REQUESTS_LIMIT` (default `8`)
        * [ ] `REQUEST_LIMIT_PER_PERIOD` (default `10`)
        * [ ] `REQUEST_LIMIT_PERIOD_SECONDS` (default `60`)
    * [ ] 
* **Search Sync**
    * [ ] A `.env` file should be used for bootstrapping environment variables.
        * [ ] `SYNC_INTERVAL_SECONDS` used to set the time between sync tasks.
* **Data Analysis**
    * [ ] Import story titles and scores from postgres
    * [ ] Rank most popular topics of all time
    * [ ] Show a topic's popularity over time
