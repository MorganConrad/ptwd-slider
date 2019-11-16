# Utilities

### Cache Elements within your Component: Only call querySelector once

In [The Slider](05_slider.html) these were saved in connectedCallback()

```js
  this._bgOverlay = this.querySelector('.bg-overlay');
  this._thumb = this.querySelector('.thumb');
```

How about a utility?

```js
function mapDOM(map, scope) {
  scope = scope || this;  // will usually need to pass it in
  let result = {};
  for (let [key,value] of Object.entries(map))
    result[key] = scope.querySelector(value);

  return result;
}

...

connectedCallback() {
  ...
  this._dom = mapDom({
    bgOverlay: '.bg-overlay',
    thumb: '.thumb'
  }, this);
  ...
}

```

### Template the HTML

#### New JS template literals
  - Can't use Strings, must be template literals "all the way down"
  - Book splits this code into a separate file with static methods, why???

```js
render(props) {
  return `${this.html(props)}
          ${this.css(props)}`;
}

html(props) { return `<h3> Some text ${props.someValue} </h3>`; }
css(props)  { return ``; }
```

#### Use the &lt;TEMPLATE&gt; or &lt;SLOT&gt; tag
  - Load data from a network request?
  - &lt;SLOT&gt; is a Web Component special, depends on Shadow DOM

#### Use "real" templating
 - [lit-html](https://lit-html.polymer-project.org/)
 - Mustache, Pug, etc...


