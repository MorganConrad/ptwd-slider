# Interactivity

## Internal Event Listeners for UI Interactivity
 - this.addEventListener('mouseXXX', (e) => this.onMouseXXX(e));
 - the book attached them to document, I attach to the web component
   - requires a mouseleave handler...
 - example code is basic and not ultra robust

## Event Dispatch to send information out

### Create and fire the event from the Web Component
```js
  let event = new CustomEvent(
    "your-event-name",
    { bubbles: true, // optional
      detail: {      // your data here under "detail"
        value: value
      }
    });
  this.dispatchEvent(event);
```
### Other elements need to listen, e.g.
```js
let theWebComponent = document.getElementById("web_component_ID");
let listeningElement = document.getElementById("listening_ID");
theWebComponent.addEventListener("your-event-name", (e) => {
  listeningElement.value = e.detail.value;
} )
```

## [Code here](https://github.com/MorganConrad/ptwd-slider/blob/master/src/05_slider.html)
## [Demo here](https://raw.githack.com/MorganConrad/ptwd-slider/master/src/05_slider.html)

