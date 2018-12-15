# HamlJS Loader for Webpack

Import "static" Haml files as modules in your webpack project. Returns a
template function that can be called with your passed-in local
attributes.

This is a fork of [haml-haml-loader](https://www.npmjs.com/package/haml-haml-loader).

## Setup

Add to your webpack config module.loaders:

```javascript
{ test: /\.html\.haml$/, loader: "hamljs" }
```

## Rendering templates

### webpack/assets/javascripts/templates/my_template.html.haml

```haml
.template
  %h1= title
```

### webpack/assets/javascripts/modules/my_module.js

```javascript
import Template from "../templates/my_template.html.haml"

const title = "My Title"
const template = Template({ title })

document.append(template)
```

will return the HTML:

```html
<div class="template">
  <h1>My Title</h1>
</div>
```
