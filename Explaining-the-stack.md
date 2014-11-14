You are looking at a so-called [Slush](https://github.com/klei/slush) generator template. Slush is described as a scaffolding system. It provides a generic framework to perform scaffolding tasks using Gulp. We use Slush here to ramp up a new project folder with a single command. It will create a REST-type MarkLogic Roxy project for you, copy a node.js/AngularJS stack on top of it, and run some initialization commands for you, all in a single run.

It comes with a barebones application, with a few of the most commonly used features already in place. Otherwise it is kept as clean, and empty as possible, to allow users like you to quickly blend in whatever you are going to need for your project.

# The stack

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
