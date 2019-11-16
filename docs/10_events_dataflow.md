# Events and Data Flow

 - no clear "standard" framework
 - pick one from your favorite framework (and hope it works)
 
### Use CustomEvents

```js
  let event = new CustomEvent("pt-slider", 
    { bubbles: true, 
      detail: { value: Number(value) } 
    });
  this.dispatchEvent(event);
  ...
  someComponent.addEventListener("pt-slider", function(e) {
    e.detail // has what you want
  });
``` 

#### bubbles
 - whether events get passed up the DOM layer,
   - e.g. from &lt;button&gt; to enclosing &lt;div&gt; to &lt;body&gt;
 - Native events default bubble true
 - Custom events default bubble = false
   - either set bubbles to true
   - or attach listener directly to your custom component
    
 
