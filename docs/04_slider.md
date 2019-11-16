# Dynamic Configuration

## Via Properties
 - TODO: define setters
 - good API to call from Javascript
 - can handle complex / "rich" data as values

## Via Attributes
 - use attributeChangedCallback()
   - also requires static get observedAttributes()
 - good API to call from HTML
   - possible from JS but more verbose than setters
 - best for simple (string, number) values
 - might be less coding that setters
 - use lowercase names, otherwise you'll shoot yourself in the foot

## Both  (Google calls this "reflection"?)
 - easy access from both JS and HTML
 - need to synchronize
   - avoid infinite loops!
 - decide which is the "one source of truth"?
 - _e.g._ set value(value) uses the attribute

## Issues

### You will likely get an attributeChangedCallback _before_ connectedCallback
  - check for existence of children before updating them
  - I like to create instance properties during connectedCallback(), YMMV
    - saves constant calls to `this.querySelector()` etc...
  e.g. (see 05_slider.html or utilities)
```js
this.innerHTML = '<div class="bg-overlay"></div><div class="thumb"></div>';
this._bgOverlay = this.querySelector('.bg-overlay');
   create more "private" properties...
```

## [Code here](https://github.com/MorganConrad/ptwd-slider/blob/master/src/04_slider.html)

