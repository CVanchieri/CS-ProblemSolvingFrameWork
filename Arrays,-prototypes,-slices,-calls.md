What's going on with JS prototypes and with the [arguments](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments) objects? Especially when we have to slice it like this:

```javascript
var args = Array.prototype.slice.call(arguments);
```

## Question 1

Why in MDN are things described as `Array.prototype.slice()` and then used as `var sliced = a.slice(1, 3);`? What's the deal with `Array.prototype`?


## Question 2

I get that `Array.prototype.slice.call(obj);` is used to convert an array-like object into an array, but i'm not getting the function of `Array`, `prototype`, `call`. I know that `call` changes what `this` refers to.... but not getting it.