# Advanced Topics

## Shadow DOM
 - browser support forthcoming
 - unsupported or deprecated features
 - accessible during constructor (real DOM isn't)
 - supposedly aids encapsulation vs. accidental and malicious users (but easy to break)

#### Shadow CSS
 - avoid "Style creep"
   - out: the web component's styles affect other components
   - in:  the App's global style, (e.g. Bootstrap), affects the web component

## Reflection is Tedious and Repetitive and Boring and Error Prone

If you have two properties/attributes, x and y

```js
set x(val) { this.setAttribute('x', val) };
get x()    { return this.getAttribute('x'); }
set y(val) { this.setAttribute('y', val) };
get y()    { return this.getAttribute('y'); }
```

 - Various libraries to help with this
   - a base class that extends HTMLElement
   - mixin / prototype
   
## Setting up Listeners is Tedious and Repetitive and Boring

#### Use MutationObserver + a single EventListener + Centralized Handler

```js
  constructor() {
  ...
    const observer = new MutationObserver( e => onMutationChange(e));
    observer.observe(this.shadowRoot, { options go here});
    this.shadowRoot.addEventListener('change', e => this.onInputValueChanged(e));
  }
...
  onMutationChange(arrayOfChanges) {
    records.forEach(rec => centralHandling(rec));
  }
  
  onInputValueChanged(e) {
    centralHandling(e);
  }
  
```
