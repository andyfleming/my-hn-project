# My Hacker News ("MyHN") Project

## Overview

This is a full stack implementation of a "Hacker News" reader app. The project structure and a high-level specification are outlined below.

**To run this project as a whole, read the instructions in [my-hn-dev-env](https://github.com/andyfleming/my-hn-dev-env).**

## Services / Apps / Environments

**Dev Environment** is a local development environment for bootstrapping the whole stack locally.

**Tests** is a set of 2 test suites. The first an agnostic API test suite. The second uses headless chrome to consume the the front-end app and API as a an user would.

**API** is the primary API that will provide stories, comments, and bookmarks.

**App** is the UI to consume the API. It will allow for stories, comments, and bookmarks to be viewed. Bookmarks can also be created, updated, and deleted.

**Crawler Importer** is a script that can be ran to idempotently import the top 500 stories from the actual Hacker News API.

<!--**Search Sync** is a worker service that will import any new records or chnages to records from MySQL to ElasticSearch.-->

<!-- **Data Analysis** is a set of scripts to determine things like most popular topics of all time (within the scope of the imported data) or the popularity of a topic over time. -->


## Implementations

Below are links to my various implementations of the services and apps. Parts of the stack are written in multiple languages to demonstrate the flexibility of microservice/service-oriented architecture and competency in those languages. (I obviously would not suggest writing every part of the stack in a different language for a real use case.)

* **Dev Environment**
    * [Docker <small>– my-hn-dev-env</small>](https://github.com/andyfleming/my-hn-dev-env)
* **Tests**
    * [Node.js <small>— my-hn-tests-node-js</small>](https://github.com/andyfleming/my-hn-tests)
* **API**
    * [Node.js <small>— my-hn-api-node-js</small>](https://github.com/andyfleming/my-hn-api-node-js)
    <!-- * Python <small>— my-hn-api-python</small> -->
    <!--* [Scala <small>— my-hn-api-scala</small>]()-->
* **App**
    * [Vanilla JS <small>my-hn-app-vanilla-js</small>](https://github.com/andyfleming/)
    <!-- * React + Redux <small>— my-hn-app-react</small> -->
* **Crawler Importer**
    * [Node.js <small>— my-hn-crawler-importer-node-js</small>](https://github.com/andyfleming/my-hn-crawler-importer-node-js)
    <!--* [Golang <small>— my-hn-crawler-importer-go</small>]() -->
    <!--* **Search Sync**-->
    <!--* Node.js <small>— my-hn-search-sync-node-js</small>-->
<!--* **Data Analysis**
    * R <small>– my-hn-data-analysis-r
    * Python <small>– my-hn-data-analysis-python</small>
-->
## Supporting Data Stores

All service implementations above leverage the same underlying stack of data stores.

* **MySQL** acts the primary data store. It's structured and relational, allowing for an organized, easy-to-follow schema.
<!-- * **Elasticsearch** provides advanced full-text search beyond what MySQL can provide efficiently and effectively, including fuzzy-matching and weighting.-->
* **Redis** is used for fast and simple caching.
