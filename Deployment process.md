Once you created a new project, you will need to go through a few additional steps to get the code up and running. It relies on a few tools for that purpose:

- [Roxy](https://github.com/marklogic/roxy)
- [NPM](https://www.npmjs.org/)
- [Bower](http://bower.io/)
- [Gulp](http://gulpjs.com/)

# Roxy

Most of the [[Project folder structure]] is generated using Roxy. Roxy serves a few purposes. It is used by the Slush template to create and initialize a MarkLogic REST-type project, to which Node.js and Angular tiers are added on top. Roxy can be used to scaffold custom [[REST extensions]], and it will also be used to bootstrap your project into MarkLogic, and deploy modules and REST extensions into the MarkLogic REST-api instance that will be serving as back-end.

It typically requires taking these steps:

- `./ml local bootstrap` (creates all users, roles, privs, amps, forests, databases, and app servers defined in deploy/ml-config.xml)
- `./ml local deploy content` (uploads anything in data/, often dictionaries and other relatively static content)
- `./ml local deploy modules` (uploads anything in src/, and deploy all REST extensions through the REST-api)

# NPM

The Node Package Management is used for installing command-line utilities necessary for building (bower, gulp, gulp-less, ..) and testing (karma, ..) the project. It is also used for installing node.js libraries that are used for running the project, like express, cookie-parser, etc.

Settings are stored in package.json, and you need to run the following command each time it is changed:

- `npm install`

You can opt to install particular tools globally, otherwise local copies are stored in node_modules/ within the project folder. Typical utilities that are installed globally are bower and gulp:

- `npm install -g bower`
- `npm install -g gulp`

# Bower

Bower is used for managing JavaScript dependencies using in the UI. The dependencies are stored in bower.json, and you need to run the following command each time it is changed:

- `bower install`

Dependencies are stored in app/ui/bower_components/. The HTML index (app/ui/index.html) refers as much as possible to third-party CSS and JS files in there.

# Gulp

Where Roxy is kind of the build system for the MarkLogic part, is Gulp the build system for the UI part. It can take care of all sorts of tasks, like concat and minify JavaScript, convert Less to CSS, and launching/running node.js scripts. It can also watch for file changes, and repeat certain tasks automatically if needed. The default task is to run less and minify tasks once, and then watch for changes to repeat those tasks. It will therefor (normally) not terminate:

- `gulp`

The other major task is to launch the Express listener that forms the [[Middle-layer|Explaining the stack]]:

- `gulp server`
