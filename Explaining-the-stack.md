The stack we are using, can be described as a three-tier solution:

- Front-end: [AngularJS](https://angularjs.org/)
- Middle-tier: [node.js](http://nodejs.org/)
- Back-end: [MarkLogic](http://marklogic.com)

# Back-end

The Back-end is formed by a [MarkLogic REST-api](http://docs.marklogic.com/guide/rest-dev) HTTP server instance. The template tries to utilize the existing REST-api as much as possible for all its needs. It adds just a few custom [[REST extensions]], partly to provide interesting features like spell-suggestions, partly to support marshall JSON to XML and v.v. as native JSON storage is not yet supported in MarkLogic. That will come in [MarkLogic 8](http://www.marklogic.com/press-releases/marklogic-sets-standard-for-modern-database/).

You will typically add and adjust search options, and depending on need add a few custom REST extensions of your own. They can optionally rely on custom XQuery libraries that will be uploaded for you in the [[Deployment process]].

You might also be adding configuration and code to leverage [MarkLogic's features](http://docs.marklogic.com/guide/app-dev), like Alerting, and DLS. Or setting up an [ingest framework](http://docs.marklogic.com/guide/ingestion) that transforms and processes incoming data using for instance Triggers, CPF, or MLCP transforms. Depending on the needs to manipulate data at ingest or afterwards this could be an area where you will be putting in part of you effort.

# Middle-tier
The Middle-tier layer is formed by an [Express](http://expressjs.com/) listener running in Node.js. In this case it is very thin. It merely hosts the static files including the AngularJS related JavaScript and HTML templates, third-party JavaScript, styling, and images. Next to this it mostly serves as a proxy for REST calls to the MarkLogic back-end, handling authentication for it along the way, and potentially shielding subsets of the MarkLogic REST-api, if you would prefer not to expose all of it.

You typically won't change this layer, unless you want to provide free access, and disable login/logout for instance.
# Front-end

The Front-end is built in dynamic HTML using JavaScript and CSS. AngularJS is used as general framework to coordinate all dynamic behavior. It includes routing and navigation through the application, as well as a MVC-like separation between data, visualization, and application logic. It also provides convenient handles for building dynamic web pages, leveraging libraries like [Angular-UI](http://angular-ui.github.io/), [Highcharts](http://www.highcharts.com/), [Google Maps](https://developers.google.com/maps/documentation/javascript/3.exp/reference) for fancy features. For presentation it uses components like [Bootstrap](http://getbootstrap.com/), and [Font-Awesome](http://fortawesome.github.io/Font-Awesome/).

You will be changing this part most heavily. It fully controls look and feel of the resulting web application.

See [[Project folder structure]] for more details how everything is arranged on the filesystem, and where to make changes to bend the application to where you want it to go.
