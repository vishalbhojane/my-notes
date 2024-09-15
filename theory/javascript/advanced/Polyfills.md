Polyfill is a piece of code that provides functionality that is not natively supported by a web browser

They are used to bring new or standardized features to older browsers or environments that do not support those features

Polyfills usually have two basic components:
- Feature detection
- Feature implementation

---
### Feature detection

Feature detection involves working out whether a browser supports a certain block of code, and running different code dependant on whether it does (or doesn’t) so that the browser can always provide a working experience rather crashing/erroring in some browsers

```js
if(“geolocation” in navigator) { 
 // it’s’supported do something with it.
} else {
 // It’s not supported create anything that reproduces the same effect or gives the user feedback
}
```

```js
if(typeof Array.prototype.filter !== "function") {
  Array.prototype.filter = function() {
    // implementation goes here
  };
}
```
### Implementation

```js
Array.prototype.filter = function(fn, thisp) {
  if (this === null) throw new TypeError;
  if (typeof fn !== "function") throw new TypeError;
  let result = [];
  for (let i = 0; i < this.length; i++) {
    if (i in this) {
      let val = this[i];
      if (fn.call(thisp, val, i, this)) {
        result.push(val);
      }
    }
  }
  return result;
};
```

----
### Degrees of completeness for a polyfill

Perfect polyfills
Polyfills that perfectly implement features completely without any side effects

Common polyfills
They might have a few small missing features, some edge cases that don’t work correctly

Partial polyfills
Implement certain features, but have a lot of missing or broken functionality

Fall-back polyfills
They don’t implement the new functionality at all, but just make sure that there is a graceful fall-back behaviour for older browsers

---

See Examples
[[forEach]]
[[notes/problems/polyfills/array/Map|Map]]
[[notes/problems/polyfills/array/Filter|Filter]]
[[notes/problems/polyfills/array/Reduce|Reduce]]
[[Flat]]
[[Call]]
[[Apply]]
[[Bind]]
[[All]]
[[All Settled]]
[[Race]]
[[Any]]
