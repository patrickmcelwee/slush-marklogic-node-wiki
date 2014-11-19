# Back-end

This Slush template is dedicated to building end-user application on top of MarkLogic. The MarkLogic REST-api is the most flexible way to integrate into any stack, and it blends in particularly well with a JavaScript stack.

# Middle-tier

Kept deliberately thin. Node.js is used a lot for JavaScript development, so convenient to use that as middle-tier.

# Front-end

Angular-router used to be a core feature of Angular but it was moved into a separate module, as were a number of other features, as part of a major refactoring.  It offers basic routing functionality to support deep-linking and treats routes as separate pages.  It’s useful for separating views, controllers, and resolves by URL as one normally would in application development.  For anything more robust, or to change states without changing urls, ui-router is the most popular replacement.  UI-router expands upon the angular-router features by allowing nested states, named views, and abstract states.  It’s more complicated but more complete.

Note: we will likely switch to UI-router in near future..

Ng-ckeditor is used to support the CKEditor (rich text editor) in a manner that works along side of Angular’s data binding.

Font-awesome is a CSS library that provides a large list of quality icons without separate images.  It’s essentially a custom font that contains icon characters so they can be rendered just like any other character with their special css classes.

UI-bootstrap is a wrapper around the bootstrap JS components (and a few others) that work along side of Angular’s data binding.  It provides basic directives for things like tabs, radio buttons, modals, date pickers, etc.

Karma was written by the same folks who write Angular , so it was designed with Angular in mind.  It’s really just a wrapper around already popular testing tools like Jasmine, Mocha, PhantomJS, etc.  The fact that it was designed for angular and that there are many community examples of how to use it make it a pretty easy choice for unit testing Angular apps.
