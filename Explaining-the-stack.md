The stack we are using, can be described as a three-tier solution:

- Front-end: [AngularJS](https://angularjs.org/)
- Middle-tier: [node.js](http://nodejs.org/)
- Back-end: [MarkLogic](http://marklogic.com)

The Middle-tier layer is in this case very thin. It merely hosts the static files including the AngularJS related JavaScript and HTML templates, third-party JavaScript, styling, and images. Next to this it mostly serves as a proxy for REST calls to the MarkLogic back-end, handling authentication for it along the way, and potentially shielding subsets of the MarkLogic REST-api, if you would prefer not to expose all of it.

# The components

This particular template includes the following main components:

- [AngularJS](https://angularjs.org/)
- [Gulp](http://gulpjs.com/)
- [node.js](http://nodejs.org/)
- [Roxy Deployer](https://github.com/marklogic/roxy)

Roxy: bootstrap MarkLogic databases, application servers, etc; scaffolding for MarkLogic REST API service extensions
