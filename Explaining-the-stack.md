The stack we are using consists of three layers:

- Front-end: [AngularJS](https://angularjs.org/)
- Middle-layer: [node.js](http://nodejs.org/)
- Back-end: [MarkLogic](http://marklogic.com)

The Middle-layer is very thin though. So even though this can be technically seen as a three-tier solution, the Middle-layer is mostly serving as a Proxy between Front-end and Back-end. There is currently no business logic in the Middle-layer. That was a deliberate choice to keep the architecture simple. So effectively it might be better to describe this as a **two-tier solution** in the way it currently works.

On the other hand, nothing stops you from moving business logic into the
Node-layer, effectively separating application logic from business logic, and
maturing the Middle-layer into a proper Middle-tier.

# Back-end

The Back-end is formed by a [MarkLogic REST
API](http://docs.marklogic.com/guide/rest-dev) HTTP server instance. The
template tries to utilize the existing REST API as much as possible for all its
needs. It adds just a few custom [[REST extensions]], partly to provide
interesting features like spell-suggestions.

You will typically add and adjust [search
options](https://docs.marklogic.com/guide/search-dev/query-options), and
depending on need add a few custom [[REST extensions]] of your own. They can
optionally rely on custom XQuery or Server-side Javascript libraries that will
be uploaded for you by Roxy.

You might also be adding configuration and code to leverage [MarkLogic's
features](http://docs.marklogic.com/guide/app-dev), like
[Alerting](https://docs.marklogic.com/guide/search-dev/alerts) and
[DLS](https://help.marklogic.com/knowledgebase/article/View/150/0/searching-across-latest-version-of-managed-documents).
Or setting up an [ingest framework](http://docs.marklogic.com/guide/ingestion)
that transforms and processes incoming data using
[triggers](https://docs.marklogic.com/guide/app-dev/triggers),
[CPF](https://docs.marklogic.com/guide/cpf), or
[MLCP](https://docs.marklogic.com/guide/ingestion/content-pump) transforms.

# Middle-layer

The Middle-layer is formed by an [Express](http://expressjs.com/) listener running in Node.js. In this case it is very thin. It merely hosts the static files including the AngularJS-related JavaScript and HTML templates, third-party JavaScript, styling, and images. Next to this it mostly serves as a proxy for REST calls to the MarkLogic back-end, handling authentication for it along the way, and potentially shielding subsets of the MarkLogic REST API, if you would prefer not to expose all of it.

You typically won't change this layer, unless you want to provide free access and disable login/logout for instance.

# Front-end

The Front-end is built in dynamic HTML using JavaScript and CSS. AngularJS is used as general framework to coordinate all dynamic behavior. It includes routing and navigation through the application, as well as a MVC-like separation between data, visualization, and application logic. It also provides convenient handles for building dynamic web pages, leveraging libraries like [Angular-UI](http://angular-ui.github.io/), [Highcharts](http://www.highcharts.com/), [Google Maps](https://developers.google.com/maps/documentation/javascript/3.exp/reference) for fancy features. For presentation it uses components like [Bootstrap](http://getbootstrap.com/), and [Font-Awesome](http://fortawesome.github.io/Font-Awesome/).

You will be changing this part most heavily. It fully controls look and feel of the resulting web application.

See [[Project folder structure]] and [[Components]] for more details how everything is arranged on the filesystem, and where to make changes to bend the application to where you want it to go.
