- \<app-name\>/
  - bower.json - front-end dependencies managed by [Bower](http://bower.io/)
  - gulp.config.js - [Gulp](http://gulpjs.com/) configuration
  - gulpfile.js - [Gulp](http://gulpjs.com/) task definitions
  - karma.conf.js - [Karma](http://karma-runner.github.io/0.13/index.html) test
    runner configuration
  - package.json - Node.js dependencies [managed with
    npm](https://docs.npmjs.com/files/package.json)
  - bower_components/
    - installed front-end dependencies managed by [Bower](http://bower.io/)
  - data/
    - dictionary-large.xml - word list for spelling suggestions
  - deploy/ - Files used by [Roxy](https://github.com/marklogic/roxy) to
    configure server when you run `./ml local bootstrap`
    - ml-config.xml - Project-specific MarkLogic configuration - This file is
      the ultimate record of how Roxy `bootstrap` will configure MarkLogic. Any
      settings in here will be set on the server. The `properties` files override
      various of these configurations.
    - build.properties - Project-specific Roxy settings (for sharing with
      teammates)
    - local.properties - Environment-specific Roxy settings (for your local
      machine; not checked into version control)
    - (other files used by Roxy...)
  - node-server/ - Files for the thin [Node.js](https://nodejs.org/)
    middle-layer, which performs proxying (largely to bypass
    [CORS](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing)). It is
    built as an [Express](http://expressjs.com/) listener. 
  - node-modules/ - Dependencies for node and gulp, installed by npm
  - rest-api/ - Files that [Roxy](https://github.com/marklogic/roxy) will put
    on the server when you run `./ml local deploy rest`
    - config/options/
    - MarkLogic [search
      options](https://docs.marklogic.com/guide/search-dev/query-options)
    - ext/
      - MarkLogic [REST API
        extensions](https://docs.marklogic.com/guide/rest-dev/extensions)
    - transforms/
      - Marklogic [REST
        transforms](https://docs.marklogic.com/guide/rest-dev/transforms)
  - sample-data/ - 25 sample JSON files representing people - See the
    [README](https://github.com/marklogic/slush-marklogic-node#sample-data) for
    information on how to load them
  - src/ - custom XQuery or server-side Javascript that Roxy will deploy into
    the app modules database when you run `./ml local deploy modules`
  - ui/
    - index.html - Entry point for browser to load and launch Angular
      application
    - specs.html - Used for running tests
    - app/ - [AngularJS](https://angularjs.org/) files
      - app.js - Initialization of Angular application
      - create/
        - sample create page and controller, allowing creation of a person
      - detail/
        - details page and controller - sample details page, which will display
          JSON data out-of-the-box, using the
          [ng-json-explorer](https://github.com/Goldark/ng-json-explorer) library
      - landing/
        - initial landing page, for developers. It should be removed when no
          longer needed
      - root/
        - a global template for your application
      - route/
        - routes.js configures your application's routes for the bundled
          [angular-ui-router](https://github.com/angular-ui/ui-router)
      - search/
        - search page, service, and controller, landing page
        - this depends heavily on the
          [ml-search-ng](https://github.com/joemfb/ml-search-ng) library, so
          look there for docs on how to update/extend it
      - user/
        - (user service, and controller, for handling login/logout)
    - fonts/
      - fonts from [fontawesome](https://fortawesome.github.io/Font-Awesome/)
        and [glyphicons](http://glyphicons.com/), used by
        [Bootstrap](http://getbootstrap.com/)
    - images/
      - logos
    - styles/
      - main.less - [Less](http://lesscss.org/) code, which will be compiled to
        css by gulp
