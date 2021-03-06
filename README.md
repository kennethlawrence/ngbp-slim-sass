# ngbp-slim-sass

A *slightly less* opinionated kickstarter for [AngularJS](http://angularjs.org) projects.
Based around AngularJS, SASS, Bower, and Grunt.
Forked from the original [ngBoilerplate](http://https://github.com/ngbp/ngbp).

***
## Purpose

ngbp-slim-sass was created to act as a robust starting point for building scalable, well
tested, easy to develop AngularJS applications. It inherits much of its mojo from the
original [ngBoilerplate](http://https://github.com/ngbp/ngbp), but removes some of the
components to allow a little more developer freedom in deciding which frameworks and
libraries get built into your application.

### Major differences from ngBoilerplate

* Development server with AngularJS HTML5Mode Redirects Added.
* SASS css preprocessor added (via libsass)
* LESS css preprocessor removed
* Twitter Bootstrap removed
* AngularUI-Bootstrap removed

## Quick Start

Install Node.js and then:

```sh
$ git clone git://github.com/kennethlawrence/ngbp-slim-sass
$ cd ngbp-slim-sass
$ sudo npm -g install grunt-cli karma bower
$ npm install
$ bower install
$ grunt watch
```

Finally, open `http://localhost:8000` in your browser.
You're good to go. 

## Purpose

`ngbp-slim-sass` is a slim kickstart that is not intended to contain an extensive array of
options, frameworks, or packages, but rather provide a basic AngularJS
starting point. It is built around the solid directory structure, and beautifully executed
build system contained within the [ngBoilerplate](https://github.com/ngbp/ngbp) project, and
makes use of the [SASS](http://sass-lang.com) CSS preprocessor language.

## Popular Options

Adding additional components to your application is easy, here are examples of
two very popular framework options.

### Twitter Bootstrap
To bring Bootstrap into you're project you could use bower to install the dependencies:
```sh
$ bower install bootstrap-sass-official --save-dev
$ bower install angular-bootstrap --save-dev
```
Then simply import the vendor sass files at the top of your **main.scss**:
``
 @import '../../vendor/bootstrap-sass-official/assets/stylesheets/bootstrap';
``
and add the angular-bootstrap javascript file to your **build.config.js** - vendor_files.js section.
``
  vendor_files: {
    js: [
      ...,
      'vendor/angular-bootstrap/ui-bootstrap-tpls.min.js',
      ...
``

## Zurb Foundation
Adding the Foundation Framework is a similar process.
Foundation can be installed in your project with:
```sh
$ bower install zurb/bower-foundation --save-dev"
$ bower install angular-foundation --save-dev
```
Then simply import the vendor sass files at the top of your **src/sass/main.scss**:
``
 @import '../../vendor/foundation/scss/foundation';
``
and add the angular-foundation javascript file to your **build.config.js** - vendor_files.js section.
``
  vendor_files: {
    js: [
      ...,
      'vendor/angular-bootstrap/mm-foundation-tpls.min.js',
      ...
``

These are only two of many possible components you can bring into your project. `ngbp-slim-sass`
tries to make very few decisions for you, and still give you a quick and effective start to
your AngularJS projects.

## Philosophy

The principal goal of `ngp-slim-sass` is the same as that of 
[ngBoilerplate](https://github.com/ngbp/ngbp), to set projects up for long-term
success.  So `ngbp-slim-sass` tries to follow these best practices everywhere it can:

- Properly orchestrated modules to encourage drag-and-drop component re-use.
- Tests exist alongside the component they are testing with no separate `test`
  directory required; the build process should be sophisticated enough to handle
  this.
- Speaking of which, the build system should work automagically, without
  involvement from the developer. It should do what needs to be done, while
  staying out of the way. Components should end up tested, linted, compiled,
  and minified, ready for use in a production environment.
- Integration with popular tools like Bower, Karma, and SASS.
- *Encourages* test-driven development. It's the only way to code.
- A directory structure that is cogent, meaningful to new team members, and
  supporting of the above points.
- Well-documented, to show new developers *why* things are set up the way they
  are.
- It should be responsive to evidence. Community feedback is therefore crucial
  to the success of `ngbp-slim-sass`.

## Learn

### Overall Directory Structure

At a high level, the structure looks roughly like this:

```
ngbp-slim-sass/
  |- grunt-tasks/
  |- karma/
  |- src/
  |  |- app/
  |  |  |- <app logic>
  |  |- assets/
  |  |  |- <static files>
  |  |- common/
  |  |  |- <reusable code>
  |  |- sass/
  |  |  |- main.scss
  |- vendor/
  |  |- angular-ui-router/
  |  |- placeholders/
  |- .bowerrc
  |- bower.json
  |- build.config.js
  |- Gruntfile.js
  |- module.prefix
  |- module.suffix
  |- package.json
```

What follows is a brief description of each entry, but most directories contain
their own `README.md` file with additional documentation, so browse around to
learn more.

- `karma/` - test configuration.
- `src/` - our application sources. [Read more &raquo;](src/README.md)
- `vendor/` - third-party libraries. [Bower](http://bower.io) will install
  packages here. Anything added to this directory will need to be manually added
  to `build.config.js` and `karma/karma-unit.js` to be picked up by the build
  system.
- `.bowerrc` - the Bower configuration file. This tells Bower to install
  components into the `vendor/` directory.
- `bower.json` - this is our project configuration for Bower and it contains the
  list of Bower dependencies we need.
- `build.config.js` - our customizable build settings; see "The Build System"
  below.
- `Gruntfile.js` - our build script; see "The Build System" below.
- `module.prefix` and `module.suffix` - our compiled application script is
  wrapped in these, which by default are used to place the application inside a
  self-executing anonymous function to ensure no clashes with other libraries.
- `package.json` - metadata about the app, used by NPM and our build script. Our
  NPM dependencies are listed here.

### Detailed Installation

This section provides a little more detailed understanding of what goes into
getting `ngb-slim-sass` up and running. Though `ngbp-slim-sass` is really simple
to use, it might help to have an understanding of the tools involved here, like
Node.js and Grunt and Bower. If you're completely new to highly organized,
modern JavaScript development, take a few short minutes to read [this overview
of the tools](tools.md) before continuing with this section.

Okay, ready to go? Here it is:

`ngbp-slim-sass` uses [Grunt](http://gruntjs.org) as its build system, so
[Node.js](http://nodejs.org) is required. Also, Grunt by default no longer comes
with a command-line utility and Karma and Bower must end up in your global path
for the build system to find it, so they must be installed independently. Once
you have Node.js installed, you can simply use `npm` to make it all happen:

```sh
$ npm -g install grunt-cli karma bower
```

If you're on Linux (like I am) then throw `sudo` in front of that command.  If
you're on Windows, then you're on your own.

Next, you can either clone this repository using Git, download it as a zip file
from GitHub, or merge the branch into your existing repository. Assuming you're
starting from scratch, simply clone this repository using git:

```sh
$ git clone git://github.com/kennethlawrence/ngbp-slim-sass my-project-name
$ cd my-project-name
```

And then install the remaining build dependencies locally:

```sh
$ npm install
```

This will read the `dependencies` (empty by default) and the `devDependencies`
(which contains our build requirements) from `package.json` and install
everything needed into a folder called `node_modules/`.

There are a few Bower packages used by `ngbp-slim-sass`, such as
Angular UI router, which are listed in `bower.js`. To install them into the
`vendor/` directory, simply run:

```sh
$ bower install
```

In the future, should you want to add a new Bower package to your app, run the
`install` command:

```sh
$ bower install packagename --save-dev
```

The `--save-dev` flag tells Bower to add the package at its current version to
our project's `bower.js` file so should another developer download our
application (or we download it from a different computer), we can simply run the
`bower install` command as above and all our dependencies will be installed for
us. Neat!

Technically, `ngbp-slim-sass` is now ready to go.

However, prior to hacking on your application, you will want to modify the
`package.json` file to contain your project's information. Do not remove any
items from the `devDependencies` array as all are needed for the build process
to work.

To ensure your setup works, launch grunt:

```sh
$ grunt watch
```

The built files are placed in the `build/` directory by default. Open
`http://localhost:8000` in your browser and check it out! Because everything is
compiled, no XHR requests are needed to retrieve templates, so until this needs
to communicate with your backend there is no need to run it from a web server.

`watch` is actually an alias of the `grunt-contrib-watch` that will first run a
partial build before watching for file changes. With this setup, any file that
changes will trigger only those build tasks necessary to bring the app up to
date. For example, when a template file changes, the templates are recompiled
and concatenated, but when a test/spec file changes, only the tests are run.
This allows the watch command to complete in a fraction of the time it would
ordinarily take.

In addition, if you're running a Live Reload plugin in your browser (see below),
you won't even have to refresh to see the changes! When the `watch` task detects
a file change, it will reload the page for you. Sweet.

When you're ready to push your app into production, just run the `compile`
command:

```sh
$ grunt compile
```

This will concatenate and minify your sources and place them by default into the
`bin/` directory. There will only be three files: `index.html`,
`your-app-name.js`, and `your-app-name.css`. All of the vendor dependencies like
possible framework styles and AngularJS itself have been added to them for super-easy
deploying. If you use any assets (`src/assets/`) then they will be copied to
`bin/` as is.

Lastly, a complete build is always available by simply running the default
task, which runs `build` and then `compile`:

```sh
$ grunt
```

### The Build System

The best way to learn about the build system is by familiarizing yourself with
Grunt and then reading through the heavily documented build script,
`Gruntfile.js`. But you don't need to do that to be very productive with
`ngbp-slim-sass`. What follows in this section is a quick introduction to the
tasks provided and should be plenty to get you started.

The driver of the process is the `delta` multi-task, which watches for file
changes using `grunt-contrib-watch` and executes one of nine tasks when a file
changes:

* `delta:gruntfile` - When `Gruntfile.js` changes, this task runs the linter
  (`jshint`) on that one file and reloads the configuration.
* `delta:assets` - When any file within `src/assets/` changes, all asset files
  are copied to `build/assets/`.
* `delta:html` - When `src/index.html` changes, it is compiled as a Grunt
  template, so script names, etc., are dynamically replaced with the correct
  values configured dynamically by Grunt.
* `delta:sass` - When any `*.scss` file within `src/` changes, the
  `src/sass/main.scss` file is linted and copied into
  `build/assets/ngbp-slim-sass.css`.
* `delta:jssrc` - When any JavaScript file within `src/` that does not end in
  `.spec.js` changes, all JavaScript sources are linted, all unit tests are run,
  and the all source files are re-copied to `build/src`.
* `delta:coffeesrc` - When any `*.coffee` file in `src/` that doesn't match
  `*.spec.coffee` changes, the Coffee scripts are compiled independently into
  `build/src` in a structure mirroring where they were in `src/` so it's easy to
  locate problems. For example, the file
  `src/common/titleService/titleService.coffee` is compiled to
  `build/src/common/titleService/titleService.js`.
* `delta:tpls` - When any `*.tpl.html` file within `src/` changes, all templates
  are put into strings in a JavaScript file (technically two, one for
  `src/common/` and another for `src/app/`) that will add the template to
  AngularJS's
  [`$templateCache`](http://docs.angularjs.org/api/ng.$templateCache) so
  template files are part of the initial JavaScript payload and do not require
  any future XHR.  The template cache files are `build/template-app.js` and
  `build/template-common.js`.
* `delta:jsunit` - When any `*.spec.js` file in `src/` changes, the test files
  are linted and the unit tests are executed.
* `delta:coffeeunit` - When any `*.spec.coffee` file in `src/` changes, the test
  files are linted, compiled their tests executed.

As covered in the previous section, `grunt watch` will execute a full build
up-front and then run any of the aforementioned `delta:*` tasks as needed to
ensure the fastest possible build. So whenever you're working on your project,
start with:

```sh
$ grunt watch
```

And everything will be done automatically!

### Build vs. Compile

To make the build even faster, tasks are placed into two categories: build and
compile. The build tasks (like those we've been discussing) are the minimal
tasks required to run your app during development.

Compile tasks, however, get your app ready for production. The compile tasks
include concatenation, minification, compression, etc. These tasks take a little
bit longer to run and are not at all necessary for development so are not called
automatically during build or watch.

To initiate a full compile, you simply run the default task:

```sh
$ grunt
```

This will perform a build and then a compile. The compiled site - ready for
uploading to the server! - is located in `bin/`, taking a cue from
traditional software development. To test that your full site works as
expected, open the `bin/index.html` file in your browser. Voila!

### Live Reload!

`ngbp-slim-sass` also includes [Live Reload](http://livereload.com/), so you no
longer have to refresh your page after making changes! A JavaScript snippet is
inserted into pages served by the development server, so no browser plugin is
required.  If you use a Live Reload browser plugin, disable the javascript
snippet (see Gruntfile.js connect task for more information)

## Contributions & Roadmap

As this is a very slim down version of [ngBoilerplate](https://github.com/ngbp/ngbp) 
there is little intended to be added in the way of features. I'll try to keep an eye 
on the upstream [ngBoilerplate](https://github.com/ngbp/ngbp), to see if any new 
features get added to the build system. If you spot any bugs, or think of a lightweight 
feature that you think should be included in this project, feel free to open an Issue,
or better yet issue a pull request and I'll take a look.

### To Do

See the [issues list](http://github.com/kennethlawrence/ngbp-slim-sass/issues). And
feel free to submit your own!

