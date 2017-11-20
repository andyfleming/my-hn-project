![MyHN](https://user-images.githubusercontent.com/721038/33003466-c3c655b8-cd6f-11e7-9258-afa9f73f089d.png)

# My Hacker News Project

This is a full stack implementation of a "Hacker News" reader app. The project structure and a high-level specification are outlined below.

:bulb: **To run this project as a whole, read the instructions in [my-hn-dev-env](https://github.com/andyfleming/my-hn-dev-env).**

Parts of the stack are written in multiple languages to demonstrate the flexibility of microservice/service-oriented architecture and competency in those languages. (I obviously would not suggest writing every part of the stack in a different language for a real use case.) The agnostic test suites can test any combination of the stack.

![stack-animation](https://user-images.githubusercontent.com/721038/32997252-f5b1bab4-cd41-11e7-9b2f-f05eb94c100a.gif)

##  Services / Apps / Environments

<table>
   <thead>
      <tr>
         <th align="left">Description</th>
         <th align="left" width="280">Implementations</th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td>
            <b>Dev Environment</b>
            <br>A local development environment for bootstrapping the whole stack locally.
         </td>
         <td><a href="https://github.com/andyfleming/my-hn-dev-env"><b>Docker</b><br><small>my-hn-dev-env</small></a></td>
      </tr>
      <tr>
         <td>
            <b>Tests</b>
            <br>A a set of 2 test suites. The first an agnostic API test suite. The second uses headless chrome to consume the the front-end app and API as a an user would.
         </td>
         <td><a href="https://github.com/andyfleming/my-hn-tests"><b>Node.js + Ava, Puppeteer</b><br><small>my-hn-tests</small></a></td>
      </tr>
      <tr>
         <td rowspan="2">
            <b>App</b>
            <br>The UI to consume the API. It will allow for stories, comments, and bookmarks to be viewed. Bookmarks can also be created, updated, and deleted.
         </td>
         <td><!--<a href="https://github.com/andyfleming/my-hn-app-react">--><b>React + Redux</b><br><small>my-hn-app-react</small><!--</a>--></td>
      </tr>
      <tr>
         <td><a href="https://github.com/andyfleming/my-hn-app-vanilla-js"><b>Vanilla JS</b><br><small>my-hn-app-vanilla-js</small></a></td>
      </tr>
      <tr>
         <td rowspan="3">
            <b>API</b>
            <br>The primary API that will provide stories, comments, and bookmarks. It also leverages Redis to cache expensive responses.
         </td>
         <td><a href="https://github.com/andyfleming/my-hn-api-node-js"><b>Node.js + Express</b><br><small>my-hn-api-node-js</small></a></td>
      </tr>
      <tr>
         <td><!--<a href="https://github.com/andyfleming/my-hn-api-python">--><b>Python + Flask<br><small>my-hn-api-python</small><!--</a>--></td>
      </tr>
      <tr>
         <td><!--<a href="https://github.com/andyfleming/my-hn-api-scala">--><b>Scala + Finatra</b><br><small>my-hn-api-scala</small><!--</a>--></td>
      </tr>
        <tr>
         <td>
            <b>Crawler Importer</b>
            <br>A script that can be ran to idempotently import the top stories from the actual Hacker News API.
         </td>
         <td><a href="https://github.com/andyfleming/my-hn-crawler-importer-node-js"><b>Node.js</b><br><small>my-hn-crawler-importer-node-js</small></a></td>
      </tr>

   </tbody>
</table>

## Supporting Data Stores

All service implementations above leverage the same underlying stack of data stores.

* **MySQL** acts the primary data store. It's structured and relational, allowing for an organized, easy-to-follow schema.
* **Redis** is used for fast and simple caching.
