# What is a Web Component?

<blockquote>
Web components are a set of web platform APIs that allow you to create new custom, reusable, encapsulated HTML tags to use in web pages and web apps. Custom components and widgets build on the Web Component standards, will work across modern browsers, and can be used with any JavaScript library or framework that works with HTML.
</blockquote>

Standards and APIs that let you stick new tags into HTML

```html
<some-new-tag-Morgan-invented id="foo" onchange=...>Some text</some-new-tag-Morgan-invented
```

## Usage

```html
<script type="module" src="node_modules/@polymer/paper-button/paper-button.js"></script>
...create in HTML
<paper-button raised class="indigo">raised</paper-button>
... or, can create in JS
let myButton = document.createElement('paper-button');
```

## Advantages>

 - Built on a Web Standard
 - Pick what other libraries you want (React, Svelte, etc...) [Compatability Page Here](https://custom-elements-everywhere.com/)
 - Better semantics (less &lt;DIV&gt;s)
 
## Disadvantages
 - No built in data binding
   - Pick what other libraries you want (React, Vue, etc...)...
 - **requires** JavaScript turned on in browser (no "progressive enhancement")
 - commingling of properties and attributes (see later)

 
## Issues
 - slow to gain traction???
 - How / where will it fit into the web ecosystem?
 - Frameworks more likely to age more gracefully?


## [Code here](https://github.com/MorganConrad/ptwd-slider/blob/master/src/01_unknown.html)

