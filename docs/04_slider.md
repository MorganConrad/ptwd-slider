# Dynamic Configuration

## Via Properties
 - define setters
 - good API to call from Javascript
 - can handle complex / "rich" data as values

## Via Attributes
 - use `attributeChangedCallback()`
   - also `static get observedAttributes()`
 - good API to call from HTML
   - possible from JS but more verbose than setters
 - best for simple (string, number) values
 - might be less coding that setters
 - all lowercase names
 
## Both  (sometimes called "reflection"?)
 - easy access from both JS and HTML
 - need to synchronize
   - avoid infinite loops
 - which is the "one source of truth"?
 


