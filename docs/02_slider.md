# Basic Web Component

## class MyFoo extends HTMLElement
 - cannot extend HTMLButtonElement, etc. (not sure why?)
 - can inherit from one of your classes extending HTMLElement
   - HTMLElement
     - MyBaseWebComponent
       - MySpecificWebComponent
 - must **extend**
 - not sure if you can use non-class inheritance

## Lifecycle Events
 - constructor()
  - you **cannot** setup children or innerHTML here!
 - connectedCallback()
  - good place to setup children, innerHTML
 - disconnectedCallback()
  - stop any timers, free up any big resources, etc.
 - attributeChangedCallback()
   - observedAttributes() tells _which_ to observe
   - may happen after constructor but before connectedCallback
 - adoptedCallback()  (seldom used)

## Register
Registering twice is a bug, so you need this icky code.
```js
if (!customElements.get('element-name')) {
      customElements.define('element-name', MyFoo);
    }
```

 - Element Name **must** contain a hyphen
   - to distinguish from native elements
   - many use a leading namespace, e.g. paper-xxx
   - can't register twice, so icky code...
 - MyFoo should extend HTMLElement

## [Code here](https://github.com/MorganConrad/ptwd-slider/blob/master/src/02_slider.html)
)
