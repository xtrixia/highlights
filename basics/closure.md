# closure
Closures are the primary mechanism used to enable data privacy, the enclosed variables are only in scope within the containing (outer) function. In other words, a closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.

```js
const counter = (function () {
  let privateCounter = 0;

  function changeBy(val) { // is the inner function, a closure
    privateCounter += val; // use variable declared in the parent function
  }

  return {
    increment: function (addition) {
      changeBy(addition);
    },
    decrement: function (minus) {
      changeBy(-minus);
    },
    value: function () {
      return privateCounter;
    },
  };
})(); // an IIFE (Immediately Invoked Function Expression) that runs as soon as it is defined

console.log(counter.value()); // 0
counter.decrement(1); // -1
counter.increment(5); // 4
```

------
### reference
- https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36
- https://github.com/getify/You-Dont-Know-JS/blob/1st-ed/scope%20&%20closures/README.md#you-dont-know-js-scope--closures
- https://www.youtube.com/watch?v=KJP1E-Y-xyo&feature=youtu.be&ab_channel=JSConf

[⬅️ table of contents](https://github.com/xtrixia/highlights)
