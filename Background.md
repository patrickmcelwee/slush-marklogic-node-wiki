You might ask, why a stack that is using AngularJS, Gulp, Node.js, etc.? The
main answer is pretty straight-forward: it matches the current direction of
MarkLogic. As of MarkLogic 8, it supports native, server-side JavaScript,
natively stores JSON, and provides a Node.js client which interacts with the
vastly extended MarkLogic REST API. 

Next to that, the MarkLogic Engineering team that builds all core
functionality, are building a [Sample
Stack](https://github.com/marklogic/marklogic-samplestack) using the same
components. The most important difference between SampleStack and this template
is that this doesn't provide a static fully-fledged (demo) application, but
rather provides a base template, a toolset, and a set of readily available
components.

More generally, JavaScript has become popular in all kinds of areas. It was
originally used most to make websites dynamic in browsers on desktops, but
mobile development has increased its popularity. The past years, it also became
a popular server-side language, increased by the hype around the JSON format.
Server-side JavaScript resulted in Node.js, which is immensely popular at the
moment. Gulp, which runs on Node.js, seems to be the most popular tool for
development tasks. Slush relies on Gulp.

And finally: AngularJS. JQuery has been pretty popular over the past decade or
so. It is a powerful tool. But it doesn't blend in very naturally with HTML,
and it doesn't provide an MVC-like separation of concerns. AngularJS first of
all kind of brings JavaScript and HTML back together, but without the need to
mess around with inline scripting. Instead it allows blending in dynamic
behavior and functional components by adding mere attributes and elements. It
encourages developers to break down code into reusable components, and it
provides good means to write a web application with an MVC model in mind.

This is probably oversimplifying things, but it hopefully gives some background behind the choices that have been made.
