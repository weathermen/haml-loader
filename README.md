# Haml Loader for Webpack

Import "static" Haml files as modules in your webpack project. Returns a rendered template.

This is a fork of [Haml-Coffee (Hamlc) Loader for Webpack](https://www.npmjs.com/package/haml-loader).

## Setup

Add to your webpack config module.loaders:

````
{ test: /\.html\.haml$/, loader: "haml-haml" }
````

## Rendering templates

### webpack/assets/javascripts/templates/my_template.html.haml

````javascript
.template
  %h1 {{ title }}
````

### webpack/assets/javascripts/modules/my_module.js

````javascript
require("templates/my_template.html.haml")
````

will return the HTML:

````html
<div class="template">
  <h1>{{ title }}</h1>
</div>
````

## Can I embed JavaScript in my Haml?

In *theory* yes, but at the moment it likely isn't wired up right; this is just a way to convert
"static" Haml into HTML in a webpack loader.

## Why the fork?

The `haml-loader` module uses haml-coffee, which doesn't understand Haml syntax as well as the
`haml` module. For instance, for an Angular template, it seems to interpret `%p {{ content }}` as
`%p{{ content }}` -- that is, it pretty much just blows up, (apparently) seeing the first curly
brace as Haml's older attribute specifier syntax.

## AngularJS

`haml-haml-loader` can be nicely chained with `ngtemplate-loader`

````
{ test: /\.html\.haml$/, loaders: ['ngtemplate?relativeTo=assets/javascripts', 'haml-haml'] },
````
