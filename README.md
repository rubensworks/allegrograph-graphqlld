# GraphQL-LD for AllegroGraph
[![Build Status](https://travis-ci.org/comunica/jQuery-Widget.js.svg?branch=master)](https://travis-ci.org/comunica/jQuery-Widget.js)

**[Try the _Web client_ live.](https://rubensworks.github.io/allegrograph-graphqlld/)**

This client-side Web application allows [GraphQL-LD](https://gist.github.com/rubensworks/9d6eccce996317677d71944ed1087ea6) queries to be executed against an AllegroGraph endpoint.

This application is powered by the [jQuery widget](https://github.com/comunica/jQuery-Widget.js) from [Comunica](https://github.com/comunica/comunica).

## What is GraphQL-LD?

*GraphQL-LD* is a way to query RDF using [GraphQL](https://graphql.org/).

Instead of querying *GraphQL interfaces*, *RDF interfaces* are queried, such as SPARQL endpoints, TPF interfaces, Linked Data documents, ...
This is done by *semantifying* GraphQL queries using a [JSON-LD context](https://json-ld.org/).

Internally, this approach involves converting a *GraphQL* query into a *SPARQL* query,
which can be executed by any *SPARQL engine*.

## Learn more about GraphQL-LD

* [Use GraphQL-LD in your JavaScript application](https://github.com/rubensworks/GraphQL-LD.js)
	* [Querying against a SPARQL endpoint](https://github.com/rubensworks/graphql-ld-sparqlendpoint.js)
	* [Querying against other types of RDF sources](https://github.com/rubensworks/graphql-ld-comunica.js)
* [Full list of GraphQL-LD query features](https://github.com/rubensworks/graphql-to-sparql.js)
	* [Shaping query results](https://github.com/rubensworks/graphql-to-sparql.js#converting-to-tree-based-results)
* [Read the academic paper on GraphQL-LD](https://comunica.github.io/Article-ISWC2018-Demo-GraphQlLD/)
* [GraphQL-RDF W3C community group](https://www.w3.org/community/graphql-rdf/)

## Use the code

This app requires [Node.JS 8.0](http://nodejs.org/) or higher and is tested on OSX and Linux.

```bash
$ git clone git@github.com:rubensworks/allegrograph-graphqlld.git
$ npm install
$ npm run production
```

These commands will generate a _static Web application_ inside the `build` folder.
All these files can be deployed on any Web server.

Currently, these files are automatically deployed to GitHub pages using Travis CI (see `.travis.yml`).
Upon each change in this Git repository, Travis will automatically rebuild and deploy the application.

## Change default queries

If you want to change the contents of the query and datasource dropdown fields,
you can edit datasources in `settings.json` and queries in the `queries` folder,
and run `queries-to-json` to compile both of them in a single JSON file.

Afterwards, you can re-execute `npm run production` to update the production version.

## How the browser client works
The _Comunica SPARQL_ engine is written for the Node.js environment. The [Webpack](https://webpack.js.org/) library makes it compatible with browsers.

The query engine itself runs in a background thread using [Web Workers](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Using_web_workers). The user interface (`ldf-client-ui.js`) instructs the worker (`ldf-client-worker.js`) to evaluate queries by sending messages, and the worker sends results back.

## Development

The `src/` folder contains all main source code in JavaScript.
Using Webpack, this JavaScript is bundled for the browser upon calling `npm run production`.

For starting a development version of the server that will automatically build upon changes, the command `npm run start` can be executed.

## License

The Linked Data Fragments jQuery Widget was originally written by [Ruben Verborgh](https://ruben.verborgh.org/)
and ported for Comunica SPARQL by [Ruben Taelman](http://rubensworks.net/).

This code is copyrighted by [Ghent University – imec](http://idlab.ugent.be/)
and released under the [MIT license](http://opensource.org/licenses/MIT).
