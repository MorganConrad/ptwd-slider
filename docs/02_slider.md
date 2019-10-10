# Basic Web Component

## class MyFoo extends HTMLElement
 - cannot extend HTMLButtonElement, etc.
 - can inherit from one of your classes extending HTMLElement
   - HTMLElement
     - MyBaseWebComponent
       - MySpecificWebComponent
 - must **extend**
 - not sure if you can use non-class inheritance

## Lifecycle Events
 - constructor()
 - connectedCallback()
 - disconnectedCallback()
 - attributeChangedCallback()
   - observedAttributes() tells _which_ to observe
 - adoptedCallback()  (seldom used)

## Register
```js
if (!customElements.get('element-name')) {
      customElements.define('element-name', MyFoo);
    }
```

 - Element Name **must** contain a hyphen
   - to distinguish from native elements
   - many use a leading namespace, e.g. paper-xxx
   - can't register twice, so icky code...

