# Large Scale Organization

Putting everything into a single large HTML file isn't very maintainable, nor is it very "componenty" if your "main" page includes several components.  What are some alternatives?

## Individual &lt;script&gt; and css tags

```html
<head>
  <script src="component_A.js"></script>
  <link href="component_A.css" rel=""stylesheet" type="text.css"/>

  <script src="component_B.js"></script>
  <link href="component_B.css" rel=""stylesheet" type="text.css"/>
  ...
  <script src="component_Z.js"></script>
  <link href="component_Z.css" rel=""stylesheet" type="text.css"/>
</head>
```

 - O.K. for developer.
 - What if component_A has a dependency on something else?

## Bundled &lt;script&gt; and css tag

Use Grunt, Gulp etc. to bundle all the .js and .css into two files

```html
<head>
  <script src="bundle.js"></script>
  <link href="bundle.css" rel="stylesheet" type="text.css"/>
</head>
```

## Individual &lt;script&gt; tag, which includes the css

Modify connectedCallback() to include the CSS, _e.g._ (best in ES6!).  Now you only have to include half as many individual files, but makes me barf.


```js
this.innerHTML =
  `<div class="bg-overlay"></div><div class="thumb"></div>

  <style>
  pt-slider {
    display: inline-block;
    ...
  </style>`
```

```html
<head>
  <script src="component_A_plusCSS.js"></script>
  <script src="component_B_plusCSS.js"></script>
  ...
  <script src="component_Z_plusCSS.js"></script>
</head>
```


## Use ES6 _import_ instead of &lt;script&gt;

#### some low level component, e.g. a single Foo

```js
export default class Foo extends HTMLElement {
  someMethod() {}
  anotherMethod(args) {}

  connectedCallback() {
    // include the CSS here
  }
}

if (!customElements.get('pt-foo'))
  customElements.define('pt-foo', Foo);
````

#### higher level component, say a Collection of Foos

```js
import Foo from '../foo.js';

export default class Foos extends HTMLElement {
  someMethod() {}
  anotherMethod(args) {}

  connectedCallback() {
    let html = '<pt-foos class="pt-foos"/>';
    for (let i=0; i<10; i++)
      html += '<pt-foo/>';
    html += '<style> lot of CSS here </style>';
    html += '</pt-foos>';
    this.innerHTML = html;

    // let's remember all those Foo we just created
    this._foos = this.querySelectorAll('pt-foo');
  }
}

if (!customElements.get('pt-foos'))
  customElements.define('pt-foos', Foos);
```

#### your "app" - make it a Web Component too

```js
import Foos from '../foo.js';
import Bars from '../bars.js';

export default class MySuperApp extends HTMLElement {
  ...
}

if (!customElements.get('pt-superapp'))
  customElements.define('pt-superapp', MySuperApp);
```

#### so the HTML is very clean

```html
<head>
  <script type="module" src="./components/app/superapp.js"></script>
  <link href="main.css" rel="stylesheet" type="text.css"/>
</head>
<body>
  <pt-superapp someattr="somevalue"></pt-superapp>
</body>
```
