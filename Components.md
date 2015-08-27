# Core tools

Once you created a new project, you will need to go through a few additional steps to get the code up and running. It relies on a few tools for that purpose:

- [Roxy](https://github.com/marklogic/roxy)
- [NPM](https://www.npmjs.org/)
- [Bower](http://bower.io/)
- [Gulp](http://gulpjs.com/)

## Roxy

Most of the [[Project folder structure]] is generated using Roxy. Roxy serves a few purposes. It is used by the Slush template to create and initialize a MarkLogic REST-type project, to which Node.js and Angular tiers are added on top. Roxy can be used to scaffold custom [[REST extensions]], and it will also be used to bootstrap your project into MarkLogic, and deploy modules and REST extensions into the MarkLogic REST-api instance that will be serving as back-end.

It typically requires taking these steps:

- `./ml local bootstrap` (creates all users, roles, privs, amps, forests, databases, and app servers defined in deploy/ml-config.xml)
- `./ml local deploy content` (uploads anything in data/, often dictionaries and other relatively static content)
- `./ml local deploy modules` (uploads anything in src/, and deploy all REST extensions through the REST-api)

## NPM

The Node Package Management is used for installing command-line utilities necessary for building (bower, gulp, gulp-less, ..) and testing (karma, ..) the project. It is also used for installing node.js libraries that are used for running the project, like express, cookie-parser, etc.

Settings are stored in package.json, and you need to run the following command each time it is changed:

- `npm install`

You can opt to install particular tools globally, otherwise local copies are stored in node_modules/ within the project folder. Typical utilities that are installed globally are bower and gulp:

- `npm install -g bower`
- `npm install -g gulp`

## Bower

Bower is used for managing JavaScript dependencies using in the UI. The dependencies are stored in bower.json, and you need to run the following command each time it is changed:

- `bower install`

Dependencies are stored in bower_components/. The HTML index (app/ui/index.html) refers as much as possible to third-party CSS and JS files in there.

## Gulp

Where Roxy acts as the build system for the MarkLogic part, Gulp is the build
system for the UI part. It can take care of all sorts of tasks, like
concatenating and minifying JavaScript, converting [Less](http://lesscss.org/)
to CSS, and launching/running node.js scripts. It can also watch for file
changes, and repeat certain tasks automatically if needed. The default task is
to run less and minify tasks once, and then watch for changes to repeat those
tasks. It will therefore (normally) not terminate:

- `gulp`

The other major task is to launch the Express listener that forms the [[Middle-layer|Explaining the stack]]:

- `gulp server`

# Front-end Components

## ML Search

[ml-search-ng](https://github.com/joemfb/ml-search-ng)

## Angular UI Router

We use the [angular-ui-router](https://github.com/angular-ui/ui-router). The
original Angular-router used to be a core feature of Angular but it was moved
into a separate module, as were a number of other features, as part of a major
refactoring. It offered basic routing functionality to support deep-linking and
treats routes as separate pages. It was useful for separating views,
controllers, and resolves by URL as one normally would in application
development. For anything more robust, or to change states without changing
urls, ui-router is the most popular replacement. UI-router expands upon the
angular-router features by allowing nested states, named views, and abstract
states. It’s more complicated but more complete.

## Angular UI Bootstrap

[angular-ui-bootstrap](https://github.com/angular-ui/bootstrap) is a wrapper
around the popular [Bootstrap](http://getbootstrap.com/) JS components (and a
few others) that work along side of Angular’s data binding. It provides basic
directives for things like tabs, radio buttons, modals, date pickers, etc.

## FontAwesome

[FontAwesome](https://fortawesome.github.io/Font-Awesome/) is a CSS library
that provides a large list of quality icons without separate images.  It’s
essentially a custom font that contains icon characters so they can be rendered
just like any other character with their special css classes.

## Angular UI TinyMCE

[angular-ui-tinymce](https://github.com/angular-ui/ui-tinymce) is used to
support the TinyMCE (rich text editor) in a manner that works along side of
Angular’s data binding.

## Angular HighlightJS

## Angular Cookies

## Angular JSON Explorer

## ML-Utils

# Development Tools

## Lodash

## JSHint

## BrowserSync

# Testing

## Karma

Karma was written by the same folks who write Angular , so it was designed with Angular in mind.  It’s really just a wrapper around already popular testing tools like Jasmine, Mocha, PhantomJS, etc.  The fact that it was designed for angular and that there are many community examples of how to use it make it a pretty easy choice for unit testing Angular apps.

## Angular Mocks
