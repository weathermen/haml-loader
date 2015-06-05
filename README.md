# Haml Loader for Webpack

Import haml files as modules in your webpack project. Returns a rendered template.

This is a fork of [Haml-Coffee Loader for webpack](https://npm.im/haml-loader).

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
  <h1></h1>
</div>
````

````javascript
require("!haml?title=test!templates/my_template.html.haml")
````

will return the HTML:

````html
<div class="template">
  <h1>test</h1>
</div>
````

## AngularJS

`haml-haml-loader` can be nicely chained with `ngtemplate-loader`

````
{ test: /\.html\.haml$/, loaders: ['ngtemplate?relativeTo=assets/javascripts', 'haml-haml'] },
````
